---
layout: post
title: Getting at Date & Time with Windows Batch (bat) Files
---

I had the requirement today to append the current date and time onto the end of file name using a windows batch (bat) file. Thought I’d share how I achieved it…

{% highlight dosbatch %}

for /f "tokens=1 delims=/ " %%a in ('date /T') do set DD=%%a
for /f "tokens=2 delims=/ " %%b in ('date /T') do set MM=%%b
for /f "tokens=3 delims=/ " %%c in ('date /T') do set YYYY=%%c
for /f "tokens=1 delims=: " %%h in ('time /T') do set HH=%%h
for /f "tokens=2 delims=: " %%m in ('time /T') do set MINS=%%m
set DATE_NOW=%DD%-%MM%-%YYYY%_%HH%.%MINS%

cd C:\yourfolder
rename "your.file" "your_%DATE_NOW%.file"

{% endhighlight %}

This was working in Windows XP, should hopefully work with other Windows flavours but not 100% sure.
