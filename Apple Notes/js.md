when we use .sort() js convert it all to strings, so we are sorting strings essentially

type chain model
undefined
null
Boolean
Number → BigInt
String → Symbol
Object
Function

if one is boolean, coerce to number.
if one is string and other is number, coerce string to number
if one is object and other is primitive, coerce object to primitive

== coerces to the same type
=== doesnt do coercion

JavaScript performs **numeric coercion** on non-numeric operands.

string.raw preserves all backslashes and escape sequences


there is precision loss in floating point arithmetic