# Default Operators

<br>

## Arithmetic Operator

Including ``+``,  ``-``,  ``*``,  ``/``,  ``%``,  ``^``.

```tapas
2.3 + 4 / 3.0 * 2^2
```
<pre class='Tapas-Return'>
7.633333
</pre>

<br>

## Logical Operators (1st level)

Including ``>``, ``<``, ``>=``,  ``<=``,  ``==``,  ``!=``.

```tapas
5 >= 5.0
```
<pre class='Tapas-Return'>
true
</pre>

<br>

## Logical Operators (2nd level)

Including ``and``, ``or``, ``in``.

```tapas
5 > 4 and (4 in [0,1,2,3,4]) or 3 > 6.0
```
<pre class='Tapas-Return'>
true
</pre>
<br>

## Operator `to`

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

## Logical Operators (3nd level)

Operator `in`.

```tapas
4 in 0 to 10
```
<pre class='Tapas-Return'>
true
</pre>
<br>

## Operator colon ``:``

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
