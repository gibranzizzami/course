---
date:  ""
draft: false
title: "Example - Format Article"
short: ""
thumb:
    image: "cover.jpg"
    anima: ""
    video: ""
layout: ""
weight: 14
lister: 3
format:
    media: "article"
    model: ""
    datum:
        data: ""
require:
    - prop: "linux"
      name: "linux"
      icon: ""
      desc: "Suspendisse condimentum ipsum vel mi luctus, nec ornare est porttitor."
metadata:
    index: false
    thumb: "cover.jpg"
    group: []
    author: ["Al Muhdil Karim"]
description: "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Etiam aliquam libero et magna suscipit vestibulum. Suspendisse condimentum ipsum vel mi luctus, nec ornare est porttitor."
---

## Heading

# H1
## H2
### H3
#### H4
##### H5
###### H6


## Formater

Emphasis, aka italics, with *asterisks* or _underscores_.

Strong emphasis, aka bold, with **asterisks** or __underscores__.

Combined emphasis with **asterisks and _underscores_**.

Strikethrough uses two tildes. ~~Scratch this.~~


## Listing

### ordered 

1. First ordered list item
2. Another item
1. Actual numbers don't matter, just that it's a number
4. And another item.


### unordered

* Unordered list can use asterisks
* Or minuses
* Or pluses


## link

[I'm an inline-style link](https://www.google.com)

[I'm an inline-style link with title](https://www.google.com "Google's Homepage")

[I'm a reference-style link][Arbitrary case-insensitive reference text]

[I'm a relative reference to a repository file](../blob/master/LICENSE)

[You can use numbers for reference-style link definitions][1]

Or leave it empty and use the [link text itself].

URLs and URLs in angle brackets will automatically get turned into links. 
http://www.example.com or <http://www.example.com> and sometimes 
example.com (but not on Github, for example).

Some text to show that the reference links can follow later.

[arbitrary case-insensitive reference text]: https://www.mozilla.org
[1]: http://slashdot.org
[link text itself]: http://www.reddit.com


## Image

Here's our logo (hover to see the title text):

Inline-style: 
![alt text](cover.jpg "Logo Title Text 1")

Reference-style: 
![alt text][logo]

[logo]: cover.jpg "Logo Title Text 2"


## Block Code

Inline `code` has `back-ticks around` it.



```javascript
var s = "JavaScript syntax highlighting";
alert(s);
```
 
```python
s = "Python syntax highlighting"
print s
```
 
```
No language indicated, so no syntax highlighting. 
But let's throw in a <b>tag</b>.
```



## Footnote

Here is a simple footnote[^1].

A footnote can also have multiple lines[^2].  

You can also use words, to fit your writing style more closely[^note].

[^1]: My reference.
[^2]: Every new line should be prefixed with 2 spaces.  
  This allows you to have a footnote with multiple lines.
[^note]:
    Named footnotes will still render with numbers instead of the text but allow easier identification and linking.  
    This footnote also has been made with a different syntax using 4 spaces for new lines.



## Table

| Tables        | Are           | Cool  |
| ------------- |:-------------:| -----:|
| col 3 is      | right-aligned | $1700 |
| col 2 is      | centered      |   $12 |
| zebra stripes | are neat      |    $1 |

There must be at least 3 dashes separating each header cell.
The outer pipes (|) are optional, and you don't need to make the 
raw Markdown line up prettily. You can also use inline Markdown.

Markdown | Less | Pretty
--- | --- | ---
*Still* | `renders` | **nicely**
1 | 2 | 3



## Blockquotes

> Blockquotes are very handy in email to emulate reply text.
> This line is part of the same quote.

Quote break.

> This is a very long line that will still be quoted properly when it wraps. Oh boy let's keep writing to make sure this is long enough to actually wrap for everyone. Oh, you can **Dalai Lama** 



## Lining

Three or more...

---