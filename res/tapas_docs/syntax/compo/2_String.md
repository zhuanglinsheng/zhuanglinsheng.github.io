# 1.6.2. String

String is inherited from C++ STL string class ``std::string``. It can be obtained by single quote '...' or double quote "...". String could be multi-lines until where the quote is closed.

```tapas
// declare a variable 'mystr'
let mystr = 'Uhis is a string'

// declare a variable 'multistr'
let multistr = 'This is a ...
    string of multiple lines'

mystr
multistr
```
<pre class='Tapas-Return'>
Uhis is a string
This is a ...
    string of multiple lines
</pre>

<br>

String is indexable. It can be indexed with integer or slice.

```tapas
mystr[0] = 'T'
mystr[0:4]
```
<pre class='Tapas-Return'>
This
</pre>
```tapas
mystr[0:2] = 'th'
mystr
```
<pre class='Tapas-Return'>
this is a string
</pre>

<br>

Currently, wide string and Unicode are NOT supported. Indexing could be wrong if your string contains non-ASCII characters.

<br>

Set operation on string: using function `append`.

```tapas
std::print('>>>Append "mystr" with string "!!!"...')
mystr.std::append('!!!')
std::print('>>>Append "mystr" with boolean true...')
mystr.std::append(true)
std::print('>>>Append "mystr" with boolean false...')
mystr.std::append(false)
std::print('>>>Append "mystr" with integer 0...')
mystr.std::append(0)
std::print('>>>Append "mystr" with double float 1.0...')
mystr.std::append(1.0)
mystr
```
<pre class='Tapas-Return'>
>>>Append "mystr" with string "!!!"...
>>>Append "mystr" with boolean true...
>>>Append "mystr" with boolean false...
>>>Append "mystr" with integer 0...
>>>Append "mystr" with double float 1.0...
this is a string!!!falsetrue01.000000
</pre>
<br>

Set operation on string: using function `insert`.

```tapas
std::print('>>>Insert to the end of "mystr" a boolean true...')
mystr.std::insert(true, mystr.std::len())
std::print('>>>Insert to the end of "mystr" a boolean false...')
mystr.std::insert(false, mystr.std::len())
std::print('>>>Insert to the end of "mystr" a integer 0...')
mystr.std::insert(0, mystr.std::len())
std::print('>>>Insert to the end of "mystr" a double float 1.0...')
mystr.std::insert(1.0, mystr.std::len())
mystr
```
<pre class='Tapas-Return'>
>>>Insert to the end of "mystr" a boolean true...
>>>Insert to the end of "mystr" a boolean false...
>>>Insert to the end of "mystr" a integer 0...
>>>Insert to the end of "mystr" a double float 1.0...
this is a string!!!falsetrue01.000000falsetrue01.000000
</pre>

<br>

Set operations on string: using function `pop`.

```tapas
std::print('>>>Pop the last character of "mystr"...')
mystr.std::pop()
mystr
```
<pre class='Tapas-Return'>
>>>Pop the last character of "mystr"...
this is a string!!!falsetrue01.000000falsetrue01.00000
</pre>

<br>

Set operations on string: using function `delete`.

```tapas
std::print('>>>Delete the end character of "mystr"...')
mystr.std::delete(mystr.std::len()-1)
mystr

std::print('>>>Delete since the 17th character of "mystr"...')
mystr.std::delete(17 : mystr.std::len()-1)
mystr
```
<pre class='Tapas-Return'>
>>>Delete the end character of "mystr"...
this is a string!!!falsetrue01.000000falsetrue01.0000
>>>Delete since the 17th character of "mystr"...
this is a string!
</pre>
<br>

Copy string

```tapas
mystr.std::copy()
mystr[0].std::copy()
```
<pre class='Tapas-Return'>
this is a string!
t
</pre>
<br>

String equality

```tapas
std::print("'aaa' == 'bbb'    ", 'aaa' == 'bbb')
std::print("'aaa' == 'aaa'    ", 'aaa' == 'aaa')
```
<pre class='Tapas-Return'>
'aaa' == 'bbb'    false
'aaa' == 'aaa'    true
</pre>
