##  Item 3: Beware of Implicit Coercions

- notes:
	- `+` can be number addition or string concatenation (which one will be used is determined by a sequence of steps, you can find it in the ECMA language specification [12.8.3](http://www.ecma-international.org/ecma-262/8.0/index.html#sec-addition-operator-plus))
    - most of times, other arithmetic operators, such as `-`, `*`, `/`, `|`, `&`, `^`, `>>`, `<<` etc, will try to convert the operands to number before processing
	- `NaN` is a special number type defined in `IEEE floating-point standard`
    - `isNaN` is not reliable at all since it does the implicit coercions automatically, should use `Number.isNaN` if use ES6 or above or use your own polyfill `x !== x`
	- `valueOf` will always be chosen over `toString` if provided when do the implicit coercions
    - be careful when deal with `undefined` and truthiness test
- MVI:
	- JS is a loosely typed language
    