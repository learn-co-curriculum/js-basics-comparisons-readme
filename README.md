# JavaScript Comparisons

## Problem Statement 
Now we know about performing basic mathematical functions, and assigning values
to variables, but how would we check to see if a value is what we're expecting?
In addition to performing arithmetic and assigning value to variables,
JavaScript has additional operators for comparing values. The value returned by
a comparison is **always** `true` or `false`.

## Objectives 
1. Identify equality operators
2. Compare numbers with the relational operators

## Identify equality operators 
There are four equality operators built into Javascript:
- **loose equality operator** (`==`)
- **strict equality operator** (`===`)
- **loose inequality operator** (`!=`)
- **strict inequality operator** (`!==`)

When writing Javascript, you only ever use the **strict** operators, as the
loose operators will return true even if the data types aren't the same. A
string '42' is not the same as an integer 42. As developers we want to ensure
that not only are the values the same, but also the data types. 

### `==` Loose Equality Operator
The **loose equality operator** returns `true` if two values are equal:
```js
42 == 42
// => true
```

However, it will _also_ return `true` if it can perform a type conversion (e.g.,
changing the string `'42'` into the number `42`) that makes the two values
equal:
```js
42 == '42'
// => true

true == 1
// => true

'0' == false
// => true

null == undefined
// => true

' ' == 0
// => true
```

This is confusing and inaccurate! It makes no sense that the string `'0'` is
equal to the boolean `false` or that `null` and `undefined` — two **completely
different** data types — are equivalent. ***Never use `==` for comparisons***.

### `===` Strict Equality Operator
The **strict equality operator** returns `true` if two values are equal _without
performing type conversions_. Even if the values on both sides of the operator
look similar (e.g., `'42' === 42`), the `===` operator will only return `true`
if the data types also match:
```js
42 === 42
// => true

42 === '42'
// => false

true === 1
// => false

'0' === false
// => false

null === undefined
// => false

' ' === 0
// => false
```

This is logical and accurate! ***Always use `===` for comparisons***.

### `!=` Loose Inequality Operator
The **loose inequality operator** is the opposite of `==`. It returns `true` if
two values are _not_ equal, performing type conversions as necessary:
```js
9000 != 9001
// => true

9001 != '9001'
// => false

[] != ''
// => false
```

***Never use `!=` for comparisons***.

### `!==` Strict Inequality Operator
The **strict inequality operator** returns `true` if two values are _not_ equal
and does not perform type conversions:
```js
9000 !== 9001
// => true

9001 !== '9001'
// => true

[] !== ''
// => true
```

***Always use `!==` for comparisons***.

## Compare numbers with the relational operators 
There are four relational operators built in to Javascript:
- **greater than** (`>`), 
- **greater than or equals** (`>=`)
- **less than** (`<`)
- **less than or equals** (`<=`)

These operators work in a very similar way to the equality operators:

```js
88 > 9
// => true
```

However, beware of type conversion when comparing non-numbers against numbers.
For instance, when a string is compared with a number, the JavaScript engine
tries to convert the string to a number:
```js
88 > '9'
// => true
```

If the engine can't convert the string into a number, the comparison will always
return `false`:
```js
88 >= 'hello'
// => false

88 <= 'hello'
// => false
```

Strings are compared with other strings lexicographically, meaning
character-by-character from left-to-right. The following returns `false` because
the Unicode value of `8`, the first character in `88`, is less than the Unicode
value of `9`.
```js
'88' > '9'
// => false
```
If you aren't sure what data type you are going to be receiving, but you still
need to compare them, make sure that you tell Javascript to [convert the string
to a number first][convert], and then compare. 

***Top Tip***: Stick to comparing _numerical_ values with the relational
 operators and you'll be golden.

## Conclusion 
Javascript contains both equality and comparison operators that assist us in
writing functional code. Make sure you're always using the strict equality
operators, and only comparing numerical values with the relational operators,
and you'll avoid those annoying troubleshooting errors that can drive you crazy! 

## Resources
- MDN
  + [Comparison operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Comparison_Operators)
  + [Equality comparisons and sameness](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Equality_comparisons_and_sameness)
- [JavaScript Equality Table](http://dorey.github.io/JavaScript-Equality-Table/)
- [freeCodeCamp Forum — JavaScript Comparison Operators](https://forum.freecodecamp.org/t/javascript-comparison-operators/14660)

[convert]:(https://gomakethings.com/converting-strings-to-numbers-with-vanilla-javascript/)