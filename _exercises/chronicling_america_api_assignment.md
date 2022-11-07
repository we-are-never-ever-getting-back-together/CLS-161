---
layout: page
title: Chronicling America API Assignment
description: API Assignment
---

# Chronicling America API Assignment

In this assignment, you are tasked with:

- searching Chronicling America's API for a key word of your choice
- parsing your results from a dictionary to a `DataFrame` with headings "title", "city", 'date", and "raw_text"
- processing the raw text by removing "\n" characters, stopwords, and then lemmatizing the raw text before adding it to a new column called "lemmas."
- saving your `DataFrame` to a csv file

If you need any help with this assignment please email micah.saxton@tufts.edu

```python
# imports
import requests
import json
import math
import pandas as pd
import spacy
```

```python
# initial search: key word = Babe Ruth
url = 'https://chroniclingamerica.loc.gov/search/pages/results/?state=&date1=1777&date2=1963&proxtext=Babe+Ruth&x=18&y=13&dateFilterType=yearRange&rows=20&searchType=basic&format=json'
response = requests.get(url)
raw_data = response.text
res = json.loads(raw_data)
```

```python
# find total amount of pages
print("Total page number is {}".format(res['totalItems'] // res['itemsPerPage'] + (res['totalItems'] % res['itemsPerPage'] != 0)))
```

    Total page number is 2957

Now that I know how many pages there will be, I can use a for loop to iterate through each result page and then each item on each result page. I then gather the data I want from each item: newspaper title, city, date, and text.

Notice in the code below I placed the url string in parentheses () so that I could break it up over multiple lines making it easier to read.

Also, for the sake of this demonstration, I am only iterating over 10 pages. For the full results the for loop should begin: `for i in range(1, total_pages+1)` (the `+1` is necessary becase the seond number in the range function is exclusive).

```python
# query the api and save to dict
data = []
start_date = '1945' # insert value
end_date = '1963' # insert value
search_term = 'Industrialization'
for i in range(1, 11):  # for sake of time I'm doing only 10, you will want to put total_pages+1
    url = (f'https://chroniclingamerica.loc.gov/search/pages/results/?state=&date1={start_date}'
           f'&date2={end_date}&proxtext={search_term}&x=16&y=8&dateFilterType=yearRange&rows=20'
           f'&searchType=basic&format=json&page={i}')  # f-string
    response = requests.get(url)
    raw = response.text
    print(response.status_code)  # checking for errors
    results = json.loads(raw)
    items_ = results['items']
    for item_ in items_:
        temp_dict = {}
        temp_dict['title'] = item_['title_normal']
        temp_dict['city'] = item_['city']
        temp_dict['date'] = item_['date']
        temp_dict['raw_text'] = item_['ocr_eng']
        data.append(temp_dict)
```

    200
    200
    200
    200
    200
    200
    200
    200
    200
    200

## Convert dictionary to a Pandas dataframe

Now that we have the information we want in a dictionary called `data`, we can put it into a dataframe.

```python
# convert dict to dataframe
df = pd.DataFrame.from_dict(data)
```

```python
# convert date column from string to date-time object
df.head()
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }

</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>title</th>
      <th>city</th>
      <th>date</th>
      <th>raw_text</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>evening star.</td>
      <td>[Washington]</td>
      <td>19580921</td>
      <td>&gt;; sy '\n■ •■ / ;, • .\nWill you leave these f...</td>
    </tr>
    <tr>
      <th>1</th>
      <td>valley settler.</td>
      <td>[Palmer]</td>
      <td>19460801</td>
      <td>Storage\nCACHE YOUR\nFOOD\nTHE\nMODERN WAY\n' ...</td>
    </tr>
    <tr>
      <th>2</th>
      <td>automotive news.</td>
      <td>[Detroit]</td>
      <td>19451022</td>
      <td>Itai/ck section\nWash. Idaho\nAgreement\nOn Re...</td>
    </tr>
    <tr>
      <th>3</th>
      <td>valley settler.</td>
      <td>[Palmer]</td>
      <td>19460228</td>
      <td>PALMER, ALASKA Dorothy Boll Editor St Publishe...</td>
    </tr>
    <tr>
      <th>4</th>
      <td>chicago star.</td>
      <td>[Chicago]</td>
      <td>19480724</td>
      <td>* — 1\nThe Chicago\nVol. 3. No. 30\nPublished\...</td>
    </tr>
  </tbody>
</table>
</div>

### Change date format

Pandas allows us to clean and edit our data easily (relatively). We can first convert the string values in the date column to properly formated dates and then sort the dataframe by date.

```python
# sort by date
df['date'] = pd.to_datetime(df['date'])
```

```python
# write fuction to process text
sorted_df = df.sort_values(by='date')
```

### Process text

We can now porcess our text for analysis. The text provded by Chronicling America comes from optical character recognition (ocr) and the accuracy of ocr can be low. Here I will remove new line characters (`\n`), stop words, and then lemamtize the text.

**Rememeber** the decisions you make in how to process your text should be based on the kind of analysis you want to do.

```python
# apply process_text function to raw_text column
# write fuction to process text
nlp = spacy.load("en_core_web_sm")
nlp.disable_pipes('ner', 'parser')  # these are unnecessary for the task at hand

def process_text(text):
    """Remove new line characters and lemmatize text. Returns string of lemmas"""
    text = text.replace('\n', ' ')
    doc = nlp(text)
    tokens = [token for token in doc]
    no_stops = [token for token in tokens if not token.is_stop]
    no_punct = [token for token in no_stops if token.is_alpha]
    lemmas = [token.lemma_ for token in no_punct]
    lemmas_lower = [lemma.lower() for lemma in lemmas]
    lemmas_string = ' '.join(lemmas_lower)
    return lemmas_string

```

```python
# apply process_text function
sorted_df['lemmas'] = sorted_df['raw_text'].apply(process_text)
```

## Save as a csv file

```python
# save to csv
sorted_df.to_csv(f'../data/{search_term}{start_date}-{end_date}.csv',index=False)
```

```python

```
