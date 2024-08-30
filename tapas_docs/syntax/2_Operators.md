---
layout: post
title: "Tapas Programming Language"
use_math: false
---



# 1.2. Operators



## 1.2.1. Arithmetic Operator

Including ``+``,  ``-``,  ``*``,  ``/``,  ``%``, `@` and  ``^``.

```tapas
2.3 + 4 / 3.0 * 2^2
```
<pre class='Tapas-Return'>
7.633333
</pre>

<br>

## 1.2.2. Logical Operators (1st level)

There are two layers of logical operators

- 1st layer Includes ``>``, ``<``, ``>=``,  ``<=``,  ``==``,  ``!=``.

```tapas
5 >= 5.0
```
<pre class='Tapas-Return'>
true
</pre>
- 2nd layer includes ``and``, ``or``, ``in``.

```
5 > 4 and (4 in [0,1,2,3,4]) or 3 > 6.0
```

<pre class='Tapas-Return'>
true
</pre>

<br>

## 1.2.4. Operator `to`

```tapas
0 to 5
```
<pre class='Tapas-Return'>
0 to 5 (by 1)
</pre>
```tapas
for (let idx: int in 0 to 5) {
    idx
}
```
<pre class='Tapas-Return'>
0
1
2
3
4
</pre>
<br>

## 1.2.5. Logical Operators (3nd level)

Operator `in`.

```tapas
4 in 0 to 10
```
<pre class='Tapas-Return'>
true
</pre>
<br>

## 1.2.6. Operator colon ``:``

```tapas
{
	'name' : 'Tony',
	'age' : 20,
}
```
<pre class='Tapas-Return'>
{
"age" : 20,
"name" : Tony,
}
</pre>

Tapas does not provide syntax of operator overloading.

Please inherit the operator interfaces in the source code and implement the corresponding methods manually if you need new operators.
