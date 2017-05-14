# Interesting Overtime

This blog uses (Jekyll)[http://jekyllrb.com/]. 

If you're setting it up for the first time, run `gem install jekyll bundler`.

# Creating a post

Make a file inside the `_drafts` directory with the pattern `{title}.md`.

Include a block at the top with the following content:
```
---
layout: post
title:  "{title}"
categories: {space separated categories}
---
```

To run the site with the drafts visible, use `jekyll serve --drafts`


## Making it public