---
layout: post
title: "Tapas Programming Language"
use_math: false
---



# 1.1. Primitive Types

Generally, there are two kind of primitive types in Tap, ``value type`` and ``composite type``. 

Consistent with other popular programming languages with virtual machines (such as Java), object of value types refers to specific values while composite types refers to a pointer.

<br>

## 1.1.1. Nil

A value of `nil` means null, empty or nothing. Nil cannot be explicitly created by users.

```tapas
std::print('The return of function "print" is a nil whose type is:').std::type()
```
<pre class='Tapas-Return'>
The return of function "print" is a nil whose type code is:
nil
</pre>

<br>

## 1.1.2. Boolean

A boolean value could be either `true` or `false`. They can be obtained by literal ``true`` and ``false`` 

```tapas
false
true
true and false or true
```
<pre class='Tapas-Return'>
true
false
true
</pre>


or by logical operations

```tapas
std::print('true and false      ', true and false)
std::print('true or  false      ', true or  false)

std::print('true  == true       ', true == true)
std::print('true  == false      ', true == false)
std::print('false == true       ', false == true)
std::print('false == false      ', false == false)
```
<pre class='Tapas-Return'>
true and false    false
true or  false       true
true  == true       true
true  == false      false
false == true       false
false == false      true
</pre>
<br>


## 1.1.3. Integer

An integer value in Tapas is in essence a `long int` in C++. They can be obtained by the literal of integer numbers

```tapas
1; 2; 3
```
<pre class='Tapas-Return'>
1
2
3
</pre>

or by integer operations.

```tapas
2 / 3
```
<pre class='Tapas-Return'>
0
</pre>
<br>

Example: Logical operations on integers

```tapas
std::print('1 == 1        ', 1 == 1)
std::print('1 == 2        ', 1 == 2)
std::print('2 == 1        ', 2 == 1)
std::print('2 == 2        ', 2 == 2)
```
<pre class='Tapas-Return'>
1 == 1        true
1 == 2        false
2 == 1        false
2 == 2        true
</pre>
Note that the boolean ``true`` and ``false`` are in essence integers ``1`` and ``0``:

```tapas
std::print('true == 1     ', true == 1)
std::print('false == 0    ', false == 0)
```
<pre class='Tapas-Return'>
true == 1     true
false == 0    true
</pre>
<br>


## 1.1.4. Float

A float value in Tapas is in essence a `double float` in C++. They can be obtained by literal of double float numbers or by numerical operations.

```tapas
std::print('2 / 3.0 = ', 2 / 3.0)
```
<pre class='Tapas-Return'>
2 / 3.0 = 0.666667
</pre>
Example: Logical operations on double floats

```tapas
std::print('2.0 == 2.0     ', 2.0 == 2.0)
std::print('2   == 2.0       ', 2   == 2.0)
std::print('2.0 == 2         ', 2.0 == 2)
```
<pre class='Tapas-Return'>
2.0 == 2.0     true
2   == 2.0       true
2.0 == 2         true
</pre>

Note that the integer ``1`` and double float ``1.0`` are the same, given that their absolute difference is less than the float precision in Tapas:

```tapas
std::print('true == 1.0      ', true == 1.0)
std::print('false == 0.0     ', false == 0.0)
```
<pre class='Tapas-Return'>
true == 1.0      true
false == 0.0     true
</pre>
