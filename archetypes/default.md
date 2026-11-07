---
title: "{{ replace .File.ContentBaseName "-" " " | title }}"
date: {{ .Date }}
draft: true
summary: ""
# sim | code | simcoder  (simcoder = both worlds together)
categories: ["simcoder"]
tags: []
# Cover image: save the photo as cover.jpg in the same folder as this file
# (create articles with `hugo new content posts/my-article/index.md`).
# It is shown at the top of the article and becomes the image of the X/Facebook card.
cover:
  image: "cover.jpg"
  alt: "Describe the photo in a few words"
  caption: "Photo by [Name](https://unsplash.com/@name) on [Unsplash](https://unsplash.com/photos/ID)"
  relative: true
# Giscus comments for this article (needs the setup described in README.md)
comments: true
# Hide the Twitter/X share button for this article:
# disableShare: true
---

Intro: why this matters, in two or three lines.

## The news

Link to the source, then what it says in your own words.

## My take

The part only you can write.

## Links

- [Source title](https://example.com)
