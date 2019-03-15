# 10-rules JavaScript Style Guide
Written by Larisa Bulacheva

**1/10 File name**
File names must be all lowercase and may include underscores (_) or dashes (-), but no additional punctuation. Follow the convention that your project uses. Filenames’ extension must be **.js**. 
Examples:
```product-name.plugin-version.filetype.js```
```jquery.plugin-0.1.js```

**2/10 Empty blocks: may be concise**
An empty block or block-like construct may be closed immediately after it is opened, with no characters, space, or line break in between (i.e. {}), unless it is a part of a multi-block statement (one that directly contains multiple blocks: **if/else or try/catch/finally**).
Example:
```function doNothing() {}```

Illegal:
```if (condition) {```
```  // …```
```} else if (otherCondition) {} else {```
```  // …```
```}```
```try {```
```  // …```
```} catch (e) {}```

**3/10 Where to break**
The prime directive of line-wrapping is: prefer to break at a higher syntactic level.
Preferred:
```currentEstimate =```
``` calc(currentEstimate + x * currentEstimate) /```
```  2.0f;```

Discouraged:
```currentEstimate = calc(currentEstimate + x *```
  ```currentEstimate) / 2.0f;```

In the preceding example, the syntactic levels from highest to lowest are as follows: assignment, division, function call, parameters, number constant. **Operators are wrapped as follows:**
1. When a line is broken at an operator the break comes after the symbol. (Note that this is not the same practice used in Google style for Java.)
This does not apply to the dot (.), which is not actually an operator.
2. A method or constructor name stays attached to the open parenthesis (() that follows it.
3. A comma (,) stays attached to the token that precedes it.

**4/10 Block comment style**
Block comments are indented at the same level as the surrounding code. They may be in /* … */ or //-style. For multi-line /* … */ comments, subsequent lines must start with * aligned with the * on the previous line, to make comments obvious with no extra context. “Parameter name” comments should appear after values whenever the value and method name do not sufficiently convey the meaning.
```/*```
```* This is```
```* okay.```
```*/```

```// And so```
```// is this.```

```/* This is fine, too. */```

```someFunction(obviousParam, true /* shouldRender */, 'hello' /* name */);```

Comments are not enclosed in boxes drawn with asterisks or other characters. Do not use JSDoc (/** … */) for any of the above implementation comments.

**5/10 Use const and let**
Declare all local variables with either **const or let**. Use const by default, unless a variable needs to be reassigned. The **var** keyword must not be used.
Discouraged:
```var apples = 5;```

**6/10 One variable per declaration**
Every local variable declaration declares only one variable: declarations such as:
```let a = 1, b = 2; ```
...are not used.

**7/10 Use trailing commas (arrays)**
Include a trailing comma whenever there is a line break between the final element and the closing bracket.
Example:
```const values = [```
```  'first value',```
```  'second value',```
```];```

**8/10 Do not use the variadic Array constructor**
The constructor is error-prone if arguments are added or removed. Use a literal instead.
Illegal:
```const a1 = new Array(x1, x2, x3);```
```const a2 = new Array(x1, x2);```
```const a3 = new Array(x1);```
```const a4 = new Array();```
This works as expected except for the third case: if x1 is a whole number then a3 is an array of size x1 where all elements are undefined. If x1 is any other number, then an exception will be thrown, and if it is anything else then it will be a single-element array. Instead, write:
```const a1 = [x1, x2, x3];```
```const a2 = [x1, x2];```
```const a3 = [x1];```
```const a4 = [];```
Explicitly allocating an array of a given length using new Array(length) is allowed when appropriate.

**9/10 Do not mix quoted and unquoted keys (objects)**
Object literals may represent either structs (with unquoted keys and/or symbols) or dicts (with quoted and/or computed keys). Do not mix these key types in a single object literal.
Illegal:
```{```
```  a: 42, // struct-style unquoted key```
```  'b': 43, // dict-style quoted key```
```}```

**10/10 No line continuations**
Do not use line continuations (that is, ending a line inside a string literal with a backslash) in either ordinary or template string literals. Even though ES5 allows this, it can lead to tricky errors if any trailing whitespace comes after the slash, and is less obvious to readers.
Illegal:
```const longString = 'This is a very long string that far exceeds the 80 \```
```    column limit. It unfortunately contains long stretches of spaces due \```
```    to how the continued lines are indented.';```
Instead, write:
```const longString = 'This is a very long string that far exceeds the 80 ' +```
```    'column limit. It does not contain long stretches of spaces since ' +```
```    'the concatenated strings are cleaner.';```

15/03