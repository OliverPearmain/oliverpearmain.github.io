---
layout: post
title: Why I Always Use Curly Braces/Brackets

redirect_from:
  - /blog/why-i-always-use-curly-bracesbrackets/
---

Developer 1 really, really hates whitespace, it’s the spawn of the devil you know, he codes the following:


{% highlight js %}
if (condition)
    doSomething();
mustHappenAfterIfStamement();
{% endhighlight %}

Inexperienced (or incompetent) developer 2 comes along to fix a problem or add a feature and fails many times.

{% highlight js %}
if (condition)
    // doSomething(); I've temporarily commented out this line for debugging, oops I've now foobar'ed the flow of code execution, worth it for the whitespace saved though <high fives dev 1, he’s the man>
mustHappenAfterIfStamement();
{% endhighlight %}

{% highlight js %}
if (condition)
    // I've subsequently added this comment, other devs might be confused about whether doSomething() is
    // executed or not, but ah well at least dev 1 saved that whitespace, I hate whitespace too, even though I have a 3x 27" monitors
    doSomething();
mustHappenAfterIfStamement();
{% endhighlight %}

{% highlight js %}
if (condition)
    doSomething();
    doSomthingMore(); // I’m not very good at tabbing, I'm hoping this will be executed only when condition is true, however it'll also be executed if its false. I hate it when it snows, it’s the white you see
mustHappenAfterIfStamement();
{% endhighlight %}

I come along sees dev 1’s code and automatically refactor because I’ve made it my habit to always included curly braces. Quick call the whitespace police… or not, it doesn’t even have to cost you your wonderful whitespace.

{% highlight js %}
if (condition)
{   // OMG white space, my eyes are bleeding, kill me
    doSomething();
}   // this is insane, help me god, no more of the whiteness
mustHappenAfterIfStamement();
{% endhighlight %}

{% highlight js %}
if (condition) { doSomething(); }
mustHappenAfterIfStamement();
{% endhighlight %}

{% highlight js %}
if (condition)
    { doSomething(); }
mustHappenAfterIfStamement();
{% endhighlight %}