## Item 7: Think of Strings As Sequences of 16-Bit Code Units

- Notes:
	- Uniode: every unit of text of all the world's writing system is assigned a unique integer between 0 and 1114111, known as a code point in Unicode terminology
    - History:
    	- 2^16 code points initialy -> UCS-2, 16-bit encoding
        - 2^20 code points -> Basic Multilingual Plane(BMP), consistes of the original 2^16 code points, The additional 16 ranges are known as the supplementary planes.
        - UTF-16 with the addition of what are known as surrogate pairs: pairs of 16-bit code units that together encode a single code point 216 or greater.
        - [more from wikipedia](https://en.wikipedia.org/wiki/Unicode)
	- An element of a JavaScript string is a 16-bit code unit
    - regular expressions operate at the level of code units too (`.` will match only one code unit)
    - While JavaScript’s built-in string datatype operates at the level of code units, this doesn’t prevent APIs from being aware of code points and surrogate pairs. In fact, some of the standard ECMAScript libraries correctly handle surrogate pairs, such as the URI manipulation functions encodeURI, decodeURI, encodeURIComponent, and decodeURIComponent.
	- I believe JS support code points starting from ES5 with `String.fromCodePoint` and `String.prototype.codePointAt()`
- MVI:
	- JavaScript strings consist of 16-bit code units, not Unicode code points.
    - Unicode code points 216 and above are represented in JavaScript by two code units, known as a surrogate pair.
    - Surrogate pairs throw off string element counts, affecting length, charAt, charCodeAt, and regular expression patterns such as “.”.
    
- Resources:
	- [`String.fromCodePoint()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/fromCodePoint)
    