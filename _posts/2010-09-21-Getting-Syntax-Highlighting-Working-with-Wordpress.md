---
layout: post
title: Getting Syntax Highlighting Working with Wordpress

redirect_from:
  - /blog/getting-syntax-highlighting-working-with-wordpress/
---

Really this post is entirely for my own benefit and to merely test the [Syntax Highlighter ComPress](http://wordpress.org/extend/plugins/syntax-highlighter-compress/){: target="_blank" } wordpress plugin that I’ve just installed.

This plugin “is based on the latest Alex Gorbatchev’s SyntaxHighlighter Script” and enables “Code and source text of different mark-up or programming languages to be highlighted.”.

Well here goes, here’s some C# code…

{% highlight csharp %}

/// <summary>
/// A customer.
/// </summary>
public interface ICustomer
{
    /// <summary>
    /// Gets or sets the customers first name.
    /// </summary>
    /// <value>The card request.</value>
    string FirstName { get; set; }
}

{% endhighlight %}

And some SQL code:

{% highlight sql linenos %}

SELECT * FROM vw_tblCustomer AS C WITH (NOLOCK)
INNER JOIN vw_tblTransaction AS T WITH (NOLOCK) ON C.id = T.id
WHERE Customer.FirstName IS 'oliver'

{% endhighlight %}

So it does seem to work, good stuff. Good points to note, I copied the code straight from Visual Studio, the < and > characters, that appear all over the place in comments, were automatically converted into &lt and &gt. Tabs from the copied code were also conviently converted into appropriate spaces.

<del>Bad points, it isn’t immediately obvious how to turn off the line numbering.</del> Actually, all you need to do is add “gutter: false;” to the pre tag class as follows:

{% highlight html %}

<pre class="brush:csharp; gutter: false;">blah</pre>

{% endhighlight %}

Will probably persevere with this, unless I find something better.