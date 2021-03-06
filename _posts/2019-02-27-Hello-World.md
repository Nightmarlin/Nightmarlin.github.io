---
title: print("Hello World");
categories: General
---

# Hello and welcome to my new blog!

It's built on [Contrast](https://niklasbuschmann.github.io/contrast) by Niklas Buschman.

I'm still fiddling so things might break spontaneously, but

This theme has loads of nice features, including:

#### &#9632; Code Highlighting

{% highlight cs %}
using System;
using System.IO;

public bool SaveString(string ToSave) {

    Console.Write("Enter a path ==> ");

    var Path = Console.ReadLine();

    try {

        File.WriteAllText(Path, ToSave);

    } catch (IOException Ex) {

        Console.Writeline($"Unable to save. Error follows{Environment.NewLine}{Ex}");

        return false;

    }

    return true;

}
{% endhighlight %}

#### &#9632; MathJax

$$ \int{\left(\frac{1}{x-1}\right)} = \ln{\left|x-1\right|} + c, x > 1 $$

$$ x_{n+1} = x_{n} - \frac{f\left(x_{n}\right)}{f`\left(x_{n}\right)}$$

#### &#9632; Images

![Image1](/assets/images/aegislash_shield.png)
[Aegislash](https://wallpapercave.com/aegislash-wallpapers) - Found on Wallpaper Cave

#### &#9632; Embeds

<div class="embed">
<iframe width="560" height="315" src="https://www.youtube.com/embed/kYJx5xt2cB0" frameborder="0" allow="accelerometer;
autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

#### &#9632; Super-sized images

<a class="large" href="/assets/images/raindrops.jpeg"><!--[Raindrops](/assets/images/raindrops.jpeg)--></a>
[Raindrops](/assets/images/raindrops.jpeg) - Found somewhere

#### &#9632; General Markdown
This site is built on Jekyll, so it supports markdown syntax such as *italics*, ~~strike\-through~~ and **bold** text,
as well as `Keyboard Shortcuts` and

```xml
<CodeBlock>
    <Highlighting>
        this.
    </Highlighting>
</CodeBlock>
```

But I'll probably just use the code blocks from earlier because they look nicer.

Markdown also supports different headings using `#`s , and block quotes using `>`.

> "Everybody is a genius.
> But if you judge a fish by it's ability to climb a tree,
> it will spend its whole life believing it is stupid"
>
>   &#9472; Albert Einstein

-----

I think it'll be a pleasure working with this theme to create something fun,
even if I'm likely to be the only person using it.