## Item 5: Avoid using `==` with Mixed Types

- Notes:
	- implicit coercions happened when you do `==` instead of `===`
    ```javascript
	"1.0e0" == { valueOf: function() { return true; } };  // true
	```
    - don't recommend `==` unless you are 100% sure what you are doing
- MVI:
	- `==` will apply a confusing set of implicit coercions when its arguments are of different types
    - `===` will be much easier to understand
    - use helper functions with explicit coercions when comparing values of different types
- Resources:
	- [JavaScript Equality Table](http://dorey.github.io/JavaScript-Equality-Table/)