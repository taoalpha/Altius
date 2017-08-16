## Item 6: Learn the Limits of Semicolon Insertion

- Notes:
	- JavaScript requires **semicolons**, JS engine will insert semicolons smartly if you don't have one
    - ^ but ECMAScript standard precisely specifies the semicolon insertion mechanism, so thats why its portable between JS engines
    - Rules of semicolon insertion:
    	1. Semicolons are only ever inserted before a `}` token, after one or more newlines, or at the end of the program input
        ```javascript
		// leave out semicolons at the end of:
		// line, block, program
		function square(x) {
        	var n = +x
	        return n * n
        }
        
		// can not leave out if its not ending block
        function area(r) { r = +r; return Math.PI * r * r }
        function add1(x) { return x + 1 }
		```
        2. Semicolons are only ever inserted when the next input token cannot be parsed
        ```javascript
		// behave as an error correction mechanism
		// won't have semicolons inserted if can be parsed fine as a single statement ( a = b(f()) )
		a = b
		(f());
		
		// semicolon will be inserted for following case
        a = b
		f();

		// another example that semicolon will not be inserted
		a = b
        ["r", "g", "b"].forEach(function(key) {
         background[key] = foreground[key] / 2;
        });

		// one more
		a = b
		/Error/i.test(str) && fail();
		// `/` will be read as division operator: a = b / Error / i.test(str) && fail();

		// be careful about file concatenation (if your concat tool does not insert the semicolons
		// file1.js
        (function() {
	        // ...
        })()

        // file2.js
        (function() {
  			// ...
        })()

		// thats why sometimes you can see code pattern like this: (put `;` ahead)
		;(function() {
  			// ...
        })()

		// IMPORTANT: restricted productions
		// there are some places that no newline is allowed to appear between two tokens
		return {}; // return an object
		return
		{};  // parses as three separate statements, equivalent to:
		return;
		{}
		;
		// SO: the newline following the return keyword forces automatic semicolon insertion, similar for:
		// A `throw` statement
		// A `break` or `continue` statement with an explicit label
		// A postfix `++` or `--` operator
        a
        ++
        b
		// Since ++ can serve as either a prefix or a suffix, but the latter cannot be preceded by a newline, this parses as:
        a; ++b;
		```
        3. Semicolons are never inserted as separators in the head of a `for` loop or as `empty` statements
        ```javascript
		for (var i = 0, total = 1 // parse error
           i < n
           i++) {
           total *= i
        }

		// similar
		function infiniteLoop() { while (true) } // parse error

		// should be
		function infiniteLoop() { while (true); }
		```
- MVI:
	- three rules
    - Never omit a semicolon before a statement beginning with (, \[, +, -, or /.
        
