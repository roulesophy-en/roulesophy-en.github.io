---
filename: 2018-02-01-learning-asciiDoc-table.md
layout: post
title: Learning AsciiDoc Table 
tags: Programming
date: 2018-02-01
comments: false
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

## > Formatting

We can add the following character before `|` of each cell to do some formatting for the corresponding cell.

| character | format |
|---|---|
|`e`|Italic|
|`m`|Monospace|
|`s`|Bold|
|`<`|Left alignment|
|`>`|right alignment|
|`^`|Center alignment|

Example：

```
|===
e|info 01 m|info 02 s|info 03
<|info 04 >|info 05 ^|info 06
<e|info 07 <m|info 08 <s|info 09
>e|info 10 >m|info 11 >s|info 12
^e|info 13 ^m|info 14 ^s|info 15
|===
```

![]({{ site.baseurl }}/images/20180201-6.png)

We can also set the format for each column by setting the `cols` before table. 

```
[cols="e,m,^,>s"]
|===
|info 1 |info 2 |info 3 |info 4 
|info 5 |info 6 |info 7 |info 8 
|===
```

![]({{ site.baseurl }}/images/20180201-7.png)

## > Table inside table

We can also create a table inside table, just by putting `a` before the cell for AsciiDoc syntax, and the cell of inner table is represented by `!` instead of `|`.

```
[cols=",,"]
|===
|info 1
a|info 2
[cols=","]
!===
!inside 1 !inside 2
!inside 3 !inside 4
!===
|info 3
|info 4 |info 5 |info 6
|===
```

![]({{ site.baseurl }}/images/20180201-8.png)

# > Merging cell

We can define number of span by some syntax `|` before each cell. For example:

|Example|Description|
|---|---|
|`2+`|This cell occupies 2 columns|
|`.2+`|This cell occupies 2 row|
|`2.3+`|This cell occupies 2 columns and 3 rows|

For example：

```
[cols=",,,"]
|===
|info 1 |info 2 |info 3 |info 4
.3+|info 5 |info 6 2.2+|info 7          
|info 8
2+|info 9 |info 10
|===
```

![]({{ site.baseurl }}/images/20180201-9.png)

This may not be clear enough, so I do some visualization here.
In `info 5`, since this cell has three columns, 3 cells below are also blank. Similarly, the `info 7` cell has 2 rows and two columns, so the cell next to it and the cell below it are also blank.

```
[cols=",,,"]
|===
   |info 1    |info 2      |info 3    |info 4
.3+|info 5    |info 6  2.2+|info 7          
              |info 8
            2+|info 9                 |info 10
|===
```

Finally it is the most difficult one:

```
[cols=",,,", options="header"]
|===
|info 1 |info 2 |info 3 |info 4
.3+a|info 5 

* list 1
* list 2
<e|info 6 2.2+a|info 7 
[cols=",,"]
!===
2+!sub 1 .2+!sub 2
!sub 3 !sub 4
!===
a|info 8

. number 1
. number 2
2+^s|info 9 <m|info 10
|===
```

![]({{ site.baseurl }}/images/20180201-10.png)


