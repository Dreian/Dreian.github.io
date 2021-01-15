---
layout: post
title:  "Type-level graphs in Haskell"
date:   2021-01-15 14:46:03 +0000
categories: jekyll update
---

Testing this:
{% highlight haskell %}
data State s a = State {runState :: s -> (a, s)}
{% endhighlight %}

