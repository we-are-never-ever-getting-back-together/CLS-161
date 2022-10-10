---
layout: page
title: JSTOR Text Analyzer
description: Here I evaluate JSTOR's Text Analyzer tool.
---

# JSTOR TEXT ANALYZER

## Source:

### [Text Analyzer (JSTOR Labs)](https://www.jstor.org/analyze/)

## Evaluation

### Background

JSTOR is a digital library founded in 1995 in New York City. Originally containing digitized back issues of academic journals, it now encompasses books and other primary sources as well as current issues of journals in the humanities and social sciences. It provides full-text searches of almost 2,000 journals.

Text Analyzer is a tool built by JSTOR Labs, designed for researchers to search for content on the library by uplodading a document

The project started out as a tool to help scholars who are almost finished with their papers, but struggling to find additional content. The goal of the project is now broadened to facilliating users during the research process. Searching using a document can help junior researchers who are looking for the right term in a keyword search, or established researcher to find relevant material outside of their domain.

Using the project is very simple. We can upload any document (text-based, but can be in text such as csv, doc, html, json, or picture format), and the tool will analyze the text to find key topics and terms, cross check it with indexed data on JSTOR, and recommend articles based on similarity.

A few notable features of the tools include support for multiple languages, and non scholastic type of content (non academic paper) such as school syllabus, webpage of a news article.

### Technical analysis

From what I gathered, the way this tool works is similar to the first step of sentiment analysis. Word count was performed, most likely with weights (some common words will have smaller weights then others), and when a set of "key words" is determined, it is used to cross check with set of key words for articles to give us the recommendation. The base technology seems very straightforward, but there seems to be a lot of coefficient recalibration done (and needed) to make the "key words" algorithm more representative of the supplied content.

I have been testing the project with some academic papers, and the first 10 recommendations for each seem really spot on with what I anticipated. However, the result is much less satisfactory when I used less orthodox content like school syllabus, which is expected due to the large amount of noisy data.

### Conclusion

This tool seems to provide a phenomenal solution to a seemingly relatable problem. If a researcher is working on their paper, and they needed more resources, they can use this tool to suggest resources based on the current content of the paper. How is it better than tradiational keyword-based search? With the traditional method, we will just put in a bunch of keywords, and then a lot of available tools will give us papers/content containing the same keyword. However, there are a few downside to this approach:

1. We can't emphasize one keyword more than another. Normally, all the keywords are treated equally
2. Sentiment analysis is done by the researcher, i.e they need to read through the abstract to know whether source agree/disagree with the point they are raising.

This tool can solve both of this problem, and based on the result I tested with just some niche topics such as "Ocean Eight and feminism", the result I got back seem very promissing. It seems no where near perfect, but I do believe that this is a viable product with a lot of room with a clear path to improvement.

```python

```
