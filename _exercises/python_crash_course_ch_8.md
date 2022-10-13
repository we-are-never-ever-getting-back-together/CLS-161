---
layout: page
title: Exercises Ch. 8
description: Select exercises from Python Crash Course
---

# Python Crash Course Chapter 8

## 8-1. Message

Write a function called display_message() that prints one sentence telling everyone what you are learning about in this chapter. Call the function, and make sure the message displays correctly.

```python
def display_message():
    print("I'm learning chapter 8")
display_message()
```

    I'm learning chapter 8

## 8-2. Favorite Book

Write a function called favorite_book() that accepts one parameter, title. The function should print a message, such as _One of my favorite books is Alice in Wonderland_. Call the function, making sure to include a book title as an argument in the function call.

```python
def favorite_book(title):
    print("One of my favorite books is {}".format(title))
favorite_book("Alice in Wonderland")
```

    One of my favorite books is Alice in Wonderland

## 8-3. T-Shirt

Write a function called _make_shirt()_ that accepts a size and the text of a message that should be printed on the shirt. The function should print a sentence summarizing the size of the shirt and the message printed on it.

Call the function once using positional arguments to make a shirt. Call the function a second time using keyword arguments.

```python
def make_shirt(size = 0, text = "default"):
    print("We are making a shirt with size: {} and text: {}".format(size, text))
make_shirt(1, "message")
make_shirt()
```

    We are making a shirt with size: 1 and text: message
    We are making a shirt with size: 0 and text: default

## 8.5. Cities

Write a function called _describe_city()_ that accepts the name of a city and its country. The function should print a simple sentence, such as _Reykjavik is in Iceland_. Give the parameter for the country a default value. Call your function for three different cities, at least one of which is not in the default country.

```python
def describe_city(country, city = "default city"):
    print ("{} is in {}".format(city, country))
describe_city("US", "New York")
describe_city("US", "Boston")
describe_city("US")
```

    New York is in US
    Boston is in US
    default city is in US

## 8.6. City Names

Write a function called _city_country()_ that takes in the name of a city and its country. The function should return a string formatted like this: _"Santiago, Chile"_

```python
def city_country(city, country):
    return "{},{}".format(city, country)
assert(city_country("New York", "US") == "New York,US")
assert(city_country("Boston", "US") == "Boston,US")
assert(city_country("Chicago", "US") == "Chicago,US")
```

## 8.7. Album

Write a function called _make_album()_ that builds a dictionary describing a music album. The function should take in an artist name and an album title, and it should return a dictionary containing these two pieces of information. Use the function to make three dictionaries representing different albums. Print each return value to show that the dictionaries are storing the album information correctly.

Use None to add an optional parameter to _make_album()_ that allows you to store the number of songs on an album. If the calling line includes a value for the number of songs, add that value to the album’s dictionary. Make at least one new function call that includes the number of songs on an album.

```python
def make_album(name, title, song_count = None):
    return {"artist name": name, "album title": title, "song number": song_count} if song_count != None \
                    else {"name": name, "title": title, "song number": song_count}
print(make_album("artist1", "album1"))
print(make_album("artist2", "album2"))
print(make_album("artist3", "album3", 10))
```

    {'name': 'artist1', 'title': 'album1', 'song number': None}
    {'name': 'artist2', 'title': 'album2', 'song number': None}
    {'artist name': 'artist3', 'album title': 'album3', 'song number': 10}

```python

```
