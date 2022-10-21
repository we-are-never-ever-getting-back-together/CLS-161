---
layout: post
title: "Natural Language Processing"
date: "2022-10-24"
categories: jekyll update
---

"The Measured Words: How Computers Analyze Text" goes over how a text file is broken down into smaller component before being put into analysis. Generally a file is constructed by a sequence of space-or-new-line separated strings, which are groups of characters. The paper then goes deeper into some technical analysis of how text file is encoded, which sometimes requires decoding so that we can get to the human readable format of ASCII characters.

The paper went into a lot of technical analysis about tokenization, but I think the general process is just reading characters and building them into word based on some delimeter, such as comma or space or new line. However, there are some preprocessing cases I didn't anticipate, such as women/woman should be counted togethers, or we need to get rid of trailing punctuation after each word.

Voyant Tools is a web-based text reading and analysis environment. Voyant can be used to give us a holistic tenical word analysis of the given input, such as how many times a word appears, what are the neighboring words, and frequency over a chosen range. The tool seems to be doing pretty well the work it claims to do. We can quickly find the occurences of each word and how are the words commonly used (i.e in what context). A feature I noticed is we can include multiple text sources, and the tool will do the text analysis for each source separately. This is a small feature but can really help smoothen the work flow. Another feature is ease in sharing current analysis with other people. Voyant tool allows generation of a static link that can be shared, allowing easy collaboration on dashboard.
