---
title: "Example of a post"
date: 2019-10-21
tags: [post]
categories: [data structure, post]
header:
  image: "/assets/images/example/post-it.jpg"
excerpt: "Example Post"
mathjax: "true"
---

# H1 Heading

## H2 Heading

### H3 Heading

Here's some basic text

And here's some *italics*

Here's some **bold** text.

What about a [link](https://github.com/lucastvms)

Here's  bulleted list:
* First item
+ Second item
- Third item

Here's a numbered list:
1. First
2. Second
3. Third

Python code block:
```python
    import numpy as np

    def test_function(x, y):
      z = np.sum(x, y)
      return z
```

R code block:
```r
library(tidyverse)
df <- read_csv("some_file.csv")
head(df)
```

Here's some inline code `x+y`.

Here's an image:
<img src="{{ site.url }}{{ site.baseurl }}/assets/images/example/post-it.jpg" alt="linearly separable data">

Here's another image using Kramdown:
![alt]({{ site.url }}{{ site.baseurl }}/assets/images/example/post-it.jpg)

Here's some math:

$$z=x+y$$

You can also put it inline $$z=x+y$$
