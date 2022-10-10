---
layout: page
title: Downloading Web Pages with Python
description: This lesson introduces Uniform Resource Locators (URLs) and explains how to use Python to download and save the contents of a web page to your local hard drive.
---

# Downloading Web Pages with Python

### Source

https://programminghistorian.org/en/lessons/working-with-web-pages

## Open a webpage using Python

```python
import urllib.request, urllib.error, urllib.parse

url = 'http://www.oldbaileyonline.org/browse.jsp?id=t17800628-33&div=t17800628-33'

response = urllib.request.urlopen(url)
webContent = response.read().decode('UTF-8')

print(webContent[0:300])

```

    <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
    <html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
    <head>
    	<title>Browse - Central Criminal Court</title>
    	<meta http-equiv="content-type" content=

## Saving a Local Copy of a Web Page

```python
import urllib.request, urllib.error, urllib.parse

url = 'http://www.oldbaileyonline.org/browse.jsp?id=t17800628-33&div=t17800628-33'

response = urllib.request.urlopen(url)
webContent = response.read().decode('UTF-8')

f = open('obo-t17800628-33.html', 'w')
f.write(webContent)
f.close

```

    <function TextIOWrapper.close()>

## Reflection

To be honest, this coding portion of this lesson is pretty straightforward, and it seem like a prerequisite for the linked lesson in the final step about using query to download multiple files. I was actually really interested in the section covering how URL works, because this is my first time reading about it. Sometimes it does cross my mind about how the URL looks longer every time I type something into google search, but this is the first time I read about query parameters and how we can manipulate it to navigate through the data of a website, possibly with the help of a web crawler. One thing that got me curious is we can get the exact file if we knew the ID of the file; however, how can we find the range of possible ID we can traverse through that has a valid or access-granted file, or it is a trial-then-error process?

```python

```
