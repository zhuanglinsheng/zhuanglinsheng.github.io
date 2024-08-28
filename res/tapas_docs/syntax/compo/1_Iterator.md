# 1.6.1. Iterator

Iterator can be created by operator ``to`` or by function ``toiter``.

<br>

- Example 1: Create an iterator "iter1" from 0 to 5 (not included) with operator `to` :

```tapas
let iter1 = 0 to 5
std::print('iter1 (abbr) = ', iter1)

for (let i in iter1) { i }
```
<pre class='Tapas-Return'>
iter1 (abbr) = "Iterator at 0x600003434e10"
0
1
2
3
4
</pre>

<br>

- Example 2: Create an iterator "iter2" from 5 to 0 (not included) with function `toiter` :

```tapas
let iter2 = std::toiter(5, -1, 0)

std::print('iter2 (full) = ', iter2.std::tostr())
for (let i in iter2) { i }
```
<pre class='Tapas-Return'>
iter2 (full) = 5 to 0 (by -1)
5
4
3
2
1
</pre>
<br>

- Example 3: Create an iterator "iter3" from 0 to 5 (not included) with function `toiter`:

```tapas
let iter3 = std::toiter(0, 1, 5)

std::print('iter1 == iter3 = ', iter1 == iter3)
for (let i in iter3) { i }
```
<pre class='Tapas-Return'>
iter1 == iter3 = true
0
1
2
3
4
</pre>
