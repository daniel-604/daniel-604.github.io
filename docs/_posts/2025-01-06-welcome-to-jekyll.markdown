---
layout: post
title:  "Welcome to Jekyll!"
date:   2025-01-06 21:56:58 +0900
categories: jekyll update
---
You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. You can rebuild the site in many different ways, but the most common way is to run `jekyll serve`, which launches a web server and auto-regenerates your site when a file is updated.

Jekyll requires blog post files to be named according to the following format:

`YEAR-MONTH-DAY-title.MARKUP`

Where `YEAR` is a four-digit number, `MONTH` and `DAY` are both two-digit numbers, and `MARKUP` is the file extension representing the format used in the file. After that, include the necessary front matter. Take a look at the source for this post to get an idea about how it works.

Jekyll also offers powerful support for code snippets:

{% highlight py %}
import sys
input = sys.stdin.readline

G = int(input())
P = int(input())
g = []
for i in range(P):
    g.append(int(input()))
parent = {}
for i in range(1, G + 1):
    parent[i] = i
def find_parent(x):
    if parent[x] == x:
        return x
    parent[x] = find_parent(parent[x])
    return parent[x]

def union(a, b):
    parent_a, parent_b = find_parent(a), find_parent(b)
    if parent_a != parent_b:
        parent[parent_a], parent[parent_b] = min(parent_a, parent_b), min(parent_a, parent_b)
switch = True
answer = 0
for i in g:
    parent_i = find_parent(i)
    if parent_i == 1:
        if switch:
            answer += 1
            switch = False
        else:
            break
    else:
        answer += 1
        union(parent_i, parent_i - 1)
print(answer)
{% endhighlight %}

Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
