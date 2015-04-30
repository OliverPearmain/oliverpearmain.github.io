---
layout: post
title: Using MAXDOP with Complex SQL Queries

redirect_from:
  - /blog/using-maxdop-with-complex-sql-queries/
---

We came across a problem at work today where the CPU resource of a quad core MS SQL machine was totally consumed by someone issuing a rather complex and time-consuming SQL query (it wasn’t me honest!).

If you’re unable to optimize or avoid running such a complex query then it is recommended you use the MAXDOP (maximum degree’s of parallelism) query hint which enables you to specify the number of CPU’s used by the query.

Here’s an example, using only a single CPU…

{% highlight sql %}

SELECT * FROM tblWithLoadsOfData WITH (NOLOCK)
WHERE  (someField LIKE '%blah%'
      OR someField LIKE '%foo%'
      OR someField LIKE '%goober%'
      OR someField LIKE '%ollie%'
      OR someField LIKE '%cpu%'
      OR someField LIKE '%maxdop%')
OPTION (MAXDOP 1)

{% endhighlight %}