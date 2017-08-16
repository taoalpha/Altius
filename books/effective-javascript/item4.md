## Item 4: Prefer Primitives to Object Wrappers

- Notes:
	- five types of primitives: booleans, numbers, strings, null, undefined + (ES6: symbols)
	- `typeof null === "object"` is a bug introduced a long long time ago... so its impossible to fix it without affecting a ton of websites
    - primivies are not equal to their object wrappers format if they have one
    - when use `prototype` functions with primitives, its creating a temporary object wrapper for the value
    - ^ so when you assign anything to it, you are assigning to its wrapper object which is temporary, so you can not store anything into a primitive value

- MVI:
	- Object wrappers for primitive types are not equivalent to their primitive values
    - Getting and setting properties on primitives implicitly creates object wrappers