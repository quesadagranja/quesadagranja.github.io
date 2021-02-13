---
title: Scope of variables in R
---
One of the things I liked the least about R when I was learning to program in it was the **scope of variables**. Its behavior is substantially different from that of other more popular languages and can cause code errors very easily if one doesn't know how it works.

Let's see a simple example.

{% highlight r linenos %}
y <- 3
f <- function(x) {
  x + y
}
{% endhighlight %}

Although the `y` variable hasn't been defined within the environment of the `f` function, this program **runs correctly**.

{% highlight r linenos %}
> f(2)
[1] 5
{% endhighlight %}

This is because R uses a [lexical scope](https://en.wikipedia.org/wiki/Scope_%28computer_science%29) to find the value associated with a variable. That is, if R doesn't find the value of the variable within the function, it will look for it outside, in the environment where the function was defined. This behavior is counter-intuitive for regular C, Python or Matlab programmers, and can be a major source of bugs.

![Image of bugs](/path/file.jpg "R bugs crawling into your code.")

When I discovered this feature, I was developing several functions with many input parameters to be called from a different function. By doing this, my first impression was that I was wasting my time. Because, what's the point in defining input parameters in R functions? There's no real need to have functions with input parameters! All you have to do is assign the function's internal variables *before* calling the function, and R will do the rest.

Of course, this is ***not at all elegant*** and generates a hard-to-read code. While this might work for small files being very careful, it would be unmanageable for large projects.

The best way to bypass the problems generated by the scope of variables in R is to ***create a package***, splitting the functions into different files. In addition, when compiling the package, functions that are not properly defined can be detected with commands like [`devtools::check()`](https://www.rdocumentation.org/packages/devtools/versions/2.3.2/topics/check).