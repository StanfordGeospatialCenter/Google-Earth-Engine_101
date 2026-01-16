# JavaScript quick syntax primer

This is a short introduction to the JavaScript syntax used in the Earth Engine
JavaScript Code Editor. It covers comments, variables, arrays/objects, and
functions with short examples. Code examples are fenced with syntax highlighting.

## Comments

Single-line comments start with `//` and block comments use `/* ... */`.

Example:

```javascript
// This is a single-line comment
/*
  This is a
  multi-line comment
*/
```

You will often see code temporarily disabled by wrapping it in block comments; remove
the `/*` and `*/` to re-enable it.

## Variables

Use `var` to declare simple variables in these examples. (Modern JavaScript
also supports `let` and `const`.)

```javascript
var the_answer = 42;           // a number
var my_variable = 'I am a string';
var my_other_variable = "I am also a string"; // double quotes are fine
```

Statements are usually terminated with a semicolon, although JavaScript has
automatic semicolon insertion in many cases.

```javascript
var test = 'I feel incomplete...';
print(test); // prints: I feel incomplete...
```

## Arrays (lists)

Arrays use square brackets `[]` and JavaScript is zero-indexed (first item is
index `0`).

```javascript
var my_list = ['eggplant', 'apple', 'wheat'];
print(my_list[0]); // prints: eggplant
```

## Objects (dictionaries)

Objects use curly braces `{}` with key-value pairs. Keys can be accessed with
either bracket notation `obj['key']` or dot notation `obj.key`.

```javascript
var my_dict = {'food': 'bread', 'color': 'red', 'number': the_answer};
print(my_dict['color']); // prints: red
print(my_dict.color);    // also prints: red
```

## Functions

Functions let you encapsulate reusable logic. Here's a simple example that
returns a greeting string.

```javascript
var my_hello_function = function(name) {
  return 'Hello ' + name + '!';
};

print(my_hello_function('world')); // prints: Hello world!
```

## Practice: Uncommenting code

Some examples are intentionally wrapped in block comments in these tutorials.
To try them, remove the surrounding `/*` and `*/` markers and run the script in
the Code Editor.

Example (uncomment to run):

```javascript
/*
var another_list = ['one', 'two', 'three'];
print('The second item in our new list is: ' + another_list[1]);
*/
```

If you want, I can add short exercises to this page (e.g., small tasks for
learners to try in the code editor). Tell me what you'd like included.
