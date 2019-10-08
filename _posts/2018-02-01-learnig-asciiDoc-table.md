---
filename: 2018-02-01-learnig-asciiDoc-table.md
layout: post
title: Learning AsciiDoc Table 
tags: Programming
date: 2018-02-01
comments: true
---

![]({{ site.baseurl }}/images/20180201-1.jpeg)  
Recently I have to used [AsciiDoc](http://asciidoc.org) for some reason. Therefore, let's talk about what I learnt.

## > Fundamental
This is the simplest example: first row of the table determines how many columns the table has.

```
|===
|header 1 |header 2 |header 3
|info 1 |info 2 |info 3
|info 4 |info 5 |info 6
|===
```

![]({{ site.baseurl }}/images/20180201-2.png)

If you want more than one line in some specific cell, you can add a new line with the `+` sign. As long as the first line sets the number of columns, AsciiDoc can do it for you.

```
|===
|header 1 |header 2 |header 3
|info 1 |info 2 +
next line |info 3
|info 4 |info 5 |info 6
|===
```

![]({{ site.baseurl }}/images/20180201-3.png)

To use AsciiDoc's syntax in the form, you can just add `a` to the `|` of the cell. For example, we can add a list to the storage grid as follow:

```
|===
|header 1 |header 2 |header 3
|info 1 a|info 2 

* item 1
* item 2
|info 3
|info 4 |info 5 |info 6
|===
```

![]({{ site.baseurl }}/images/20180201-4.png)

It is possible to add some attributes to the table. For example, we can set the relative width of each column and add Header as follow:

```
[cols="1,2,3", options="header"]
|===
|header 1 |header 2 |header 3
|info 1 |info 2 |info 3
|info 4 |info 5 |info 6
|===
```

![]({{ site.baseurl }}/images/20180201-5.png)

Personal thinking: Actually it is very hard to maintain and modify later.
