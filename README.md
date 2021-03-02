# One More Calculator Language
----

This repo is a work-in-progress language for performing calculations in a REPL.

An example session could look something like this (not actual data because it
isn't written yet):

```
>> 2 + 2  # Comment
4
>> 2 + 2 -> x  # Store a result in x
>> x  # Get the value of x
4
>> y = 2+2; y  # Other way to store a result, plus two commands on a line (outputs last one)
4
>> 3 * (2 + 2)
12
>> 2 + 2 )*3  # Extra close-parens have implicit open paren at line begin
12
>> pi  # Useful constants have a name you can use
3.141592
>> ln(e)  # Useful math functions also exist
1
>> e * e )ln  # Alternative function call syntax
2
```

Most of this implementation is standard. The left-to-right assignment and
implicit open parentheses are designed for typing out math expressions more
easily, since going back and editing is harder, whereas appending to the end of
an existing line is harder. For example, if you evaluate an expression, see the
result, and want to save it in a variable, you can press the up arrow, then type
`->x` to get a command which saves the previous expression in `x`.

The REPL can also take commands by beginning a line with `:`, which can be used
to control some aspects of the calculation, including internal precision and
output format. The exact syntax for these commands is TBD.
