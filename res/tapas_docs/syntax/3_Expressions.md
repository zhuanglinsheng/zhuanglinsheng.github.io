# 1.3. Expressions

This section will illustrate the priority of different expressions in Tapas.

Here is an example of parsing expressions according to the rule of priority:

```tapas
var arr: list = std::tolist(1,2,3)
var test_pri: real = -1 * 2 * 2 / std::toint(2^2) + arr[0] in 0 to arr[2]
test_pri
```
<pre class='Tapas-Return'>
true
</pre>

These codes would print out ``true``. When the propriety is not clear, always use parenthesis.

<br>

## 1.3.1. Value

The expressions with the highest priority are

- Integer
- Float
- Boolean ``true`` or ``false``
- String ``'...'`` or ``"..."``
- Dictionary  ``{ key_1 : value_1, key_2 : value_2 }``
- Function ``(..) { ... }``
- Environment copy ``this`` and ``base``
- Variable name

These expressions directly create or refer to the values in Tap. They are the basis of other operations, and Tapas script will always try to interpret these parts first.

<br>

## 1.3.2. Calling and indexing

Expressions of the second priority are calling and indexing.

Calling expression looks like ``f(a,b,c,...)`` where ``f`` is a callable value, and ``a``, ``b``, ``c``, ``...`` are parameters. Calling expression can be changed into the equivalent ``tunnel`` form, ``a.f(b, c, ...)``.

```tapas
arr.std::len()
```
<pre class='Tapas-Return'>
3
</pre>
Indexing expression is of the same priority as calling expression, which looks like ``arr[idx]``. Here ``arr`` is a indexable value, and ``idx`` is the index. String indexing expression can be transformed into the equivalent ``read-only string indexing`` form, which looks like ``arr::idx``. Here no need to add quotes in ``idx``. The read-only string indexing form cannot be lvalue in assignment.

```tapas
var d: dict = {
    'k1' : [1],
    'k2' : [2],
    'f1' : () { return 99999 },
}
```
Now we index the elements of the dictionary above:

```tapas
d::k1.std::tostr()
```
<pre class='Tapas-Return'>
[1]
</pre>

```tapas
d::k2.std::tostr()
```
<pre class='Tapas-Return'>
[2]
</pre>

```tapas
d::k2[0] / 2
```
<pre class='Tapas-Return'>
1
</pre>

```tapas
d::f1()
```
<pre class='Tapas-Return'>
99999
</pre>
<br>

## 1.3.3. Arithmetic operations

Expressions of the third priority are arithmetic operations. They can be divided into three orders.

- Third order  ``^`` (power calculation)
- Second order  ``*`` (multiplication), ``/`` (devision) and ``%`` (modulo calculation)
- First order  ``+`` (addition) and ``-`` (subtraction)

Higher order arithmetic operations are executed first inside an arithmetic operation.

<br>

## 1.3.4. Third order logic operations

Expression of the 4th priority is third order logical expression. The logical operators in this level include ``>``, ``<``, ``>=``, ``<=``, ``==``, ``!=``. Note that floats cannot be applied into ``==`` for equality judgment.

<br>

## 1.3.5. Second order logic operations

Expression of the 5th priority is second order logical expression. The logical operators in this level include ``and`` and ``or``, the logical and operation and logical or operation. A ``nil`` would be returned if either side is not logical expression (boolean value or the expression that returns boolean value).

<br>

## 1.3.6. Expression to

Expression of the 6th priority is ``to`` expression, which looks like ``v1 to v2``. Here ``to`` is an operator and ``v1`` and ``v2`` are integers.

<br>

## 1.3.7. Expression pair

Expression of the 7th priority is ``pair`` expression, which looks like ``v1 : v2``. Here `:` is an operator and ``v1`` and ``v2`` are Tapas values.

<br>

## 1.3.8. Expression in

The expression at the lowest position of the priority system is ``in`` expression: ``v1 in v2`` where ``in`` is logically existence operator. ``v1`` is an element and ``v2`` is an iterable value. (sub class of ``tcompo_iter``), including ``titer`` and ``tlist``. Operator ``in`` returns a boolean, standing for whether ``v1`` is in ``v2``.

