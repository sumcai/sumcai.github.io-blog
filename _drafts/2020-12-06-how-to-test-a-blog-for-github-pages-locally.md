---
layout: post
title:  "How to test a blog for GitHub Pages locally"
date:   2020-12-06 20:55:00 +0300
tags: [GitHub Pages]
---

### Overview

In the post, we are going to discuss how to test a blog on GitHub Pages locally.

### Test blog locally

In my opinion, it is better to test a blog locally before publishing when you configure it the first time.

Follow the steps below to test a GitHub Pages blog locally:

- Install ruby

For windows, you could download [here](https://rubyinstaller.org/downloads/).

- Install the jekyll and bundler gems:

```
gem install jekyll bundler
```

- Install dependencies based on Gemfile file:

```
bundle install
```

- Run server locally:

```
bundle exec jekyll serve
```

- Browse to http://localhost:4000

### Conclusion

We have described how to test a blog for GitHub Pages locally.
