## Item 2: Understand JavaScript's Floating-Point Numbers

- Notes:
	- one `number` type
    - all store as `double-precision floating-point` (64-bit encoding -> doubles)
    - range from -2^53 to 2^53
    - the bitwise arithmetic operators only work on `integers`, will convert the operands to 32-bit before do any processing
    - `0.1 + 0.2 !== 0.3` because doubles can only represent a finite set of numbers, and `0.1` is infinite when convert to binary
    - above cause the `associative` won't always true
    - above can be solved if convert all to larger integerts like `1 + 2 === 3`
- MVI:
	- bitwise operators only work for 32-bit (integers)
    - limitations of precisions in floating-point arithmetic
