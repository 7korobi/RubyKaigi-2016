
```
A Tale of Two String Representations
Kevin Menard @nirvdrum

http://togetter.com/li/1021993?utm_source=dlvr.it&utm_medium=twitter
https://github.com/jruby/jruby/wiki/Truffle
https://github.com/jruby/jruby/tree/master/truffle
http://www.spinute.org/ruby/gsoc2016/japanese.html
https://github.com/spinute/CRope/blob/master/src/rope.c#L56-L59
```


'Hello'
- 7bit
- utf-8
- 5bytes


RStrings
- Mutable
- requires contiguous memory
- copy-on-write


Ropes (JRuby + Truffle)
- Immutable
- Tree representation
- Logical string fragment oriented
- shares memory by building new trees with existing nodes


Concatenation
  x = 'Hello'
  y = 'World'
  z = x + y

- RString 
- O(n) operation

- Rope
- O(1) operation


String#+   40倍(MRI)〜130倍(JRuby)早い
String#<< 


Substring
  x = "Hello"
  y = x[1..3]


Multiplication
  x = 'abc'
  y = x * 3

- Rope
- O(1) : RepeatingRope(times: 3)


String Length
  'Hello'.bytesize
- 17倍遅い

  'こにちわ'.size
- 100倍遅い


Rope Benefits
- Allow for interining of string
- Metaprogramming
- Final values are great for Graal
- Implicitly thread-safe


Ruby String have two purposes
- sequence of characters (looked at thus far)
- Byte buffer            (Ropes are not very good at)

Node costs dominate smaller string fragments



