# JavaScript Style Guide

## Table of Contents

1. [Types](#types)
1. [References](#references)
1. [Objects](#objects)
1. [Arrays](#arrays)
1. [Destructuring](#destructuring)
1. [Strings](#strings)
1. [Functions](#functions)
1. [Arrow Functions](#arrow-functions)
1. [Classes & Constructors](#classes--constructors)
1. [Modules](#modules)
1. [Iterators and Generators](#iterators-and-generators)
1. [Properties](#properties)
1. [Variables](#variables)
1. [Hoisting](#hoisting)
1. [Comparison Operators & Equality](#comparison-operators--equality)
1. [Blocks](#blocks)
1. [Control Statements](#control-statements)
1. [Comments](#comments)
1. [Whitespace](#whitespace)
1. [Commas](#commas)
1. [Semicolons](#semicolons)
1. [Type Casting & Coercion](#type-casting--coercion)
1. [Naming Conventions](#naming-conventions)
1. [Accessors](#accessors)
1. [loops](#loops-and-conditional-statements)
1. [Formatting](#formating)


# React/JSX Style Guide


## Table of Contents

1. [Basic Rules](#basic-rules)
1. [Class vs `React.createClass` vs stateless](#class-vs-reactcreateclass-vs-stateless)
1. [Mixins](#mixins)
1. [Naming](#naming)
1. [Declaration](#declaration)
1. [Alignment](#alignment)
1. [Quotes](#quotes)
1. [Spacing](#spacing)
1. [Props](#props)
1. [Refs](#refs)
1. [Parentheses](#parentheses)
1. [Tags](#tags)
1. [Methods](#methods)
1. [Ordering](#ordering)
1. [`isMounted`](#ismounted)

## Types

<a name="types--primitives"></a><a name="1.1"></a>

- [1.1](#types--primitives) **Primitives**: When you access a primitive type you work directly on its value.

  - `string`
  - `number`
  - `boolean`
  - `null`
  - `undefined`
  - `symbol`
  - `bigint`

  <br />

  ```javascript
  const foo = 1;
  let bar = foo;

  bar = 9;

  console.log(foo, bar); // => 1, 9
  ```

  - Symbols and BigInts cannot be faithfully polyfilled, so they should not be used when targeting browsers/environments that don’t support them natively.

<a name="types--complex"></a><a name="1.2"></a>

- [1.2](#types--complex) **Complex**: When you access a complex type you work on a reference to its value.

  - `object`
  - `array`
  - `function`

  <br />

  ```javascript
  const foo = [1, 2];
  const bar = foo;

  bar[0] = 9;

  console.log(foo[0], bar[0]); // => 9, 9
  ```

**[⬆ back to top](#table-of-contents)**

## References

<a name="references--prefer-const"></a><a name="2.1"></a>

- [2.1](#references--prefer-const) Use `const` for all of your references; avoid using `var`. eslint: [`prefer-const`](https://eslint.org/docs/rules/prefer-const), [`no-const-assign`](https://eslint.org/docs/rules/no-const-assign)

  > Why? This ensures that you can’t reassign your references, which can lead to bugs and difficult to comprehend code.

  ```javascript
  // bad
  var a = 1;
  var b = 2;

  // good
  const a = 1;
  const b = 2;
  ```

<a name="references--disallow-var"></a><a name="2.2"></a>

- [2.2](#references--disallow-var) If you must reassign references, use `let` instead of `var`. eslint: [`no-var`](https://eslint.org/docs/rules/no-var)

  > Why? `let` is block-scoped rather than function-scoped like `var`.

  ```javascript
  // bad
  var count = 1;
  if (true) {
    count += 1;
  }

  // good, use the let.
  let count = 1;
  if (true) {
    count += 1;
  }
  ```

<a name="references--block-scope"></a><a name="2.3"></a>

- [2.3](#references--block-scope) Note that both `let` and `const` are block-scoped, whereas `var` is function-scoped.

  ```javascript
  // const and let only exist in the blocks they are defined in.
  {
    let a = 1;
    const b = 1;
    var c = 1;
  }
  console.log(a); // ReferenceError
  console.log(b); // ReferenceError
  console.log(c); // Prints 1
  ```

  In the above code, you can see that referencing `a` and `b` will produce a ReferenceError, while `c` contains the number. This is because `a` and `b` are block scoped, while `c` is scoped to the containing function.

**[⬆ back to top](#table-of-contents)**

## Objects

<a name="objects--no-new"></a><a name="3.1"></a>

- [3.1](#objects--no-new) Use the literal syntax for object creation. eslint: [`no-new-object`](https://eslint.org/docs/rules/no-new-object)

  ```javascript
  // bad
  const item = new Object();

  // good
  const item = {};
  ```

<a name="es6-computed-properties"></a><a name="3.4"></a>

- [3.2](#es6-computed-properties) Use computed property names when creating objects with dynamic property names.

  > Why? They allow you to define all the properties of an object in one place.

  ```javascript
  function getKey(k) {
    return `a key named ${k}`;
  }

  // bad
  const obj = {
    id: 5,
    name: "San Francisco",
  };
  obj[getKey("enabled")] = true;

  // good
  const obj = {
    id: 5,
    name: "San Francisco",
    [getKey("enabled")]: true,
  };
  ```

<a name="es6-object-shorthand"></a><a name="3.5"></a>

- [3.3](#es6-object-shorthand) Use object method shorthand. eslint: [`object-shorthand`](https://eslint.org/docs/rules/object-shorthand)

  ```javascript
  // bad
  const atom = {
    value: 1,

    addValue: function (value) {
      return atom.value + value;
    },
  };

  // good
  const atom = {
    value: 1,

    addValue(value) {
      return atom.value + value;
    },
  };
  ```

<a name="es6-object-concise"></a><a name="3.6"></a>

- [3.4](#es6-object-concise) Use property value shorthand. eslint: [`object-shorthand`](https://eslint.org/docs/rules/object-shorthand)

  > Why? It is shorter and descriptive.

  ```javascript
  const lukeSkywalker = "Luke Skywalker";

  // bad
  const obj = {
    lukeSkywalker: lukeSkywalker,
  };

  // good
  const obj = {
    lukeSkywalker,
  };
  ```

<a name="objects--grouped-shorthand"></a><a name="3.7"></a>

- [3.5](#objects--grouped-shorthand) Group your shorthand properties at the beginning of your object declaration.

  > Why? It’s easier to tell which properties are using the shorthand.

  ```javascript
  const anakinSkywalker = "Anakin Skywalker";
  const lukeSkywalker = "Luke Skywalker";

  // bad
  const obj = {
    episodeOne: 1,
    twoJediWalkIntoACantina: 2,
    lukeSkywalker,
    episodeThree: 3,
    mayTheFourth: 4,
    anakinSkywalker,
  };

  // good
  const obj = {
    lukeSkywalker,
    anakinSkywalker,
    episodeOne: 1,
    twoJediWalkIntoACantina: 2,
    episodeThree: 3,
    mayTheFourth: 4,
  };
  ```

<a name="objects--quoted-props"></a><a name="3.8"></a>

- [3.6](#objects--quoted-props) Only quote properties that are invalid identifiers. eslint: [`quote-props`](https://eslint.org/docs/rules/quote-props)

  > Why? In general we consider it subjectively easier to read. It improves syntax highlighting, and is also more easily optimized by many JS engines.

  ```javascript
  // bad
  const bad = {
    foo: 3,
    bar: 4,
    "data-blah": 5,
  };

  // good
  const good = {
    foo: 3,
    bar: 4,
    "data-blah": 5,
  };
  ```

<a name="objects--prototype-builtins"></a>

- [3.7](#objects--prototype-builtins) Do not call `Object.prototype` methods directly, such as `hasOwnProperty`, `propertyIsEnumerable`, and `isPrototypeOf`. eslint: [`no-prototype-builtins`](https://eslint.org/docs/rules/no-prototype-builtins)

  > Why? These methods may be shadowed by properties on the object in question - consider `{ hasOwnProperty: false }` - or, the object may be a null object (`Object.create(null)`). In modern browsers that support ES2022, or with a polyfill such as <https://npmjs.com/object.hasown>, `Object.hasOwn` can also be used as an alternative to `Object.prototype.hasOwnProperty.call`.

  ```javascript
  // bad
  console.log(object.hasOwnProperty(key));

  // good
  console.log(Object.prototype.hasOwnProperty.call(object, key));

  // better
  const has = Object.prototype.hasOwnProperty; // cache the lookup once, in module scope.
  console.log(has.call(object, key));

  // best
  console.log(Object.hasOwn(object, key)); // only supported in browsers that support ES2022

  /* or */
  import has from "has"; // https://www.npmjs.com/package/has
  console.log(has(object, key));
  /* or */
  console.log(Object.hasOwn(object, key)); // https://www.npmjs.com/package/object.hasown
  ```

<a name="objects--rest-spread"></a>

- [3.8](#objects--rest-spread) Prefer the object spread syntax over [`Object.assign`](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/Object/assign) to shallow-copy objects. Use the object rest parameter syntax to get a new object with certain properties omitted. eslint: [`prefer-object-spread`](https://eslint.org/docs/rules/prefer-object-spread)

  ```javascript
  // very bad
  const original = { a: 1, b: 2 };
  const copy = Object.assign(original, { c: 3 }); // this mutates `original` ಠ_ಠ
  delete copy.a; // so does this

  // bad
  const original = { a: 1, b: 2 };
  const copy = Object.assign({}, original, { c: 3 }); // copy => { a: 1, b: 2, c: 3 }

  // good
  const original = { a: 1, b: 2 };
  const copy = { ...original, c: 3 }; // copy => { a: 1, b: 2, c: 3 }

  const { a, ...noA } = copy; // noA => { b: 2, c: 3 }
  ```

**[⬆ back to top](#table-of-contents)**

## Arrays

<a name="arrays--literals"></a><a name="4.1"></a>

- [4.1](#arrays--literals) Use the literal syntax for array creation. eslint: [`no-array-constructor`](https://eslint.org/docs/rules/no-array-constructor)

  ```javascript
  // bad
  const items = new Array();

  // good
  const items = [];
  ```

<a name="arrays--push"></a><a name="4.2"></a>

- [4.2](#arrays--push) Use [Array#push](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/Array/push) instead of direct assignment to add items to an array.

  ```javascript
  const someStack = [];

  // bad
  someStack[someStack.length] = "abracadabra";

  // good
  someStack.push("abracadabra");
  ```

<a name="es6-array-spreads"></a><a name="4.3"></a>

- [4.3](#es6-array-spreads) Use array spreads `...` to copy arrays.

  ```javascript
  // bad
  const len = items.length;
  const itemsCopy = [];
  let i;

  for (i = 0; i < len; i += 1) {
    itemsCopy[i] = items[i];
  }

  // good
  const itemsCopy = [...items];
  ```

<a name="arrays--from"></a>
<a name="arrays--from-iterable"></a><a name="4.4"></a>

- [4.4](#arrays--from-iterable) To convert an iterable object to an array, use spreads `...` instead of [`Array.from`](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/Array/from)

  ```javascript
  const foo = document.querySelectorAll(".foo");

  // good
  const nodes = Array.from(foo);

  // best
  const nodes = [...foo];
  ```

<a name="arrays--from-array-like"></a>

- [4.5](#arrays--from-array-like) Use [`Array.from`](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/Array/from) for converting an array-like object to an array.

  ```javascript
  const arrLike = { 0: "foo", 1: "bar", 2: "baz", length: 3 };

  // bad
  const arr = Array.prototype.slice.call(arrLike);

  // good
  const arr = Array.from(arrLike);
  ```

<a name="arrays--mapping"></a>

- [4.6](#arrays--mapping) Use [`Array.from`](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/Array/from) instead of spread `...` for mapping over iterables, because it avoids creating an intermediate array.

  ```javascript
  // bad
  const baz = [...foo].map(bar);

  // good
  const baz = Array.from(foo, bar);
  ```

<a name="arrays--callback-return"></a><a name="4.5"></a>

- [4.7](#arrays--callback-return) Use return statements in array method callbacks. It’s ok to omit the return if the function body consists of a single statement returning an expression without side effects, following [8.2](#arrows--implicit-return). eslint: [`array-callback-return`](https://eslint.org/docs/rules/array-callback-return)

  ```javascript
  // good
  [1, 2, 3].map((x) => {
    const y = x + 1;
    return x * y;
  });

  // good
  [1, 2, 3].map((x) => x + 1);

  // bad - no returned value means `acc` becomes undefined after the first iteration
  [
    [0, 1],
    [2, 3],
    [4, 5],
  ].reduce((acc, item, index) => {
    const flatten = acc.concat(item);
  });

  // good
  [
    [0, 1],
    [2, 3],
    [4, 5],
  ].reduce((acc, item, index) => {
    const flatten = acc.concat(item);
    return flatten;
  });

  // bad
  inbox.filter((msg) => {
    const { subject, author } = msg;
    if (subject === "Mockingbird") {
      return author === "Harper Lee";
    } else {
      return false;
    }
  });

  // good
  inbox.filter((msg) => {
    const { subject, author } = msg;
    if (subject === "Mockingbird") {
      return author === "Harper Lee";
    }

    return false;
  });
  ```

<a name="arrays--bracket-newline"></a>

- [4.8](#arrays--bracket-newline) Use line breaks after opening array brackets and before closing array brackets, if an array has multiple lines

  ```javascript
  // bad
  const arr = [
    [0, 1],
    [2, 3],
    [4, 5],
  ];

  const objectInArray = [
    {
      id: 1,
    },
    {
      id: 2,
    },
  ];

  const numberInArray = [1, 2];

  // good
  const arr = [
    [0, 1],
    [2, 3],
    [4, 5],
  ];

  const objectInArray = [
    {
      id: 1,
    },
    {
      id: 2,
    },
  ];

  const numberInArray = [1, 2];
  ```

**[⬆ back to top](#table-of-contents)**

## Destructuring

<a name="destructuring--object"></a><a name="5.1"></a>

- [5.1](#destructuring--object) Use object destructuring when accessing and using multiple properties of an object. eslint: [`prefer-destructuring`](https://eslint.org/docs/rules/prefer-destructuring)

  > Why? Destructuring saves you from creating temporary references for those properties, and from repetitive access of the object. Repeating object access creates more repetitive code, requires more reading, and creates more opportunities for mistakes. Destructuring objects also provides a single site of definition of the object structure that is used in the block, rather than requiring reading the entire block to determine what is used.

  ```javascript
  // bad
  function getFullName(user) {
    const firstName = user.firstName;
    const lastName = user.lastName;

    return `${firstName} ${lastName}`;
  }

  // good
  function getFullName(user) {
    const { firstName, lastName } = user;
    return `${firstName} ${lastName}`;
  }

  // best
  function getFullName({ firstName, lastName }) {
    return `${firstName} ${lastName}`;
  }
  ```

<a name="destructuring--array"></a><a name="5.2"></a>

- [5.2](#destructuring--array) Use array destructuring. eslint: [`prefer-destructuring`](https://eslint.org/docs/rules/prefer-destructuring)

  ```javascript
  const arr = [1, 2, 3, 4];

  // bad
  const first = arr[0];
  const second = arr[1];

  // good
  const [first, second] = arr;
  ```

<a name="destructuring--object-over-array"></a><a name="5.3"></a>

- [5.3](#destructuring--object-over-array) Use object destructuring for multiple return values, not array destructuring.

  > Why? You can add new properties over time or change the order of things without breaking call sites.

  ```javascript
  // bad
  function processInput(input) {
    // then a miracle occurs
    return [left, right, top, bottom];
  }

  // the caller needs to think about the order of return data
  const [left, __, top] = processInput(input);

  // good
  function processInput(input) {
    // then a miracle occurs
    return { left, right, top, bottom };
  }

  // the caller selects only the data they need
  const { left, top } = processInput(input);
  ```

**[⬆ back to top](#table-of-contents)**

## Strings

<a name="strings--quotes"></a><a name="6.1"></a>

- [6.1](#strings--quotes) Use single quotes `''` for strings. eslint: [`quotes`](https://eslint.org/docs/rules/quotes)

  ```javascript
  // bad
  const name = "Capt. Janeway";

  // bad - template literals should contain interpolation or newlines
  const name = `Capt. Janeway`;

  // good
  const name = "Capt. Janeway";
  ```

<a name="strings--line-length"></a><a name="6.2"></a>

- [6.2](#strings--line-length) Strings that cause the line to go over 100 characters should not be written across multiple lines using string concatenation.

  > Why? Broken strings are painful to work with and make code less searchable.

  ```javascript
  // bad
  const errorMessage =
    "This is a super long error that was thrown because \
  of Batman. When you stop to think about how Batman had anything to do \
  with this, you would get nowhere \
  fast.";

  // bad
  const errorMessage =
    "This is a super long error that was thrown because " +
    "of Batman. When you stop to think about how Batman had anything to do " +
    "with this, you would get nowhere fast.";

  // good
  const errorMessage =
    "This is a super long error that was thrown because of Batman. When you stop to think about how Batman had anything to do with this, you would get nowhere fast.";
  ```

<a name="es6-template-literals"></a><a name="6.4"></a>

- [6.3](#es6-template-literals) When programmatically building up strings, use template strings instead of concatenation. eslint: [`prefer-template`](https://eslint.org/docs/rules/prefer-template) [`template-curly-spacing`](https://eslint.org/docs/rules/template-curly-spacing)

  > Why? Template strings give you a readable, concise syntax with proper newlines and string interpolation features.

  ```javascript
  // bad
  function sayHi(name) {
    return "How are you, " + name + "?";
  }

  // bad
  function sayHi(name) {
    return ["How are you, ", name, "?"].join();
  }

  // bad
  function sayHi(name) {
    return `How are you, ${name}?`;
  }

  // good
  function sayHi(name) {
    return `How are you, ${name}?`;
  }
  ```

<a name="strings--eval"></a><a name="6.5"></a>

- [6.4](#strings--eval) Never use `eval()` on a string; it opens too many vulnerabilities. eslint: [`no-eval`](https://eslint.org/docs/rules/no-eval)

<a name="strings--escaping"></a>

- [6.5](#strings--escaping) Do not unnecessarily escape characters in strings. eslint: [`no-useless-escape`](https://eslint.org/docs/rules/no-useless-escape)

  > Why? Backslashes harm readability, thus they should only be present when necessary.

  ```javascript
  // bad
  const foo = "'this' is \"quoted\"";

  // good
  const foo = "'this' is \"quoted\"";
  const foo = `my name is '${name}'`;
  ```

**[⬆ back to top](#table-of-contents)**

## Functions

<a name="functions--declarations"></a><a name="7.1"></a>

- [7.1](#functions--declarations) Use named function expressions instead of function declarations. eslint: [`func-style`](https://eslint.org/docs/rules/func-style), [`func-names`](https://eslint.org/docs/latest/rules/func-names)

  > Why? Function declarations are hoisted, which means that it’s easy - too easy - to reference the function before it is defined in the file. This harms readability and maintainability. If you find that a function’s definition is large or complex enough that it is interfering with understanding the rest of the file, then perhaps it’s time to extract it to its own module! Don’t forget to explicitly name the expression, regardless of whether or not the name is inferred from the containing variable (which is often the case in modern browsers or when using compilers such as Babel). This eliminates any assumptions made about the Error’s call stack. ([Discussion](https://github.com/airbnb/javascript/issues/794))

  ```javascript
  // bad
  function foo() {
    // ...
  }

  // bad
  const foo = function () {
    // ...
  };

  // good
  // lexical name distinguished from the variable-referenced invocation(s)
  const short = function longUniqueMoreDescriptiveLexicalFoo() {
    // ...
  };
  ```

<a name="functions--iife"></a><a name="7.2"></a>

- [7.2](#functions--iife) Wrap immediately invoked function expressions in parentheses. eslint: [`wrap-iife`](https://eslint.org/docs/rules/wrap-iife)

  > Why? An immediately invoked function expression is a single unit - wrapping both it, and its invocation parens, in parens, cleanly expresses this. Note that in a world with modules everywhere, you almost never need an IIFE.

  ```javascript
  // immediately-invoked function expression (IIFE)
  (function () {
    console.log("Welcome to the Internet. Please follow me.");
  })();
  ```

<a name="functions--in-blocks"></a><a name="7.3"></a>

- [7.3](#functions--in-blocks) Never declare a function in a non-function block (`if`, `while`, etc). Assign the function to a variable instead. Browsers will allow you to do it, but they all interpret it differently, which is bad news bears. eslint: [`no-loop-func`](https://eslint.org/docs/rules/no-loop-func)

<a name="functions--note-on-blocks"></a><a name="7.4"></a>

- [7.4](#functions--note-on-blocks) **Note:** ECMA-262 defines a `block` as a list of statements. A function declaration is not a statement.

  ```javascript
  // bad
  if (currentUser) {
    function test() {
      console.log("Nope.");
    }
  }

  // good
  let test;
  if (currentUser) {
    test = () => {
      console.log("Yup.");
    };
  }
  ```

<a name="functions--arguments-shadow"></a><a name="7.5"></a>

- [7.5](#functions--arguments-shadow) Never name a parameter `arguments`. This will take precedence over the `arguments` object that is given to every function scope.

  ```javascript
  // bad
  function foo(name, options, arguments) {
    // ...
  }

  // good
  function foo(name, options, args) {
    // ...
  }
  ```

<a name="es6-rest"></a><a name="7.6"></a>

- [7.6](#es6-rest) Never use `arguments`, opt to use rest syntax `...` instead. eslint: [`prefer-rest-params`](https://eslint.org/docs/rules/prefer-rest-params)

  > Why? `...` is explicit about which arguments you want pulled. Plus, rest arguments are a real Array, and not merely Array-like like `arguments`.

  ```javascript
  // bad
  function concatenateAll() {
    const args = Array.prototype.slice.call(arguments);
    return args.join("");
  }

  // good
  function concatenateAll(...args) {
    return args.join("");
  }
  ```

<a name="es6-default-parameters"></a><a name="7.7"></a>

- [7.7](#es6-default-parameters) Use default parameter syntax rather than mutating function arguments.

  ```javascript
  // really bad
  function handleThings(opts) {
    // No! We shouldn’t mutate function arguments.
    // Double bad: if opts is falsy it'll be set to an object which may
    // be what you want but it can introduce subtle bugs.
    opts = opts || {};
    // ...
  }

  // still bad
  function handleThings(opts) {
    if (opts === void 0) {
      opts = {};
    }
    // ...
  }

  // good
  function handleThings(opts = {}) {
    // ...
  }
  ```

<a name="functions--default-side-effects"></a><a name="7.8"></a>

- [7.8](#functions--default-side-effects) Avoid side effects with default parameters.

  > Why? They are confusing to reason about.

  ```javascript
  let b = 1;
  // bad
  function count(a = b++) {
    console.log(a);
  }
  count(); // 1
  count(); // 2
  count(3); // 3
  count(); // 3
  ```

<a name="functions--defaults-last"></a><a name="7.9"></a>

- [7.9](#functions--defaults-last) Always put default parameters last. eslint: [`default-param-last`](https://eslint.org/docs/rules/default-param-last)

  ```javascript
  // bad
  function handleThings(opts = {}, name) {
    // ...
  }

  // good
  function handleThings(name, opts = {}) {
    // ...
  }
  ```

<a name="functions--constructor"></a><a name="7.10"></a>

- [7.10](#functions--constructor) Never use the Function constructor to create a new function. eslint: [`no-new-func`](https://eslint.org/docs/rules/no-new-func)

  > Why? Creating a function in this way evaluates a string similarly to `eval()`, which opens vulnerabilities.

  ```javascript
  // bad
  const add = new Function("a", "b", "return a + b");

  // still bad
  const subtract = Function("a", "b", "return a - b");
  ```

<a name="functions--signature-spacing"></a><a name="7.11"></a>

- [7.11](#functions--signature-spacing) Spacing in a function signature. eslint: [`space-before-function-paren`](https://eslint.org/docs/rules/space-before-function-paren) [`space-before-blocks`](https://eslint.org/docs/rules/space-before-blocks)

  > Why? Consistency is good, and you shouldn’t have to add or remove a space when adding or removing a name.

  ```javascript
  // bad
  const f = function () {};
  const g = function () {};
  const h = function () {};

  // good
  const x = function () {};
  const y = function a() {};
  ```

<a name="functions--mutate-params"></a><a name="7.12"></a>

- [7.12](#functions--mutate-params) Never mutate parameters. eslint: [`no-param-reassign`](https://eslint.org/docs/rules/no-param-reassign)

  > Why? Manipulating objects passed in as parameters can cause unwanted variable side effects in the original caller.

  ```javascript
  // bad
  function f1(obj) {
    obj.key = 1;
  }

  // good
  function f2(obj) {
    const key = Object.prototype.hasOwnProperty.call(obj, "key") ? obj.key : 1;
  }
  ```

<a name="functions--reassign-params"></a><a name="7.13"></a>

- [7.13](#functions--reassign-params) Never reassign parameters. eslint: [`no-param-reassign`](https://eslint.org/docs/rules/no-param-reassign)

  > Why? Reassigning parameters can lead to unexpected behavior, especially when accessing the `arguments` object. It can also cause optimization issues, especially in V8.

  ```javascript
  // bad
  function f1(a) {
    a = 1;
    // ...
  }

  function f2(a) {
    if (!a) {
      a = 1;
    }
    // ...
  }

  // good
  function f3(a) {
    const b = a || 1;
    // ...
  }

  function f4(a = 1) {
    // ...
  }
  ```

<a name="functions--spread-vs-apply"></a><a name="7.14"></a>

- [7.14](#functions--spread-vs-apply) Prefer the use of the spread syntax `...` to call variadic functions. eslint: [`prefer-spread`](https://eslint.org/docs/rules/prefer-spread)

  > Why? It’s cleaner, you don’t need to supply a context, and you can not easily compose `new` with `apply`.

  ```javascript
  // bad
  const x = [1, 2, 3, 4, 5];
  console.log.apply(console, x);

  // good
  const x = [1, 2, 3, 4, 5];
  console.log(...x);

  // bad
  new (Function.prototype.bind.apply(Date, [null, 2016, 8, 5]))();

  // good
  new Date(...[2016, 8, 5]);
  ```

<a name="functions--signature-invocation-indentation"></a>

- [7.15](#functions--signature-invocation-indentation) Functions with multiline signatures, or invocations, should be indented just like every other multiline list in this guide: with each item on a line by itself, with a trailing comma on the last item. eslint: [`function-paren-newline`](https://eslint.org/docs/rules/function-paren-newline)

  ```javascript
  // bad
  function foo(bar, baz, quux) {
    // ...
  }

  // good
  function foo(bar, baz, quux) {
    // ...
  }

  // bad
  console.log(foo, bar, baz);

  // good
  console.log(foo, bar, baz);
  ```

**[⬆ back to top](#table-of-contents)**

## Arrow Functions

<a name="arrows--use-them"></a><a name="8.1"></a>

- [8.1](#arrows--use-them) When you must use an anonymous function (as when passing an inline callback), use arrow function notation. eslint: [`prefer-arrow-callback`](https://eslint.org/docs/rules/prefer-arrow-callback), [`arrow-spacing`](https://eslint.org/docs/rules/arrow-spacing)

  > Why? It creates a version of the function that executes in the context of `this`, which is usually what you want, and is a more concise syntax.

  > Why not? If you have a fairly complicated function, you might move that logic out into its own named function expression.

  ```javascript
  // bad
  [1, 2, 3].map(function (x) {
    const y = x + 1;
    return x * y;
  });

  // good
  [1, 2, 3].map((x) => {
    const y = x + 1;
    return x * y;
  });
  ```

<a name="arrows--implicit-return"></a><a name="8.2"></a>

- [8.2](#arrows--implicit-return) If the function body consists of a single statement returning an [expression](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators#Expressions) without side effects, omit the braces and use the implicit return. Otherwise, keep the braces and use a `return` statement. eslint: [`arrow-parens`](https://eslint.org/docs/rules/arrow-parens), [`arrow-body-style`](https://eslint.org/docs/rules/arrow-body-style)

  > Why? Syntactic sugar. It reads well when multiple functions are chained together.

  ```javascript
  // bad
  [1, 2, 3].map((number) => {
    const nextNumber = number + 1;
    `A string containing the ${nextNumber}.`;
  });

  // good
  [1, 2, 3].map((number) => `A string containing the ${number + 1}.`);

  // good
  [1, 2, 3].map((number) => {
    const nextNumber = number + 1;
    return `A string containing the ${nextNumber}.`;
  });

  // good
  [1, 2, 3].map((number, index) => ({
    [index]: number,
  }));

  // No implicit return with side effects
  function foo(callback) {
    const val = callback();
    if (val === true) {
      // Do something if callback returns true
    }
  }

  let bool = false;

  // bad
  foo(() => (bool = true));

  // good
  foo(() => {
    bool = true;
  });
  ```

<a name="arrows--paren-wrap"></a><a name="8.3"></a>

- [8.3](#arrows--paren-wrap) In case the expression spans over multiple lines, wrap it in parentheses for better readability.

  > Why? It shows clearly where the function starts and ends.

  ```javascript
  // bad
  ["get", "post", "put"].map((httpMethod) =>
    Object.prototype.hasOwnProperty.call(
      httpMagicObjectWithAVeryLongName,
      httpMethod
    )
  );

  // good
  ["get", "post", "put"].map((httpMethod) =>
    Object.prototype.hasOwnProperty.call(
      httpMagicObjectWithAVeryLongName,
      httpMethod
    )
  );
  ```

<a name="arrows--one-arg-parens"></a><a name="8.4"></a>

- [8.4](#arrows--one-arg-parens) Always include parentheses around arguments for clarity and consistency. eslint: [`arrow-parens`](https://eslint.org/docs/rules/arrow-parens)

  > Why? Minimizes diff churn when adding or removing arguments.

  ```javascript
  // bad
  [1, 2, 3].map((x) => x * x);

  // good
  [1, 2, 3].map((x) => x * x);

  // bad
  [1, 2, 3].map(
    (number) =>
      `A long string with the ${number}. It’s so long that we don’t want it to take up space on the .map line!`
  );

  // good
  [1, 2, 3].map(
    (number) =>
      `A long string with the ${number}. It’s so long that we don’t want it to take up space on the .map line!`
  );

  // bad
  [1, 2, 3].map((x) => {
    const y = x + 1;
    return x * y;
  });

  // good
  [1, 2, 3].map((x) => {
    const y = x + 1;
    return x * y;
  });
  ```

<a name="arrows--confusing"></a><a name="8.5"></a>

- [8.5](#arrows--confusing) Avoid confusing arrow function syntax (`=>`) with comparison operators (`<=`, `>=`). eslint: [`no-confusing-arrow`](https://eslint.org/docs/rules/no-confusing-arrow)

  ```javascript
  // bad
  const itemHeight = (item) =>
    item.height <= 256 ? item.largeSize : item.smallSize;

  // bad
  const itemHeight = (item) =>
    item.height >= 256 ? item.largeSize : item.smallSize;

  // good
  const itemHeight = (item) =>
    item.height <= 256 ? item.largeSize : item.smallSize;

  // good
  const itemHeight = (item) => {
    const { height, largeSize, smallSize } = item;
    return height <= 256 ? largeSize : smallSize;
  };
  ```

<a name="whitespace--implicit-arrow-linebreak"></a>

- [8.6](#whitespace--implicit-arrow-linebreak) Enforce the location of arrow function bodies with implicit returns. eslint: [`implicit-arrow-linebreak`](https://eslint.org/docs/rules/implicit-arrow-linebreak)

  ```javascript
  // bad
  (foo) => bar;

  (foo) => bar;

  // good
  (foo) => bar;
  (foo) => bar;
  (foo) => bar;
  ```

**[⬆ back to top](#table-of-contents)**

## Classes & Constructors

<a name="constructors--use-class"></a><a name="9.1"></a>

- [9.1](#constructors--use-class) Always use `class`. Avoid manipulating `prototype` directly.

  > Why? `class` syntax is more concise and easier to reason about.

  ```javascript
  // bad
  function Queue(contents = []) {
    this.queue = [...contents];
  }
  Queue.prototype.pop = function () {
    const value = this.queue[0];
    this.queue.splice(0, 1);
    return value;
  };

  // good
  class Queue {
    constructor(contents = []) {
      this.queue = [...contents];
    }
    pop() {
      const value = this.queue[0];
      this.queue.splice(0, 1);
      return value;
    }
  }
  ```

<a name="constructors--extends"></a><a name="9.2"></a>

- [9.2](#constructors--extends) Use `extends` for inheritance.

  > Why? It is a built-in way to inherit prototype functionality without breaking `instanceof`.

  ```javascript
  // bad
  const inherits = require("inherits");
  function PeekableQueue(contents) {
    Queue.apply(this, contents);
  }
  inherits(PeekableQueue, Queue);
  PeekableQueue.prototype.peek = function () {
    return this.queue[0];
  };

  // good
  class PeekableQueue extends Queue {
    peek() {
      return this.queue[0];
    }
  }
  ```

<a name="constructors--chaining"></a><a name="9.3"></a>

- [9.3](#constructors--chaining) Methods can return `this` to help with method chaining.

  ```javascript
  // bad
  Jedi.prototype.jump = function () {
    this.jumping = true;
    return true;
  };

  Jedi.prototype.setHeight = function (height) {
    this.height = height;
  };

  const luke = new Jedi();
  luke.jump(); // => true
  luke.setHeight(20); // => undefined

  // good
  class Jedi {
    jump() {
      this.jumping = true;
      return this;
    }

    setHeight(height) {
      this.height = height;
      return this;
    }
  }

  const luke = new Jedi();

  luke.jump().setHeight(20);
  ```

<a name="constructors--tostring"></a><a name="9.4"></a>

- [9.4](#constructors--tostring) It’s okay to write a custom `toString()` method, just make sure it works successfully and causes no side effects.

  ```javascript
  class Jedi {
    constructor(options = {}) {
      this.name = options.name || "no name";
    }

    getName() {
      return this.name;
    }

    toString() {
      return `Jedi - ${this.getName()}`;
    }
  }
  ```

<a name="constructors--no-useless"></a><a name="9.5"></a>

- [9.5](#constructors--no-useless) Classes have a default constructor if one is not specified. An empty constructor function or one that just delegates to a parent class is unnecessary. eslint: [`no-useless-constructor`](https://eslint.org/docs/rules/no-useless-constructor)

  ```javascript
  // bad
  class Jedi {
    constructor() {}

    getName() {
      return this.name;
    }
  }

  // bad
  class Rey extends Jedi {
    constructor(...args) {
      super(...args);
    }
  }

  // good
  class Rey extends Jedi {
    constructor(...args) {
      super(...args);
      this.name = "Rey";
    }
  }
  ```

<a name="classes--no-duplicate-members"></a>

- [9.6](#classes--no-duplicate-members) Avoid duplicate class members. eslint: [`no-dupe-class-members`](https://eslint.org/docs/rules/no-dupe-class-members)

  > Why? Duplicate class member declarations will silently prefer the last one - having duplicates is almost certainly a bug.

  ```javascript
  // bad
  class Foo {
    bar() {
      return 1;
    }
    bar() {
      return 2;
    }
  }

  // good
  class Foo {
    bar() {
      return 1;
    }
  }

  // good
  class Foo {
    bar() {
      return 2;
    }
  }
  ```

<a name="classes--methods-use-this"></a>

- [9.7](#classes--methods-use-this) Class methods should use `this` or be made into a static method unless an external library or framework requires using specific non-static methods. Being an instance method should indicate that it behaves differently based on properties of the receiver. eslint: [`class-methods-use-this`](https://eslint.org/docs/rules/class-methods-use-this)

  ```javascript
  // bad
  class Foo {
    bar() {
      console.log("bar");
    }
  }

  // good - this is used
  class Foo {
    bar() {
      console.log(this.bar);
    }
  }

  // good - constructor is exempt
  class Foo {
    constructor() {
      // ...
    }
  }

  // good - static methods aren't expected to use this
  class Foo {
    static bar() {
      console.log("bar");
    }
  }
  ```

**[⬆ back to top](#table-of-contents)**

## Modules

<a name="modules--use-them"></a><a name="10.1"></a>

- [10.1](#modules--use-them) Always use modules (`import`/`export`) over a non-standard module system. You can always transpile to your preferred module system.

  > Why? Modules are the future, let’s start using the future now.

  ```javascript
  // bad
  const AirbnbStyleGuide = require('./AirbnbStyleGuide');
  module.exports = AirbnbStyleGuide.es6;

  // ok
  import AirbnbStyleGuide from './AirbnbStyleGuide';
  export default AirbnbStyleGuide.es6;

  // best
  import { es6 } from './AirbnbStyleGuide';
  export default es6;
  ```

<a name="modules--no-wildcard"></a><a name="10.2"></a>

- [10.2](#modules--no-wildcard) Do not use wildcard imports.

  > Why? This makes sure you have a single default export.

  ```javascript
  // bad
  import * as AirbnbStyleGuide from "./AirbnbStyleGuide";

  // good
  import AirbnbStyleGuide from "./AirbnbStyleGuide";
  ```

<a name="modules--no-export-from-import"></a><a name="10.3"></a>

- [10.3](#modules--no-export-from-import) And do not export directly from an import.

  > Why? Although the one-liner is concise, having one clear way to import and one clear way to export makes things consistent.

  ```javascript
  // bad
  // filename es6.js
  export { es6 as default } from './AirbnbStyleGuide';

  // good
  // filename es6.js
  import { es6 } from './AirbnbStyleGuide';
  export default es6;
  ```

<a name="modules--no-duplicate-imports"></a>

- [10.4](#modules--no-duplicate-imports) Only import from a path in one place.
  eslint: [`no-duplicate-imports`](https://eslint.org/docs/rules/no-duplicate-imports)

  > Why? Having multiple lines that import from the same path can make code harder to maintain.

  ```javascript
  // bad
  import foo from "foo";
  // … some other imports … //
  import { named1, named2 } from "foo";

  // good
  import foo, { named1, named2 } from "foo";

  // good
  import foo, { named1, named2 } from "foo";
  ```

<a name="modules--no-mutable-exports"></a>

- [10.5](#modules--no-mutable-exports) Do not export mutable bindings.
  eslint: [`import/no-mutable-exports`](https://github.com/import-js/eslint-plugin-import/blob/master/docs/rules/no-mutable-exports.md)

  > Why? Mutation should be avoided in general, but in particular when exporting mutable bindings. While this technique may be needed for some special cases, in general, only constant references should be exported.

  ```javascript
  // bad
  let foo = 3;
  export { foo };

  // good
  const foo = 3;
  export { foo };
  ```

<a name="modules--prefer-default-export"></a>

- [10.6](#modules--prefer-default-export) In modules with a single export, prefer default export over named export.
  eslint: [`import/prefer-default-export`](https://github.com/import-js/eslint-plugin-import/blob/master/docs/rules/prefer-default-export.md)

  > Why? To encourage more files that only ever export one thing, which is better for readability and maintainability.

  ```javascript
  // bad
  export function foo() {}

  // good
  export default function foo() {}
  ```

<a name="modules--imports-first"></a>

- [10.7](#modules--imports-first) Put all `import`s above non-import statements.
  eslint: [`import/first`](https://github.com/import-js/eslint-plugin-import/blob/master/docs/rules/first.md)

  > Why? Since `import`s are hoisted, keeping them all at the top prevents surprising behavior.

  ```javascript
  // bad
  import foo from "foo";
  foo.init();

  import bar from "bar";

  // good
  import foo from "foo";
  import bar from "bar";

  foo.init();
  ```

<a name="modules--multiline-imports-over-newlines"></a>

- [10.8](#modules--multiline-imports-over-newlines) Multiline imports should be indented just like multiline array and object literals.
  eslint: [`object-curly-newline`](https://eslint.org/docs/rules/object-curly-newline)

  > Why? The curly braces follow the same indentation rules as every other curly brace block in the style guide, as do the trailing commas.

  ```javascript
  // bad
  import { longNameA, longNameB, longNameC, longNameD, longNameE } from "path";

  // good
  import { longNameA, longNameB, longNameC, longNameD, longNameE } from "path";
  ```

<a name="modules--no-webpack-loader-syntax"></a>

- [10.9](#modules--no-webpack-loader-syntax) Disallow Webpack loader syntax in module import statements.
  eslint: [`import/no-webpack-loader-syntax`](https://github.com/import-js/eslint-plugin-import/blob/master/docs/rules/no-webpack-loader-syntax.md)

  > Why? Since using Webpack syntax in the imports couples the code to a module bundler. Prefer using the loader syntax in `webpack.config.js`.

  ```javascript
  // bad
  import fooSass from "css!sass!foo.scss";
  import barCss from "style!css!bar.css";

  // good
  import fooSass from "foo.scss";
  import barCss from "bar.css";
  ```

<a name="modules--import-extensions"></a>

- [10.10](#modules--import-extensions) Do not include JavaScript filename extensions
  eslint: [`import/extensions`](https://github.com/import-js/eslint-plugin-import/blob/master/docs/rules/extensions.md)

  > Why? Including extensions inhibits refactoring, and inappropriately hardcodes implementation details of the module you're importing in every consumer.

  ```javascript
  // bad
  import foo from "./foo.js";
  import bar from "./bar.jsx";
  import baz from "./baz/index.jsx";

  // good
  import foo from "./foo";
  import bar from "./bar";
  import baz from "./baz";
  ```

**[⬆ back to top](#table-of-contents)**

## Iterators and Generators

<a name="iterators--nope"></a><a name="11.1"></a>

- [11.1](#iterators--nope) Don’t use iterators. Prefer JavaScript’s higher-order functions instead of loops like `for-in` or `for-of`. eslint: [`no-iterator`](https://eslint.org/docs/rules/no-iterator) [`no-restricted-syntax`](https://eslint.org/docs/rules/no-restricted-syntax)

  > Why? This enforces our immutable rule. Dealing with pure functions that return values is easier to reason about than side effects.

  > Use `map()` / `every()` / `filter()` / `find()` / `findIndex()` / `reduce()` / `some()` / ... to iterate over arrays, and `Object.keys()` / `Object.values()` / `Object.entries()` to produce arrays so you can iterate over objects.

  ```javascript
  const numbers = [1, 2, 3, 4, 5];

  // bad
  let sum = 0;
  for (let num of numbers) {
    sum += num;
  }
  sum === 15;

  // good
  let sum = 0;
  numbers.forEach((num) => {
    sum += num;
  });
  sum === 15;

  // best (use the functional force)
  const sum = numbers.reduce((total, num) => total + num, 0);
  sum === 15;

  // bad
  const increasedByOne = [];
  for (let i = 0; i < numbers.length; i++) {
    increasedByOne.push(numbers[i] + 1);
  }

  // good
  const increasedByOne = [];
  numbers.forEach((num) => {
    increasedByOne.push(num + 1);
  });

  // best (keeping it functional)
  const increasedByOne = numbers.map((num) => num + 1);
  ```

<a name="generators--nope"></a><a name="11.2"></a>

- [11.2](#generators--nope) Don’t use generators for now.

  > Why? They don’t transpile well to ES5.

<a name="generators--spacing"></a>

- [11.3](#generators--spacing) If you must use generators, or if you disregard [our advice](#generators--nope), make sure their function signature is spaced properly. eslint: [`generator-star-spacing`](https://eslint.org/docs/rules/generator-star-spacing)

  > Why? `function` and `*` are part of the same conceptual keyword - `*` is not a modifier for `function`, `function*` is a unique construct, different from `function`.

  ```javascript
  // bad
  function* foo() {
    // ...
  }

  // bad
  const bar = function* () {
    // ...
  };

  // bad
  const baz = function* () {
    // ...
  };

  // bad
  const quux = function* () {
    // ...
  };

  // bad
  function* foo() {
    // ...
  }

  // bad
  function* foo() {
    // ...
  }

  // very bad
  function* foo() {
    // ...
  }

  // very bad
  const wat = function* () {
    // ...
  };

  // good
  function* foo() {
    // ...
  }

  // good
  const foo = function* () {
    // ...
  };
  ```

**[⬆ back to top](#table-of-contents)**

## Properties

<a name="properties--dot"></a><a name="12.1"></a>

- [12.1](#properties--dot) Use dot notation when accessing properties. eslint: [`dot-notation`](https://eslint.org/docs/rules/dot-notation)

  ```javascript
  const luke = {
    jedi: true,
    age: 28,
  };

  // bad
  const isJedi = luke["jedi"];

  // good
  const isJedi = luke.jedi;
  ```

<a name="properties--bracket"></a><a name="12.2"></a>

- [12.2](#properties--bracket) Use bracket notation `[]` when accessing properties with a variable.

  ```javascript
  const luke = {
    jedi: true,
    age: 28,
  };

  function getProp(prop) {
    return luke[prop];
  }

  const isJedi = getProp("jedi");
  ```

<a name="es2016-properties--exponentiation-operator"></a>

- [12.3](#es2016-properties--exponentiation-operator) Use exponentiation operator `**` when calculating exponentiations. eslint: [`prefer-exponentiation-operator`](https://eslint.org/docs/rules/prefer-exponentiation-operator).

  ```javascript
  // bad
  const binary = Math.pow(2, 10);

  // good
  const binary = 2 ** 10;
  ```

**[⬆ back to top](#table-of-contents)**

## Variables

<a name="variables--const"></a><a name="13.1"></a>

- [13.1](#variables--const) Always use `const` or `let` to declare variables. Not doing so will result in global variables. We want to avoid polluting the global namespace. Captain Planet warned us of that. eslint: [`no-undef`](https://eslint.org/docs/rules/no-undef) [`prefer-const`](https://eslint.org/docs/rules/prefer-const)

  ```javascript
  // bad
  superPower = new SuperPower();

  // good
  const superPower = new SuperPower();
  ```

<a name="variables--one-const"></a><a name="13.2"></a>

- [13.2](#variables--one-const) Use one `const` or `let` declaration per variable or assignment. eslint: [`one-var`](https://eslint.org/docs/rules/one-var)

  > Why? It’s easier to add new variable declarations this way, and you never have to worry about swapping out a `;` for a `,` or introducing punctuation-only diffs. You can also step through each declaration with the debugger, instead of jumping through all of them at once.

  ```javascript
  // bad
  const items = getItems(),
    goSportsTeam = true,
    dragonball = "z";

  // bad
  // (compare to above, and try to spot the mistake)
  const items = getItems(),
    goSportsTeam = true;
  dragonball = "z";

  // good
  const items = getItems();
  const goSportsTeam = true;
  const dragonball = "z";
  ```

<a name="variables--const-let-group"></a><a name="13.3"></a>

- [13.3](#variables--const-let-group) Group all your `const`s and then group all your `let`s.

  > Why? This is helpful when later on you might need to assign a variable depending on one of the previously assigned variables.

  ```javascript
  // bad
  let i,
    len,
    dragonball,
    items = getItems(),
    goSportsTeam = true;

  // bad
  let i;
  const items = getItems();
  let dragonball;
  const goSportsTeam = true;
  let len;

  // good
  const goSportsTeam = true;
  const items = getItems();
  let dragonball;
  let i;
  let length;
  ```

<a name="variables--define-where-used"></a><a name="13.4"></a>

- [13.4](#variables--define-where-used) Assign variables where you need them, but place them in a reasonable place.

  > Why? `let` and `const` are block scoped and not function scoped.

  ```javascript
  // bad - unnecessary function call
  function checkName(hasName) {
    const name = getName();

    if (hasName === "test") {
      return false;
    }

    if (name === "test") {
      this.setName("");
      return false;
    }

    return name;
  }

  // good
  function checkName(hasName) {
    if (hasName === "test") {
      return false;
    }

    const name = getName();

    if (name === "test") {
      this.setName("");
      return false;
    }

    return name;
  }
  ```

<a name="variables--no-chain-assignment"></a><a name="13.5"></a>

- [13.5](#variables--no-chain-assignment) Don’t chain variable assignments. eslint: [`no-multi-assign`](https://eslint.org/docs/rules/no-multi-assign)

  > Why? Chaining variable assignments creates implicit global variables.

  ```javascript
  // bad
  (function example() {
    // JavaScript interprets this as
    // let a = ( b = ( c = 1 ) );
    // The let keyword only applies to variable a; variables b and c become
    // global variables.
    let a = (b = c = 1);
  })();

  console.log(a); // throws ReferenceError
  console.log(b); // 1
  console.log(c); // 1

  // good
  (function example() {
    let a = 1;
    let b = a;
    let c = a;
  })();

  console.log(a); // throws ReferenceError
  console.log(b); // throws ReferenceError
  console.log(c); // throws ReferenceError

  // the same applies for `const`
  ```

<a name="variables--unary-increment-decrement"></a><a name="13.6"></a>

- [13.6](#variables--unary-increment-decrement) Avoid using unary increments and decrements (`++`, `--`). eslint [`no-plusplus`](https://eslint.org/docs/rules/no-plusplus)

  > Why? Per the eslint documentation, unary increment and decrement statements are subject to automatic semicolon insertion and can cause silent errors with incrementing or decrementing values within an application. It is also more expressive to mutate your values with statements like `num += 1` instead of `num++` or `num ++`. Disallowing unary increment and decrement statements also prevents you from pre-incrementing/pre-decrementing values unintentionally which can also cause unexpected behavior in your programs.

  ```javascript
  // bad

  const array = [1, 2, 3];
  let num = 1;
  num++;
  --num;

  let sum = 0;
  let truthyCount = 0;
  for (let i = 0; i < array.length; i++) {
    let value = array[i];
    sum += value;
    if (value) {
      truthyCount++;
    }
  }

  // good

  const array = [1, 2, 3];
  let num = 1;
  num += 1;
  num -= 1;

  const sum = array.reduce((a, b) => a + b, 0);
  const truthyCount = array.filter(Boolean).length;
  ```

<a name="variables--linebreak"></a>

- [13.7](#variables--linebreak) Avoid linebreaks before or after `=` in an assignment. If your assignment violates [`max-len`](https://eslint.org/docs/rules/max-len), surround the value in parens. eslint [`operator-linebreak`](https://eslint.org/docs/rules/operator-linebreak).

  > Why? Linebreaks surrounding `=` can obfuscate the value of an assignment.

  ```javascript
  // bad
  const foo = superLongLongLongLongLongLongLongLongFunctionName();

  // bad
  const foo = "superLongLongLongLongLongLongLongLongString";

  // good
  const foo = superLongLongLongLongLongLongLongLongFunctionName();

  // good
  const foo = "superLongLongLongLongLongLongLongLongString";
  ```

<a name="variables--no-unused-vars"></a>

- [13.8](#variables--no-unused-vars) Disallow unused variables. eslint: [`no-unused-vars`](https://eslint.org/docs/rules/no-unused-vars)

  > Why? Variables that are declared and not used anywhere in the code are most likely an error due to incomplete refactoring. Such variables take up space in the code and can lead to confusion by readers.

  ```javascript
  // bad

  const some_unused_var = 42;

  // Write-only variables are not considered as used.
  let y = 10;
  y = 5;

  // A read for a modification of itself is not considered as used.
  let z = 0;
  z = z + 1;

  // Unused function arguments.
  function getX(x, y) {
    return x;
  }

  // good

  function getXPlusY(x, y) {
    return x + y;
  }

  const x = 1;
  const y = a + 2;

  alert(getXPlusY(x, y));

  // 'type' is ignored even if unused because it has a rest property sibling.
  // This is a form of extracting an object that omits the specified keys.
  const { type, ...coords } = data;
  // 'coords' is now the 'data' object without its 'type' property.
  ```

**[⬆ back to top](#table-of-contents)**

## Hoisting

<a name="hoisting--about"></a><a name="14.1"></a>

- [14.1](#hoisting--about) `var` declarations get hoisted to the top of their closest enclosing function scope, their assignment does not. `const` and `let` declarations are blessed with a new concept called [Temporal Dead Zones (TDZ)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let#temporal_dead_zone_tdz). It’s important to know why [typeof is no longer safe](https://web.archive.org/web/20200121061528/http://es-discourse.com/t/why-typeof-is-no-longer-safe/15).

  ```javascript
  // we know this wouldn’t work (assuming there
  // is no notDefined global variable)
  function example() {
    console.log(notDefined); // => throws a ReferenceError
  }

  // creating a variable declaration after you
  // reference the variable will work due to
  // variable hoisting. Note: the assignment
  // value of `true` is not hoisted.
  function example() {
    console.log(declaredButNotAssigned); // => undefined
    var declaredButNotAssigned = true;
  }

  // the interpreter is hoisting the variable
  // declaration to the top of the scope,
  // which means our example could be rewritten as:
  function example() {
    let declaredButNotAssigned;
    console.log(declaredButNotAssigned); // => undefined
    declaredButNotAssigned = true;
  }

  // using const and let
  function example() {
    console.log(declaredButNotAssigned); // => throws a ReferenceError
    console.log(typeof declaredButNotAssigned); // => throws a ReferenceError
    const declaredButNotAssigned = true;
  }
  ```

<a name="hoisting--anon-expressions"></a><a name="14.2"></a>

- [14.2](#hoisting--anon-expressions) Anonymous function expressions hoist their variable name, but not the function assignment.

  ```javascript
  function example() {
    console.log(anonymous); // => undefined

    anonymous(); // => TypeError anonymous is not a function

    var anonymous = function () {
      console.log("anonymous function expression");
    };
  }
  ```

<a name="hoisting--named-expresions"></a><a name="hoisting--named-expressions"></a><a name="14.3"></a>

- [14.3](#hoisting--named-expressions) Named function expressions hoist the variable name, not the function name or the function body.

  ```javascript
  function example() {
    console.log(named); // => undefined

    named(); // => TypeError named is not a function

    superPower(); // => ReferenceError superPower is not defined

    var named = function superPower() {
      console.log("Flying");
    };
  }

  // the same is true when the function name
  // is the same as the variable name.
  function example() {
    console.log(named); // => undefined

    named(); // => TypeError named is not a function

    var named = function named() {
      console.log("named");
    };
  }
  ```

<a name="hoisting--declarations"></a><a name="14.4"></a>

- [14.4](#hoisting--declarations) Function declarations hoist their name and the function body.

  ```javascript
  function example() {
    superPower(); // => Flying

    function superPower() {
      console.log("Flying");
    }
  }
  ```

<a name="no-use-before-define"></a>

- [14.5](#no-use-before-define) Variables, classes, and functions should be defined before they can be used. eslint: [`no-use-before-define`](https://eslint.org/docs/latest/rules/no-use-before-define)

  > Why? When variables, classes, or functions are declared after being used, it can harm readability since a reader won't know what a thing that's referenced is. It's much clearer for a reader to first encounter the source of a thing (whether imported from another module, or defined in the file) before encountering a use of the thing.

  ```javascript
  // bad

  // Variable a is being used before it is being defined.
  console.log(a); // this will be undefined, since while the declaration is hoisted, the initialization is not
  var a = 10;

  // Function fun is being called before being defined.
  fun();
  function fun() {}

  // Class A is being used before being defined.
  new A(); // ReferenceError: Cannot access 'A' before initialization
  class A {}

  // `let` and `const` are hoisted, but they don't have a default initialization.
  // The variables 'a' and 'b' are in a Temporal Dead Zone where JavaScript
  // knows they exist (declaration is hoisted) but they are not accessible
  // (as they are not yet initialized).

  console.log(a); // ReferenceError: Cannot access 'a' before initialization
  console.log(b); // ReferenceError: Cannot access 'b' before initialization
  let a = 10;
  const b = 5;

  // good

  var a = 10;
  console.log(a); // 10

  function fun() {}
  fun();

  class A {}
  new A();

  let a = 10;
  const b = 5;
  console.log(a); // 10
  console.log(b); // 5
  ```

- For more information refer to [JavaScript Scoping & Hoisting](https://www.adequatelygood.com/2010/2/JavaScript-Scoping-and-Hoisting/) by [Ben Cherry](https://www.adequatelygood.com/).

**[⬆ back to top](#table-of-contents)**

## Comparison Operators & Equality

<a name="comparison--eqeqeq"></a><a name="15.1"></a>

- [15.1](#comparison--eqeqeq) Use `===` and `!==` over `==` and `!=`. eslint: [`eqeqeq`](https://eslint.org/docs/rules/eqeqeq)

<a name="comparison--if"></a><a name="15.2"></a>

- [15.2](#comparison--if) Conditional statements such as the `if` statement evaluate their expression using coercion with the `ToBoolean` abstract method and always follow these simple rules:

  - **Objects** evaluate to **true**
  - **Undefined** evaluates to **false**
  - **Null** evaluates to **false**
  - **Booleans** evaluate to **the value of the boolean**
  - **Numbers** evaluate to **false** if **+0, -0, or NaN**, otherwise **true**
  - **Strings** evaluate to **false** if an empty string `''`, otherwise **true**

  ```javascript
  if ([0] && []) {
    // true
    // an array (even an empty one) is an object, objects will evaluate to true
  }
  ```

<a name="comparison--shortcuts"></a><a name="15.3"></a>

- [15.3](#comparison--shortcuts) Use shortcuts for booleans, but explicit comparisons for strings and numbers.

  ```javascript
  // bad
  if (isValid === true) {
    // ...
  }

  // good
  if (isValid) {
    // ...
  }

  // bad
  if (name) {
    // ...
  }

  // good
  if (name !== "") {
    // ...
  }

  // bad
  if (collection.length) {
    // ...
  }

  // good
  if (collection.length > 0) {
    // ...
  }
  ```

<a name="comparison--moreinfo"></a><a name="15.4"></a>

- [15.4](#comparison--moreinfo) For more information see [Truth, Equality, and JavaScript](https://javascriptweblog.wordpress.com/2011/02/07/truth-equality-and-javascript/#more-2108) by Angus Croll.

<a name="comparison--switch-blocks"></a><a name="15.5"></a>

- [15.5](#comparison--switch-blocks) Use braces to create blocks in `case` and `default` clauses that contain lexical declarations (e.g. `let`, `const`, `function`, and `class`). eslint: [`no-case-declarations`](https://eslint.org/docs/rules/no-case-declarations)

  > Why? Lexical declarations are visible in the entire `switch` block but only get initialized when assigned, which only happens when its `case` is reached. This causes problems when multiple `case` clauses attempt to define the same thing.

  ```javascript
  // bad
  switch (foo) {
    case 1:
      let x = 1;
      break;
    case 2:
      const y = 2;
      break;
    case 3:
      function f() {
        // ...
      }
      break;
    default:
      class C {}
  }

  // good
  switch (foo) {
    case 1: {
      let x = 1;
      break;
    }
    case 2: {
      const y = 2;
      break;
    }
    case 3: {
      function f() {
        // ...
      }
      break;
    }
    case 4:
      bar();
      break;
    default: {
      class C {}
    }
  }
  ```

<a name="comparison--nested-ternaries"></a><a name="15.6"></a>

- [15.6](#comparison--nested-ternaries) Ternaries should not be nested and generally be single line expressions. eslint: [`no-nested-ternary`](https://eslint.org/docs/rules/no-nested-ternary)

  ```javascript
  // bad
  const foo = maybe1 > maybe2 ? "bar" : value1 > value2 ? "baz" : null;

  // split into 2 separated ternary expressions
  const maybeNull = value1 > value2 ? "baz" : null;

  // better
  const foo = maybe1 > maybe2 ? "bar" : maybeNull;

  // best
  const foo = maybe1 > maybe2 ? "bar" : maybeNull;
  ```

<a name="comparison--unneeded-ternary"></a><a name="15.7"></a>

- [15.7](#comparison--unneeded-ternary) Avoid unneeded ternary statements. eslint: [`no-unneeded-ternary`](https://eslint.org/docs/rules/no-unneeded-ternary)

  ```javascript
  // bad
  const foo = a ? a : b;
  const bar = c ? true : false;
  const baz = c ? false : true;
  const quux = a != null ? a : b;

  // good
  const foo = a || b;
  const bar = !!c;
  const baz = !c;
  const quux = a ?? b;
  ```

<a name="comparison--no-mixed-operators"></a>

- [15.8](#comparison--no-mixed-operators) When mixing operators, enclose them in parentheses. The only exception is the standard arithmetic operators: `+`, `-`, and `**` since their precedence is broadly understood. We recommend enclosing `/` and `*` in parentheses because their precedence can be ambiguous when they are mixed.
  eslint: [`no-mixed-operators`](https://eslint.org/docs/rules/no-mixed-operators)

  > Why? This improves readability and clarifies the developer’s intention.

  ```javascript
  // bad
  const foo = (a && b < 0) || c > 0 || d + 1 === 0;

  // bad
  const bar = a ** b - (5 % d);

  // bad
  // one may be confused into thinking (a || b) && c
  if (a || (b && c)) {
    return d;
  }

  // bad
  const bar = a + (b / c) * d;

  // good
  const foo = (a && b < 0) || c > 0 || d + 1 === 0;

  // good
  const bar = a ** b - (5 % d);

  // good
  if (a || (b && c)) {
    return d;
  }

  // good
  const bar = a + (b / c) * d;
  ```

<a name="nullish-coalescing-operator"></a>

- [15.9](#nullish-coalescing-operator) The nullish coalescing operator (`??`) is a logical operator that returns its right-hand side operand when its left-hand side operand is `null` or `undefined`. Otherwise, it returns the left-hand side operand.

  > Why? It provides precision by distinguishing null/undefined from other falsy values, enhancing code clarity and predictability.

  ```javascript
  // bad
  const value = 0 ?? "default";
  // returns 0, not 'default'

  // bad
  const value = "" ?? "default";
  // returns '', not 'default'

  // good
  const value = null ?? "default";
  // returns 'default'

  // good
  const user = {
    name: "John",
    age: null,
  };
  const age = user.age ?? 18;
  // returns 18
  ```

**[⬆ back to top](#table-of-contents)**

## Blocks

<a name="blocks--braces"></a><a name="16.1"></a>

- [16.1](#blocks--braces) Use braces with all multiline blocks. eslint: [`nonblock-statement-body-position`](https://eslint.org/docs/rules/nonblock-statement-body-position)

  ```javascript
  // bad
  if (test) return false;

  // good
  if (test) return false;

  // good
  if (test) {
    return false;
  }

  // bad
  function foo() {
    return false;
  }

  // good
  function bar() {
    return false;
  }
  ```

<a name="blocks--cuddled-elses"></a><a name="16.2"></a>

- [16.2](#blocks--cuddled-elses) If you’re using multiline blocks with `if` and `else`, put `else` on the same line as your `if` block’s closing brace. eslint: [`brace-style`](https://eslint.org/docs/rules/brace-style)

  ```javascript
  // bad
  if (test) {
    thing1();
    thing2();
  } else {
    thing3();
  }

  // good
  if (test) {
    thing1();
    thing2();
  } else {
    thing3();
  }
  ```

<a name="blocks--no-else-return"></a><a name="16.3"></a>

- [16.3](#blocks--no-else-return) If an `if` block always executes a `return` statement, the subsequent `else` block is unnecessary. A `return` in an `else if` block following an `if` block that contains a `return` can be separated into multiple `if` blocks. eslint: [`no-else-return`](https://eslint.org/docs/rules/no-else-return)

  ```javascript
  // bad
  function foo() {
    if (x) {
      return x;
    } else {
      return y;
    }
  }

  // bad
  function cats() {
    if (x) {
      return x;
    } else if (y) {
      return y;
    }
  }

  // bad
  function dogs() {
    if (x) {
      return x;
    } else {
      if (y) {
        return y;
      }
    }
  }

  // good
  function foo() {
    if (x) {
      return x;
    }

    return y;
  }

  // good
  function cats() {
    if (x) {
      return x;
    }

    if (y) {
      return y;
    }
  }

  // good
  function dogs(x) {
    if (x) {
      if (z) {
        return y;
      }
    } else {
      return z;
    }
  }
  ```

**[⬆ back to top](#table-of-contents)**

## Control Statements

<a name="control-statements"></a>

- [17.1](#control-statements) In case your control statement (`if`, `while` etc.) gets too long or exceeds the maximum line length, each (grouped) condition could be put into a new line. The logical operator should begin the line.

  > Why? Requiring operators at the beginning of the line keeps the operators aligned and follows a pattern similar to method chaining. This also improves readability by making it easier to visually follow complex logic.

  ```javascript
  // bad
  if (
    (foo === 123 || bar === "abc") &&
    doesItLookGoodWhenItBecomesThatLong() &&
    isThisReallyHappening()
  ) {
    thing1();
  }

  // bad
  if (foo === 123 && bar === "abc") {
    thing1();
  }

  // bad
  if (foo === 123 && bar === "abc") {
    thing1();
  }

  // bad
  if (foo === 123 && bar === "abc") {
    thing1();
  }

  // good
  if (foo === 123 && bar === "abc") {
    thing1();
  }

  // good
  if (
    (foo === 123 || bar === "abc") &&
    doesItLookGoodWhenItBecomesThatLong() &&
    isThisReallyHappening()
  ) {
    thing1();
  }

  // good
  if (foo === 123 && bar === "abc") {
    thing1();
  }
  ```

<a name="control-statement--value-selection"></a><a name="control-statements--value-selection"></a>

- [17.2](#control-statements--value-selection) Don't use selection operators in place of control statements.

  ```javascript
  // bad
  !isRunning && startRunning();

  // good
  if (!isRunning) {
    startRunning();
  }
  ```

**[⬆ back to top](#table-of-contents)**

## Comments

<a name="comments--multiline"></a><a name="17.1"></a>

- [18.1](#comments--multiline) Use `/** ... */` for multiline comments.

  ```javascript
  // bad
  // make() returns a new element
  // based on the passed in tag name
  //
  // @param {String} tag
  // @return {Element} element
  function make(tag) {
    // ...

    return element;
  }

  // good
  /**
   * make() returns a new element
   * based on the passed-in tag name
   */
  function make(tag) {
    // ...

    return element;
  }
  ```

<a name="comments--singleline"></a><a name="17.2"></a>

- [18.2](#comments--singleline) Use `//` for single line comments. Place single line comments on a newline above the subject of the comment. Put an empty line before the comment unless it’s on the first line of a block.

  ```javascript
  // bad
  const active = true; // is current tab

  // good
  // is current tab
  const active = true;

  // bad
  function getType() {
    console.log("fetching type...");
    // set the default type to 'no type'
    const type = this.type || "no type";

    return type;
  }

  // good
  function getType() {
    console.log("fetching type...");

    // set the default type to 'no type'
    const type = this.type || "no type";

    return type;
  }

  // also good
  function getType() {
    // set the default type to 'no type'
    const type = this.type || "no type";

    return type;
  }
  ```

<a name="comments--spaces"></a>

- [18.3](#comments--spaces) Start all comments with a space to make it easier to read. eslint: [`spaced-comment`](https://eslint.org/docs/rules/spaced-comment)

  ```javascript
  // bad
  //is current tab
  const active = true;

  // good
  // is current tab
  const active = true;

  // bad
  /**
   *make() returns a new element
   *based on the passed-in tag name
   */
  function make(tag) {
    // ...

    return element;
  }

  // good
  /**
   * make() returns a new element
   * based on the passed-in tag name
   */
  function make(tag) {
    // ...

    return element;
  }
  ```

<a name="comments--actionitems"></a><a name="17.3"></a>

- [18.4](#comments--actionitems) Prefixing your comments with `FIXME` or `TODO` helps other developers quickly understand if you’re pointing out a problem that needs to be revisited, or if you’re suggesting a solution to the problem that needs to be implemented. These are different than regular comments because they are actionable. The actions are `FIXME: -- need to figure this out` or `TODO: -- need to implement`.

<a name="comments--fixme"></a><a name="17.4"></a>

- [18.5](#comments--fixme) Use `// FIXME:` to annotate problems.

  ```javascript
  class Calculator extends Abacus {
    constructor() {
      super();

      // FIXME: shouldn’t use a global here
      total = 0;
    }
  }
  ```

<a name="comments--todo"></a><a name="17.5"></a>

- [18.6](#comments--todo) Use `// TODO:` to annotate solutions to problems.

  ```javascript
  class Calculator extends Abacus {
    constructor() {
      super();

      // TODO: total should be configurable by an options param
      this.total = 0;
    }
  }
  ```

**[⬆ back to top](#table-of-contents)**

## Whitespace

<a name="whitespace--spaces"></a><a name="18.1"></a>

- [19.1](#whitespace--spaces) Use soft tabs (space character) set to 2 spaces. eslint: [`indent`](https://eslint.org/docs/rules/indent)

  ```javascript
  // bad
  function foo() {
  ∙∙∙∙let name;
  }

  // bad
  function bar() {
  ∙let name;
  }

  // good
  function baz() {
  ∙∙let name;
  }
  ```

<a name="whitespace--before-blocks"></a><a name="18.2"></a>

- [19.2](#whitespace--before-blocks) Place 1 space before the leading brace. eslint: [`space-before-blocks`](https://eslint.org/docs/rules/space-before-blocks)

  ```javascript
  // bad
  function test() {
    console.log("test");
  }

  // good
  function test() {
    console.log("test");
  }

  // bad
  dog.set("attr", {
    age: "1 year",
    breed: "Bernese Mountain Dog",
  });

  // good
  dog.set("attr", {
    age: "1 year",
    breed: "Bernese Mountain Dog",
  });
  ```

<a name="whitespace--around-keywords"></a><a name="18.3"></a>

- [19.3](#whitespace--around-keywords) Place 1 space before the opening parenthesis in control statements (`if`, `while` etc.). Place no space between the argument list and the function name in function calls and declarations. eslint: [`keyword-spacing`](https://eslint.org/docs/rules/keyword-spacing)

  ```javascript
  // bad
  if (isJedi) {
    fight();
  }

  // good
  if (isJedi) {
    fight();
  }

  // bad
  function fight() {
    console.log("Swooosh!");
  }

  // good
  function fight() {
    console.log("Swooosh!");
  }
  ```

<a name="whitespace--infix-ops"></a><a name="18.4"></a>

- [19.4](#whitespace--infix-ops) Set off operators with spaces. eslint: [`space-infix-ops`](https://eslint.org/docs/rules/space-infix-ops)

  ```javascript
  // bad
  const x = y + 5;

  // good
  const x = y + 5;
  ```

<a name="whitespace--newline-at-end"></a><a name="18.5"></a>

- [19.5](#whitespace--newline-at-end) End files with a single newline character. eslint: [`eol-last`](https://eslint.org/docs/rules/eol-last)

  ```javascript
  // bad
  import { es6 } from "./AirbnbStyleGuide";
  // ...
  export default es6;
  ```

  ```javascript
  // bad
  import { es6 } from './AirbnbStyleGuide';
    // ...
  export default es6;↵
  ↵
  ```

  ```javascript
  // good
  import { es6 } from './AirbnbStyleGuide';
    // ...
  export default es6;↵
  ```

<a name="whitespace--chains"></a><a name="18.6"></a>

- [19.6](#whitespace--chains) Use indentation when making long method chains (more than 2 method chains). Use a leading dot, which
  emphasizes that the line is a method call, not a new statement. eslint: [`newline-per-chained-call`](https://eslint.org/docs/rules/newline-per-chained-call) [`no-whitespace-before-property`](https://eslint.org/docs/rules/no-whitespace-before-property)

  ```javascript
  // bad
  $("#items").find(".selected").highlight().end().find(".open").updateCount();

  // bad
  $("#items").find(".selected").highlight().end().find(".open").updateCount();

  // good
  $("#items").find(".selected").highlight().end().find(".open").updateCount();

  // bad
  const leds = stage
    .selectAll(".led")
    .data(data)
    .enter()
    .append("svg:svg")
    .classed("led", true)
    .attr("width", (radius + margin) * 2)
    .append("svg:g")
    .attr("transform", `translate(${radius + margin}, ${radius + margin})`)
    .call(tron.led);

  // good
  const leds = stage
    .selectAll(".led")
    .data(data)
    .enter()
    .append("svg:svg")
    .classed("led", true)
    .attr("width", (radius + margin) * 2)
    .append("svg:g")
    .attr("transform", `translate(${radius + margin}, ${radius + margin})`)
    .call(tron.led);

  // good
  const leds = stage.selectAll(".led").data(data);
  const svg = leds.enter().append("svg:svg");
  svg.classed("led", true).attr("width", (radius + margin) * 2);
  const g = svg.append("svg:g");
  g.attr("transform", `translate(${radius + margin}, ${radius + margin})`).call(
    tron.led
  );
  ```

<a name="whitespace--after-blocks"></a><a name="18.7"></a>

- [19.7](#whitespace--after-blocks) Leave a blank line after blocks and before the next statement.

  ```javascript
  // bad
  if (foo) {
    return bar;
  }
  return baz;

  // good
  if (foo) {
    return bar;
  }

  return baz;

  // bad
  const obj = {
    foo() {},
    bar() {},
  };
  return obj;

  // good
  const obj = {
    foo() {},

    bar() {},
  };

  return obj;

  // bad
  const arr = [function foo() {}, function bar() {}];
  return arr;

  // good
  const arr = [function foo() {}, function bar() {}];

  return arr;
  ```

<a name="whitespace--padded-blocks"></a><a name="18.8"></a>

- [19.8](#whitespace--padded-blocks) Do not pad your blocks with blank lines. eslint: [`padded-blocks`](https://eslint.org/docs/rules/padded-blocks)

  ```javascript
  // bad
  function bar() {
    console.log(foo);
  }

  // bad
  if (baz) {
    console.log(quux);
  } else {
    console.log(foo);
  }

  // bad
  class Foo {
    constructor(bar) {
      this.bar = bar;
    }
  }

  // good
  function bar() {
    console.log(foo);
  }

  // good
  if (baz) {
    console.log(quux);
  } else {
    console.log(foo);
  }
  ```

<a name="whitespace--no-multiple-blanks"></a>

- [19.9](#whitespace--no-multiple-blanks) Do not use multiple blank lines to pad your code. eslint: [`no-multiple-empty-lines`](https://eslint.org/docs/rules/no-multiple-empty-lines)

  <!-- markdownlint-disable MD012 -->

  ```javascript
  // bad
  class Person {
    constructor(fullName, email, birthday) {
      this.fullName = fullName;

      this.email = email;

      this.setAge(birthday);
    }

    setAge(birthday) {
      const today = new Date();

      const age = this.getAge(today, birthday);

      this.age = age;
    }

    getAge(today, birthday) {
      // ..
    }
  }

  // good
  class Person {
    constructor(fullName, email, birthday) {
      this.fullName = fullName;
      this.email = email;
      this.setAge(birthday);
    }

    setAge(birthday) {
      const today = new Date();
      const age = getAge(today, birthday);
      this.age = age;
    }

    getAge(today, birthday) {
      // ..
    }
  }
  ```

<a name="whitespace--in-parens"></a><a name="18.9"></a>

- [19.10](#whitespace--in-parens) Do not add spaces inside parentheses. eslint: [`space-in-parens`](https://eslint.org/docs/rules/space-in-parens)

  ```javascript
  // bad
  function bar(foo) {
    return foo;
  }

  // good
  function bar(foo) {
    return foo;
  }

  // bad
  if (foo) {
    console.log(foo);
  }

  // good
  if (foo) {
    console.log(foo);
  }
  ```

<a name="whitespace--in-brackets"></a><a name="18.10"></a>

- [19.11](#whitespace--in-brackets) Do not add spaces inside brackets. eslint: [`array-bracket-spacing`](https://eslint.org/docs/rules/array-bracket-spacing)

  ```javascript
  // bad
  const foo = [1, 2, 3];
  console.log(foo[0]);

  // good
  const foo = [1, 2, 3];
  console.log(foo[0]);
  ```

<a name="whitespace--in-braces"></a><a name="18.11"></a>

- [19.12](#whitespace--in-braces) Add spaces inside curly braces. eslint: [`object-curly-spacing`](https://eslint.org/docs/rules/object-curly-spacing)

  ```javascript
  // bad
  const foo = { clark: "kent" };

  // good
  const foo = { clark: "kent" };
  ```

<a name="whitespace--max-len"></a><a name="18.12"></a>

- [19.13](#whitespace--max-len) Avoid having lines of code that are longer than 100 characters (including whitespace). Note: per [above](#strings--line-length), long strings are exempt from this rule, and should not be broken up. eslint: [`max-len`](https://eslint.org/docs/rules/max-len)

  > Why? This ensures readability and maintainability.

  ```javascript
  // bad
  const foo =
    jsonData &&
    jsonData.foo &&
    jsonData.foo.bar &&
    jsonData.foo.bar.baz &&
    jsonData.foo.bar.baz.quux &&
    jsonData.foo.bar.baz.quux.xyzzy;

  // bad
  $.ajax({ method: "POST", url: "https://airbnb.com/", data: { name: "John" } })
    .done(() => console.log("Congratulations!"))
    .fail(() => console.log("You have failed this city."));

  // good
  const foo =
    jsonData &&
    jsonData.foo &&
    jsonData.foo.bar &&
    jsonData.foo.bar.baz &&
    jsonData.foo.bar.baz.quux &&
    jsonData.foo.bar.baz.quux.xyzzy;

  // better
  const foo = jsonData?.foo?.bar?.baz?.quux?.xyzzy;

  // good
  $.ajax({
    method: "POST",
    url: "https://airbnb.com/",
    data: { name: "John" },
  })
    .done(() => console.log("Congratulations!"))
    .fail(() => console.log("You have failed this city."));
  ```

<a name="whitespace--block-spacing"></a>

- [19.14](#whitespace--block-spacing) Require consistent spacing inside an open block token and the next token on the same line. This rule also enforces consistent spacing inside a close block token and previous token on the same line. eslint: [`block-spacing`](https://eslint.org/docs/rules/block-spacing)

  ```javascript
  // bad
  function foo() {
    return true;
  }
  if (foo) {
    bar = 0;
  }

  // good
  function foo() {
    return true;
  }
  if (foo) {
    bar = 0;
  }
  ```

<a name="whitespace--comma-spacing"></a>

- [19.15](#whitespace--comma-spacing) Avoid spaces before commas and require a space after commas. eslint: [`comma-spacing`](https://eslint.org/docs/rules/comma-spacing)

  ```javascript
  // bad
  const foo = 1,
    bar = 2;
  const arr = [1, 2];

  // good
  const foo = 1,
    bar = 2;
  const arr = [1, 2];
  ```

<a name="whitespace--computed-property-spacing"></a>

- [19.16](#whitespace--computed-property-spacing) Enforce spacing inside of computed property brackets. eslint: [`computed-property-spacing`](https://eslint.org/docs/rules/computed-property-spacing)

  ```javascript
  // bad
  obj[foo];
  obj["foo"];
  const x = { [b]: a };
  obj[foo[bar]];

  // good
  obj[foo];
  obj["foo"];
  const x = { [b]: a };
  obj[foo[bar]];
  ```

<a name="whitespace--func-call-spacing"></a>

- [19.17](#whitespace--func-call-spacing) Avoid spaces between functions and their invocations. eslint: [`func-call-spacing`](https://eslint.org/docs/rules/func-call-spacing)

  ```javascript
  // bad
  func();

  func();

  // good
  func();
  ```

<a name="whitespace--key-spacing"></a>

- [19.18](#whitespace--key-spacing) Enforce spacing between keys and values in object literal properties. eslint: [`key-spacing`](https://eslint.org/docs/rules/key-spacing)

  ```javascript
  // bad
  const obj = { foo: 42 };
  const obj2 = { foo: 42 };

  // good
  const obj = { foo: 42 };
  ```

<a name="whitespace--no-trailing-spaces"></a>

- [19.19](#whitespace--no-trailing-spaces) Avoid trailing spaces at the end of lines. eslint: [`no-trailing-spaces`](https://eslint.org/docs/rules/no-trailing-spaces)

<a name="whitespace--no-multiple-empty-lines"></a>

- [19.20](#whitespace--no-multiple-empty-lines) Avoid multiple empty lines, only allow one newline at the end of files, and avoid a newline at the beginning of files. eslint: [`no-multiple-empty-lines`](https://eslint.org/docs/rules/no-multiple-empty-lines)

  <!-- markdownlint-disable MD012 -->

  ```javascript
  // bad - multiple empty lines
  const x = 1;

  const y = 2;

  // bad - 2+ newlines at end of file
  const x = 1;
  const y = 2;

  // bad - 1+ newline(s) at beginning of file

  const x = 1;
  const y = 2;

  // good
  const x = 1;
  const y = 2;
  ```

**[⬆ back to top](#table-of-contents)**

## Commas

<a name="commas--leading-trailing"></a><a name="19.1"></a>

- [20.1](#commas--leading-trailing) Leading commas: **Nope.** eslint: [`comma-style`](https://eslint.org/docs/rules/comma-style)

  ```javascript
  // bad
  const story = [once, upon, aTime];

  // good
  const story = [once, upon, aTime];

  // bad
  const hero = {
    firstName: "Ada",
    lastName: "Lovelace",
    birthYear: 1815,
    superPower: "computers",
  };

  // good
  const hero = {
    firstName: "Ada",
    lastName: "Lovelace",
    birthYear: 1815,
    superPower: "computers",
  };
  ```

<a name="commas--dangling"></a><a name="19.2"></a>

- [20.2](#commas--dangling) Additional trailing comma: **Yup.** eslint: [`comma-dangle`](https://eslint.org/docs/rules/comma-dangle)

  > Why? This leads to cleaner git diffs. Also, transpilers like Babel will remove the additional trailing comma in the transpiled code which means you don’t have to worry about the [trailing comma problem](https://github.com/airbnb/javascript/blob/es5-deprecated/es5/README.md#commas) in legacy browsers.

  ```diff
  // bad - git diff without trailing comma
  const hero = {
       firstName: 'Florence',
  -    lastName: 'Nightingale'
  +    lastName: 'Nightingale',
  +    inventorOf: ['coxcomb chart', 'modern nursing']
  };

  // good - git diff with trailing comma
  const hero = {
       firstName: 'Florence',
       lastName: 'Nightingale',
  +    inventorOf: ['coxcomb chart', 'modern nursing'],
  };
  ```

  ```javascript
  // bad
  const hero = {
    firstName: "Dana",
    lastName: "Scully",
  };

  const heroes = ["Batman", "Superman"];

  // good
  const hero = {
    firstName: "Dana",
    lastName: "Scully",
  };

  const heroes = ["Batman", "Superman"];

  // bad
  function createHero(firstName, lastName, inventorOf) {
    // does nothing
  }

  // good
  function createHero(firstName, lastName, inventorOf) {
    // does nothing
  }

  // good (note that a comma must not appear after a "rest" element)
  function createHero(firstName, lastName, inventorOf, ...heroArgs) {
    // does nothing
  }

  // bad
  createHero(firstName, lastName, inventorOf);

  // good
  createHero(firstName, lastName, inventorOf);

  // good (note that a comma must not appear after a "rest" element)
  createHero(firstName, lastName, inventorOf, ...heroArgs);
  ```

**[⬆ back to top](#table-of-contents)**

## Semicolons

<a name="semicolons--required"></a><a name="20.1"></a>

- [21.1](#semicolons--required) **Yup.** eslint: [`semi`](https://eslint.org/docs/rules/semi)

  > Why? When JavaScript encounters a line break without a semicolon, it uses a set of rules called [Automatic Semicolon Insertion](https://tc39.github.io/ecma262/#sec-automatic-semicolon-insertion) to determine whether it should regard that line break as the end of a statement, and (as the name implies) place a semicolon into your code before the line break if it thinks so. ASI contains a few eccentric behaviors, though, and your code will break if JavaScript misinterprets your line break. These rules will become more complicated as new features become a part of JavaScript. Explicitly terminating your statements and configuring your linter to catch missing semicolons will help prevent you from encountering issues.

  ```javascript
  // bad - raises exception
  const luke = {};
  const leia = {}[(luke, leia)].forEach((jedi) => (jedi.father = "vader"));

  // bad - raises exception
  const reaction = "No! That’s impossible!"(
    (async function meanwhileOnTheFalcon() {
      // handle `leia`, `lando`, `chewie`, `r2`, `c3p0`
      // ...
    })()
  );

  // bad - returns `undefined` instead of the value on the next line - always happens when `return` is on a line by itself because of ASI!
  function foo() {
    return;
    ("search your feelings, you know it to be foo");
  }

  // good
  const luke = {};
  const leia = {};
  [luke, leia].forEach((jedi) => {
    jedi.father = "vader";
  });

  // good
  const reaction = "No! That’s impossible!";
  (async function meanwhileOnTheFalcon() {
    // handle `leia`, `lando`, `chewie`, `r2`, `c3p0`
    // ...
  })();

  // good
  function foo() {
    return "search your feelings, you know it to be foo";
  }
  ```

  [Read more](https://stackoverflow.com/questions/7365172/semicolon-before-self-invoking-function/7365214#7365214).

**[⬆ back to top](#table-of-contents)**

## Type Casting & Coercion

<a name="coercion--explicit"></a><a name="21.1"></a>

- [22.1](#coercion--explicit) Perform type coercion at the beginning of the statement.

<a name="coercion--strings"></a><a name="21.2"></a>

- [22.2](#coercion--strings) Strings: eslint: [`no-new-wrappers`](https://eslint.org/docs/rules/no-new-wrappers)

  ```javascript
  // => this.reviewScore = 9;

  // bad
  const totalScore = new String(this.reviewScore); // typeof totalScore is "object" not "string"

  // bad
  const totalScore = this.reviewScore + ""; // invokes this.reviewScore.valueOf()

  // bad
  const totalScore = this.reviewScore.toString(); // isn’t guaranteed to return a string

  // good
  const totalScore = String(this.reviewScore);
  ```

<a name="coercion--numbers"></a><a name="21.3"></a>

- [22.3](#coercion--numbers) Numbers: Use `Number` for type casting and `parseInt` always with a radix for parsing strings. eslint: [`radix`](https://eslint.org/docs/rules/radix) [`no-new-wrappers`](https://eslint.org/docs/rules/no-new-wrappers)

  > Why? The `parseInt` function produces an integer value dictated by interpretation of the contents of the string argument according to the specified radix. Leading whitespace in string is ignored. If radix is `undefined` or `0`, it is assumed to be `10` except when the number begins with the character pairs `0x` or `0X`, in which case a radix of 16 is assumed. This differs from ECMAScript 3, which merely discouraged (but allowed) octal interpretation. Many implementations have not adopted this behavior as of 2013. And, because older browsers must be supported, always specify a radix.

  ```javascript
  const inputValue = "4";

  // bad
  const val = new Number(inputValue);

  // bad
  const val = +inputValue;

  // bad
  const val = inputValue >> 0;

  // bad
  const val = parseInt(inputValue);

  // good
  const val = Number(inputValue);

  // good
  const val = parseInt(inputValue, 10);
  ```

<a name="coercion--comment-deviations"></a><a name="21.4"></a>

- [22.4](#coercion--comment-deviations) If for whatever reason you are doing something wild and `parseInt` is your bottleneck and need to use Bitshift for [performance reasons](https://web.archive.org/web/20200414205431/https://jsperf.com/coercion-vs-casting/3), leave a comment explaining why and what you’re doing.

  ```javascript
  // good
  /**
   * parseInt was the reason my code was slow.
   * Bitshifting the String to coerce it to a
   * Number made it a lot faster.
   */
  const val = inputValue >> 0;
  ```

<a name="coercion--bitwise"></a><a name="21.5"></a>

- [22.5](#coercion--bitwise) **Note:** Be careful when using bitshift operations. Numbers are represented as [64-bit values](https://es5.github.io/#x4.3.19), but bitshift operations always return a 32-bit integer ([source](https://es5.github.io/#x11.7)). Bitshift can lead to unexpected behavior for integer values larger than 32 bits. [Discussion](https://github.com/airbnb/javascript/issues/109). Largest signed 32-bit Int is 2,147,483,647:

  ```javascript
  2147483647 >> 0; // => 2147483647
  2147483648 >> 0; // => -2147483648
  2147483649 >> 0; // => -2147483647
  ```

<a name="coercion--booleans"></a><a name="21.6"></a>

- [22.6](#coercion--booleans) Booleans: eslint: [`no-new-wrappers`](https://eslint.org/docs/rules/no-new-wrappers)

  ```javascript
  const age = 0;

  // bad
  const hasAge = new Boolean(age);

  // good
  const hasAge = Boolean(age);

  // best
  const hasAge = !!age;
  ```

**[⬆ back to top](#table-of-contents)**

## Naming Conventions

<a name="naming--descriptive"></a><a name="22.1"></a>

- [23.1](#naming--descriptive) Avoid single letter names. Be descriptive with your naming. eslint: [`id-length`](https://eslint.org/docs/rules/id-length)

  ```javascript
  // bad
  function q() {
    // ...
  }

  // good
  function query() {
    // ...
  }
  ```

<a name="naming--camelCase"></a><a name="22.2"></a>

- [23.2](#naming--camelCase) Use camelCase when naming objects, functions, and instances. eslint: [`camelcase`](https://eslint.org/docs/rules/camelcase)

  ```javascript
  // bad
  const OBJEcttsssss = {};
  const this_is_my_object = {};
  function c() {}

  // good
  const thisIsMyObject = {};
  function thisIsMyFunction() {}
  ```

<a name="naming--PascalCase"></a><a name="22.3"></a>

- [23.3](#naming--PascalCase) Use PascalCase only when naming constructors or classes. eslint: [`new-cap`](https://eslint.org/docs/rules/new-cap)

  ```javascript
  // bad
  function user(options) {
    this.name = options.name;
  }

  const bad = new user({
    name: "nope",
  });

  // good
  class User {
    constructor(options) {
      this.name = options.name;
    }
  }

  const good = new User({
    name: "yup",
  });
  ```

<a name="naming--leading-underscore"></a><a name="22.4"></a>

- [23.4](#naming--leading-underscore) Do not use trailing or leading underscores. eslint: [`no-underscore-dangle`](https://eslint.org/docs/rules/no-underscore-dangle)

  > Why? JavaScript does not have the concept of privacy in terms of properties or methods. Although a leading underscore is a common convention to mean “private”, in fact, these properties are fully public, and as such, are part of your public API contract. This convention might lead developers to wrongly think that a change won’t count as breaking, or that tests aren’t needed. tl;dr: if you want something to be “private”, it must not be observably present.

  ```javascript
  // bad
  this.__firstName__ = "Panda";
  this.firstName_ = "Panda";
  this._firstName = "Panda";

  // good
  this.firstName = "Panda";

  // good, in environments where WeakMaps are available
  // see https://compat-table.github.io/compat-table/es6/#test-WeakMap
  const firstNames = new WeakMap();
  firstNames.set(this, "Panda");
  ```

<a name="naming--self-this"></a><a name="22.5"></a>

- [23.5](#naming--self-this) Don’t save references to `this`. Use arrow functions or [Function#bind](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/bind).

  ```javascript
  // bad
  function foo() {
    const self = this;
    return function () {
      console.log(self);
    };
  }

  // bad
  function foo() {
    const that = this;
    return function () {
      console.log(that);
    };
  }

  // good
  function foo() {
    return () => {
      console.log(this);
    };
  }
  ```

<a name="naming--filename-matches-export"></a><a name="22.6"></a>

- [23.6](#naming--filename-matches-export) A base filename should exactly match the name of its default export.

  ```javascript
  // file 1 contents
  class CheckBox {
    // ...
  }
  export default CheckBox;

  // file 2 contents
  export default function fortyTwo() { return 42; }

  // file 3 contents
  export default function insideDirectory() {}

  // in some other file
  // bad
  import CheckBox from './checkBox'; // PascalCase import/export, camelCase filename
  import FortyTwo from './FortyTwo'; // PascalCase import/filename, camelCase export
  import InsideDirectory from './InsideDirectory'; // PascalCase import/filename, camelCase export

  // bad
  import CheckBox from './check_box'; // PascalCase import/export, snake_case filename
  import forty_two from './forty_two'; // snake_case import/filename, camelCase export
  import inside_directory from './inside_directory'; // snake_case import, camelCase export
  import index from './inside_directory/index'; // requiring the index file explicitly
  import insideDirectory from './insideDirectory/index'; // requiring the index file explicitly

  // good
  import CheckBox from './CheckBox'; // PascalCase export/import/filename
  import fortyTwo from './fortyTwo'; // camelCase export/import/filename
  import insideDirectory from './insideDirectory'; // camelCase export/import/directory name/implicit "index"
  // ^ supports both insideDirectory.js and insideDirectory/index.js
  ```

<a name="naming--camelCase-default-export"></a><a name="22.7"></a>

- [23.7](#naming--camelCase-default-export) Use camelCase when you export-default a function. Your filename should be identical to your function’s name.

  ```javascript
  function makeStyleGuide() {
    // ...
  }

  export default makeStyleGuide;
  ```

<a name="naming--PascalCase-singleton"></a><a name="22.8"></a>

- [23.8](#naming--PascalCase-singleton) Use PascalCase when you export a constructor / class / singleton / function library / bare object.

  ```javascript
  const AirbnbStyleGuide = {
    es6: {},
  };

  export default AirbnbStyleGuide;
  ```

<a name="naming--Acronyms-and-Initialisms"></a>

- [23.9](#naming--Acronyms-and-Initialisms) Acronyms and initialisms should always be all uppercased, or all lowercased.

  > Why? Names are for readability, not to appease a computer algorithm.

  ```javascript
  // bad
  import SmsContainer from "./containers/SmsContainer";

  // bad
  const HttpRequests = [
    // ...
  ];

  // good
  import SMSContainer from "./containers/SMSContainer";

  // good
  const HTTPRequests = [
    // ...
  ];

  // also good
  const httpRequests = [
    // ...
  ];

  // best
  import TextMessageContainer from "./containers/TextMessageContainer";

  // best
  const requests = [
    // ...
  ];
  ```

<a name="naming--uppercase"></a>

- [23.10](#naming--uppercase) You may optionally uppercase a constant only if it (1) is exported, (2) is a `const` (it can not be reassigned), and (3) the programmer can trust it (and its nested properties) to never change.

  > Why? This is an additional tool to assist in situations where the programmer would be unsure if a variable might ever change. UPPERCASE_VARIABLES are letting the programmer know that they can trust the variable (and its properties) not to change.

  - What about all `const` variables? - This is unnecessary, so uppercasing should not be used for constants within a file. It should be used for exported constants however.
  - What about exported objects? - Uppercase at the top level of export (e.g. `EXPORTED_OBJECT.key`) and maintain that all nested properties do not change.

  ```javascript
  // bad
  const PRIVATE_VARIABLE =
    "should not be unnecessarily uppercased within a file";

  // bad
  export const THING_TO_BE_CHANGED = "should obviously not be uppercased";

  // bad
  export let REASSIGNABLE_VARIABLE = "do not use let with uppercase variables";

  // ---

  // allowed but does not supply semantic value
  export const apiKey = "SOMEKEY";

  // better in most cases
  export const API_KEY = "SOMEKEY";

  // ---

  // bad - unnecessarily uppercases key while adding no semantic value
  export const MAPPING = {
    KEY: "value",
  };

  // good
  export const MAPPING = {
    key: "value",
  };
  ```

**[⬆ back to top](#table-of-contents)**

## Accessors

<a name="accessors--not-required"></a><a name="23.1"></a>

- [24.1](#accessors--not-required) Accessor functions for properties are not required.

<a name="accessors--no-getters-setters"></a><a name="23.2"></a>

- [24.2](#accessors--no-getters-setters) Do not use JavaScript getters/setters as they cause unexpected side effects and are harder to test, maintain, and reason about. Instead, if you do make accessor functions, use `getVal()` and `setVal('hello')`.

  ```javascript
  // bad
  class Dragon {
    get age() {
      // ...
    }

    set age(value) {
      // ...
    }
  }

  // good
  class Dragon {
    getAge() {
      // ...
    }

    setAge(value) {
      // ...
    }
  }
  ```

<a name="accessors--boolean-prefix"></a><a name="23.3"></a>

- [24.3](#accessors--boolean-prefix) If the property/method is a `boolean`, use `isVal()` or `hasVal()`.

  ```javascript
  // bad
  if (!dragon.age()) {
    return false;
  }

  // good
  if (!dragon.hasAge()) {
    return false;
  }
  ```

<a name="accessors--consistent"></a><a name="23.4"></a>

- [24.4](#accessors--consistent) It’s okay to create `get()` and `set()` functions, but be consistent.

  ```javascript
  class Jedi {
    constructor(options = {}) {
      const lightsaber = options.lightsaber || "blue";
      this.set("lightsaber", lightsaber);
    }

    set(key, val) {
      this[key] = val;
    }

    get(key) {
      return this[key];
    }
  }
  ```

**[⬆ back to top](#table-of-contents)**

## Loops and Conditional Statements

<a name="loops--initialization"></a><a name="4.1"></a>

- [25.1](#loops--initialization) When loops are required, choose the appropriate one from `for(;;)`, `for...of`, `while`, etc.

  <br />

  - When iterating through all collection elements, avoid using the classical `for(;;)` loop; prefer `for...of` or `forEach()`. Note that if you are using a collection that is not an `Array`, you have to check that `for...of` is actually supported (it requires the variable to be iterable), or that the `forEach()` method is actually present.

  ```javascript
  // Use for...of:
  const dogs = ["Rex", "Lassie"];
  for (const dog of dogs) {
    console.log(dog);
  }

  // Or forEach():
  const dogs = ["Rex", "Lassie"];
  dogs.forEach((dog) => {
    console.log(dog);
  });
  ```

  - Do not use `for(;;)` — not only do you have to add an extra index, `i`, but you also have to track the length of the array. This can be error-prone for beginners.

  ```javascript
  // bad
  const dogs = ["Rex", "Lassie"];
  for (let i = 0; i < dogs.length; i++) {
    console.log(dogs[i]);
  }
  ```

<a name="loops--initializer"></a><a name="4.2"></a>

- [25.2](#loops--initializer) Make sure that you define the initializer properly by using the `const` keyword for `for...of` or `let` for the other loops. Don't omit it.

  ```javascript
  // good
  const cats = ["Athena", "Luna"];
  for (const cat of cats) {
    console.log(cat);
  }

  for (let i = 0; i < 4; i++) {
    result += arr[i];
  }

  // bad
  const cats = ["Athena", "Luna"];
  for (i of cats) {
    console.log(i);
  }
  ```

<a name="loops--foreach"></a><a name="4.3"></a>

- [25.3](#loops--foreach) When you need to access both the value and the index, you can use `.forEach()` instead of `for(;;)`.

  ```javascript
  // good
  const gerbils = ["Zoé", "Chloé"];
  gerbils.forEach((gerbil, i) => {
    console.log(`Gerbil #${i}: ${gerbil}`);
  });

  // bad
  const gerbils = ["Zoé", "Chloé"];
  for (let i = 0; i < gerbils.length; i++) {
    console.log(`Gerbil #${i}: ${gerbils[i]}`);
  }
  ```

<a name="loops--for-in"></a><a name="4.4"></a>

- [25.4](#loops--for-in) **Warning**: Never use `for...in` with arrays and strings.

<a name="loops--alternatives"></a><a name="4.5"></a>

- [25.5](#loops--alternatives) **Note**: Consider not using a `for` loop at all. If you are using an `Array` (or a `String` for some operations), consider using more semantic iteration methods instead, like `map()`, `every()`, `findIndex()`, `find()`, `includes()`, and many more.

<a name="loops--braces"></a><a name="4.6"></a>

- [25.6](#loops--braces) Use braces with control flow statements and loops. This prevents forgetting to add the braces when adding more statements.

  ```javascript
  // good
  for (const car of storedCars) {
    car.paint("red");
  }

  // bad
  for (const car of storedCars) car.paint("red");
  ```

<a name="conditional-statements"></a><a name="4.7"></a>

- [25.7](#conditional-statements) If the `if` statement ends with a `return`, do not add an `else` statement.

  ```javascript
  // good
  if (test) {
    // Perform something if test is true
    // …
    return;
  }

  // Perform something if test is false
  // …

  // bad
  if (test) {
    // Perform something if test is true
    // …
    return;
  } else {
    // Perform something if test is false
    // …
  }
  ```

<a name="switch-statements"></a><a name="4.8"></a>

- [25.8](#switch-statements) **Switch statements** can be a little tricky.

  - Don't add a `break` statement after a `return` statement in a specific case.

  ```javascript
  // good
  switch (species) {
    case "chicken":
      return farm.shed;
    case "horse":
      return corral.entry;
    default:
      return "";
  }

  // bad
  switch (species) {
    case "chicken":
      return farm.shed;
      break;
    case "horse":
      return corral.entry;
      break;
    default:
      return "";
  }
  ```

  - Use `default` as the last case, and don't end it with a `break` statement. If you need to do it differently, add a comment explaining why.
  - Remember that when you declare a local variable for a case, you need to use braces to define a scope:

  ```javascript
  switch (fruits) {
    case "Orange": {
      const slice = fruit.slice();
      eat(slice);
      break;
    }
    case "Apple": {
      const core = fruit.extractCore();
      recycle(core);
      break;
    }
  }
  ```

<a name="error-handling"></a><a name="4.9"></a>

- [25.9](#error-handling) **Error handling**: If certain states of your program throw uncaught errors, they will halt execution and potentially reduce the usefulness of the example. You should, therefore, catch errors using a `try...catch` block.

  ```javascript
  try {
    console.log(getResult());
  } catch (e) {
    console.error(e);
  }
  ```

  - When you don't need the parameter of the `catch` statement, omit it:

  ```javascript
  try {
    console.log(getResult());
  } catch {
    console.error("An error happened!");
  }
  ```

**[⬆ back to top](#table-of-contents)**

Here's the formatted JavaScript code formatting style guide based on the information provided:

---

## Formating

[26.1]**Braces**
Braces are used for all control structures, including `if`, `else`, `for`, `do`, `while`, and others. The opening brace appears at the end of the control statement line, and the closing brace appears on its own line aligned with the start of the control statement.

```javascript
// Disallowed: Single line if statement without braces
if (someVeryLongCondition()) doSomething();

// Allowed: Simple if statement without else
if (shortCondition()) foo();
```

[26.2] **Block indentation: +2 spaces**
Each new block or block-like construct increases the indent by two spaces. Braces follow the Kernighan and Ritchie style (Egyptian brackets) for nonempty blocks.

```javascript
class InnerClass {
  constructor() {}

  method(foo) {
    if (condition(foo)) {
      try {
        something();
      } catch (err) {
        recover();
      }
    }
  }
}
```

[26.3] **Statements**
Each statement is on its own line and terminated with a semicolon.

```javascript
const a = 1;
let b = a;
b = 9;
console.log(a, b); // => 1, 9;
```

[26.4] **Column limit: 80**
Lines should not exceed 80 characters, and line-wrapping should be used where necessary.

```javascript
currentEstimate = calc(currentEstimate + x * currentEstimate) / 2.0;
```

[26.5] **Line-wrapping**
Line-wrapping is used to avoid exceeding the column limit, breaking at higher syntactic levels when possible.

```javascript
currentEstimate = calc(currentEstimate + x * currentEstimate) / 2.0;
```

[26.6] **Grouping parentheses**
Optional grouping parentheses should be used to clarify intent.

```javascript
someFunction(obviousParam, /* shouldRender= */ true, /* name= */ "hello");
```

## Basic Rules

- Only include one React component per file.
  - However, multiple [Stateless, or Pure, Components](https://facebook.github.io/react/docs/reusable-components.html#stateless-functions) are allowed per file. eslint: [`react/no-multi-comp`](https://github.com/jsx-eslint/eslint-plugin-react/blob/master/docs/rules/no-multi-comp.md#ignorestateless).
- Always use JSX syntax.
- Do not use `React.createElement` unless you’re initializing the app from a file that is not JSX.
- [`react/forbid-prop-types`](https://github.com/jsx-eslint/eslint-plugin-react/blob/master/docs/rules/forbid-prop-types.md) will allow `arrays` and `objects` only if it is explicitly noted what `array` and `object` contains, using `arrayOf`, `objectOf`, or `shape`.

## Class vs `React.createClass` vs stateless

- If you have internal state and/or refs, prefer `class extends React.Component` over `React.createClass`. eslint: [`react/prefer-es6-class`](https://github.com/jsx-eslint/eslint-plugin-react/blob/master/docs/rules/prefer-es6-class.md) [`react/prefer-stateless-function`](https://github.com/jsx-eslint/eslint-plugin-react/blob/master/docs/rules/prefer-stateless-function.md)

  ```jsx
  // bad
  const Listing = React.createClass({
    // ...
    render() {
      return <div>{this.state.hello}</div>;
    },
  });

  // good
  class Listing extends React.Component {
    // ...
    render() {
      return <div>{this.state.hello}</div>;
    }
  }
  ```

  And if you don’t have state or refs, prefer normal functions (not arrow functions) over classes:

  ```jsx
  // bad
  class Listing extends React.Component {
    render() {
      return <div>{this.props.hello}</div>;
    }
  }

  // bad (relying on function name inference is discouraged)
  const Listing = ({ hello }) => <div>{hello}</div>;

  // good
  function Listing({ hello }) {
    return <div>{hello}</div>;
  }
  ```

## Mixins

- [Do not use mixins](https://facebook.github.io/react/blog/2016/07/13/mixins-considered-harmful.html).

> Why? Mixins introduce implicit dependencies, cause name clashes, and cause snowballing complexity. Most use cases for mixins can be accomplished in better ways via components, higher-order components, or utility modules.

## Naming

- **Extensions**: Use `.jsx` extension for React components. eslint: [`react/jsx-filename-extension`](https://github.com/jsx-eslint/eslint-plugin-react/blob/master/docs/rules/jsx-filename-extension.md)
- **Filename**: Use PascalCase for filenames. E.g., `ReservationCard.jsx`.
- **Reference Naming**: Use PascalCase for React components and camelCase for their instances. eslint: [`react/jsx-pascal-case`](https://github.com/jsx-eslint/eslint-plugin-react/blob/master/docs/rules/jsx-pascal-case.md)

  ```jsx
  // bad
  import reservationCard from "./ReservationCard";

  // good
  import ReservationCard from "./ReservationCard";

  // bad
  const ReservationItem = <ReservationCard />;

  // good
  const reservationItem = <ReservationCard />;
  ```

- **Component Naming**: Use the filename as the component name. For example, `ReservationCard.jsx` should have a reference name of `ReservationCard`. However, for root components of a directory, use `index.jsx` as the filename and use the directory name as the component name:

  ```jsx
  // bad
  import Footer from "./Footer/Footer";

  // bad
  import Footer from "./Footer/index";

  // good
  import Footer from "./Footer";
  ```

- **Higher-order Component Naming**: Use a composite of the higher-order component’s name and the passed-in component’s name as the `displayName` on the generated component. For example, the higher-order component `withFoo()`, when passed a component `Bar` should produce a component with a `displayName` of `withFoo(Bar)`.

  > Why? A component’s `displayName` may be used by developer tools or in error messages, and having a value that clearly expresses this relationship helps people understand what is happening.

  ```jsx
  // bad
  export default function withFoo(WrappedComponent) {
    return function WithFoo(props) {
      return <WrappedComponent {...props} foo />;
    }
  }

  // good
  export default function withFoo(WrappedComponent) {
    function WithFoo(props) {
      return <WrappedComponent {...props} foo />;
    }

    const wrappedComponentName = WrappedComponent.displayName
      || WrappedComponent.name
      || 'Component';

    WithFoo.displayName = `withFoo(${wrappedComponentName})`;
    return WithFoo;
  }
  ```

- **Props Naming**: Avoid using DOM component prop names for different purposes.

  > Why? People expect props like `style` and `className` to mean one specific thing. Varying this API for a subset of your app makes the code less readable and less maintainable, and may cause bugs.

  ```jsx
  // bad
  <MyComponent style="fancy" />

  // bad
  <MyComponent className="fancy" />

  // good
  <MyComponent variant="fancy" />
  ```

## Declaration

- Do not use `displayName` for naming components. Instead, name the component by reference.

  ```jsx
  // bad
  export default React.createClass({
    displayName: 'ReservationCard',
    // stuff goes here
  });

  // good
  export default class ReservationCard extends React.Component {
  }
  ```

## Alignment

- Follow these alignment styles for JSX syntax. eslint: [`react/jsx-closing-bracket-location`](https://github.com/jsx-eslint/eslint-plugin-react/blob/master/docs/rules/jsx-closing-bracket-location.md) [`react/jsx-closing-tag-location`](https://github.com/jsx-eslint/eslint-plugin-react/blob/master/docs/rules/jsx-closing-tag-location.md)

  ```jsx
  // bad
  <Foo superLongParam="bar"
       anotherSuperLongParam="baz" />

  // good
  <Foo
    superLongParam="bar"
    anotherSuperLongParam="baz"
  />

  // if props fit in one line then keep it on the same line
  <Foo bar="bar" />

  // children get indented normally
  <Foo
    superLongParam="bar"
    anotherSuperLongParam="baz"
  >
    <Quux />
  </Foo>

  // bad
  {showButton &&
    <Button />
  }

  // bad
  {
    showButton &&
      <Button />
  }

  // good
  {showButton && (
    <Button />
  )}

  // good
  {showButton && <Button />}

  // good
  {someReallyLongConditional
    && anotherLongConditional
    && (
      <Foo
        superLongParam="bar"
        anotherSuperLongParam="baz"
      />
    )
  }

  // good
  {someConditional ? (
    <Foo />
  ) : (
    <Foo
      superLongParam="bar"
      anotherSuperLongParam="baz"
    />
  )}
  ```

## Quotes

- Always use double quotes (`"`) for JSX attributes, but single quotes (`'`) for all other JS. eslint: [`jsx-quotes`](https://eslint.org/docs/rules/jsx-quotes)

  > Why? Regular HTML attributes also typically use double quotes instead of single, so JSX attributes mirror this convention.

  ```jsx
  // bad
  <Foo bar='bar' />

  // good
  <Foo bar="bar" />

  // bad
  <Foo style={{ left: "20px" }} />

  // good
  <Foo style={{ left: '20px' }} />
  ```

## Spacing

- Always include a single space in your self-closing tag. eslint: [`no-multi-spaces`](https://eslint.org/docs/rules/no-multi-spaces), [`react/jsx-tag-spacing`](https://github.com/jsx-eslint/eslint-plugin-react/blob/master/docs/rules/jsx-tag-spacing.md)

  ```jsx
  // bad
  <Foo/>

  // very bad
  <Foo                 />

  // bad
  <Foo
   />

  // good
  <Foo />
  ```

- Do not pad JSX curly braces with spaces. eslint: [`react/jsx-curly-spacing`](https://github.com/jsx-eslint/eslint-plugin-react/blob/master/docs/rules/jsx-curly-spacing.md)

  ```jsx
  // bad
  <Foo bar={ baz } />

  // good
  <Foo bar={baz} />
  ```

## Props

- Always use camelCase for prop names, or PascalCase if the prop value is a React component.

  ```jsx
  // bad
  <Foo
    UserName="hello"
    phone_number={12345678}
  />

  // good
  <Foo
    userName="hello"
    phoneNumber={12345678}
    Component={SomeComponent}
  />
  ```

- Omit the value of the prop when it is explicitly `true`. eslint: [`react/jsx-boolean-value`](https://github.com/jsx-eslint/eslint-plugin-react/blob/master/docs/rules/jsx-boolean-value.md)

  ```jsx
  // bad
  <Foo
    hidden={true}
  />

  // good
  <Foo
    hidden
  />

  // good
  <Foo hidden />
  ```

- Always include an `alt` prop on `<img>` tags. If the image is presentational, `alt` can be an empty string or the `<img>` must have `role="presentation"`. eslint: [`jsx-a11y/alt-text`](https://github.com/jsx-eslint/eslint-plugin-jsx-a11y/blob/master/docs/rules/alt-text.md)

  ```jsx
  // bad
  <img src="hello.jpg" />

  // good
  <img src="hello.jpg" alt="Me waving hello" />

  // good
  <img src="hello.jpg" alt="" />

  // good
  <img src="hello.jpg" role="presentation" />
  ```

- Do not use words like "image", "photo", or "picture" in `<img>` `alt` props. eslint: [`jsx-a11y/img-redundant-alt`](https://github.com/jsx-eslint/eslint-plugin-jsx-a11y/blob/master/docs/rules/img-redundant-alt.md)

  > Why? Screenreaders already announce `img` elements as images, so there is no need to include this information in the alt text.

  ```jsx
  // bad
  <img src="hello.jpg" alt="Picture of me waving hello" />

  // good
  <img src="hello.jpg" alt="Me waving hello" />
  ```

- Use only valid, non-abstract [ARIA roles](https://www.w3.org/TR/wai-aria/#usage_intro). eslint: [`jsx-a11y/aria-role`](https://github.com/jsx-eslint/eslint-plugin-jsx-a11y/blob/master/docs/rules/aria-role.md)

  ```jsx
  // bad - not an ARIA role
  <div role="datepicker" />

  // bad - abstract ARIA role
  <div role="range" />

  // good
  <div role="button" />
  ```

- Do not use `accessKey` on elements. eslint: [`jsx-a11y/no-access-key`](https://github.com/jsx-eslint/eslint-plugin-jsx-a11y/blob/master/docs/rules/no-access-key.md)

> Why? Inconsistencies between keyboard shortcuts and keyboard commands used by people using screenreaders and keyboards complicate accessibility.

```jsx
// bad
<div accessKey="h" />

// good
<div />
```

- Avoid using an array index as `key` prop, prefer a stable ID. eslint: [`react/no-array-index-key`](https://github.com/jsx-eslint/eslint-plugin-react/blob/master/docs/rules/no-array-index-key.md)

> Why? Not using a stable ID [is an anti-pattern](https://medium.com/@robinpokorny/index-as-a-key-is-an-anti-pattern-e0349aece318) because it can negatively impact performance and cause issues with component state.

We don’t recommend using indexes for keys if the order of items may change.

```jsx
// bad
{
  todos.map((todo, index) => <Todo {...todo} key={index} />);
}

// good
{
  todos.map((todo) => <Todo {...todo} key={todo.id} />);
}
```

- Always define explicit defaultProps for all non-required props.

> Why? propTypes are a form of documentation, and providing defaultProps means the reader of your code doesn’t have to assume as much. In addition, it can mean that your code can omit certain type checks.

```jsx
// bad
function SFC({ foo, bar, children }) {
  return (
    <div>
      {foo}
      {bar}
      {children}
    </div>
  );
}
SFC.propTypes = {
  foo: PropTypes.number.isRequired,
  bar: PropTypes.string,
  children: PropTypes.node,
};

// good
function SFC({ foo, bar, children }) {
  return (
    <div>
      {foo}
      {bar}
      {children}
    </div>
  );
}
SFC.propTypes = {
  foo: PropTypes.number.isRequired,
  bar: PropTypes.string,
  children: PropTypes.node,
};
SFC.defaultProps = {
  bar: "",
  children: null,
};
```

- Use spread props sparingly.
  > Why? Otherwise you’re more likely to pass unnecessary props down to components. And for React v15.6.1 and older, you could [pass invalid HTML attributes to the DOM](https://reactjs.org/blog/2017/09/08/dom-attributes-in-react-16.html).

Exceptions:

- HOCs that proxy down props and hoist propTypes

```jsx
function HOC(WrappedComponent) {
  return class Proxy extends React.Component {
    Proxy.propTypes = {
      text: PropTypes.string,
      isLoading: PropTypes.bool
    };

    render() {
      return <WrappedComponent {...this.props} />
    }
  }
}
```

- Spreading objects with known, explicit props. This can be particularly useful when testing React components with Mocha’s beforeEach construct.

```jsx
export default function Foo {
  const props = {
    text: '',
    isPublished: false
  }

  return (<div {...props} />);
}
```

Notes for use:
Filter out unnecessary props when possible. Also, use [prop-types-exact](https://www.npmjs.com/package/prop-types-exact) to help prevent bugs.

```jsx
// bad
render() {
  const { irrelevantProp, ...relevantProps } = this.props;
  return <WrappedComponent {...this.props} />
}

// good
render() {
  const { irrelevantProp, ...relevantProps } = this.props;
  return <WrappedComponent {...relevantProps} />
}
```

## Refs

- Always use ref callbacks. eslint: [`react/no-string-refs`](https://github.com/jsx-eslint/eslint-plugin-react/blob/master/docs/rules/no-string-refs.md)

  ```jsx
  // bad
  <Foo
    ref="myRef"
  />

  // good
  <Foo
    ref={(ref) => { this.myRef = ref; }}
  />
  ```

## Parentheses

- Wrap JSX tags in parentheses when they span more than one line. eslint: [`react/jsx-wrap-multilines`](https://github.com/jsx-eslint/eslint-plugin-react/blob/master/docs/rules/jsx-wrap-multilines.md)

  ```jsx
  // bad
  render() {
    return <MyComponent variant="long body" foo="bar">
             <MyChild />
           </MyComponent>;
  }

  // good
  render() {
    return (
      <MyComponent variant="long body" foo="bar">
        <MyChild />
      </MyComponent>
    );
  }

  // good, when single line
  render() {
    const body = <div>hello</div>;
    return <MyComponent>{body}</MyComponent>;
  }
  ```

## Tags

- Always self-close tags that have no children. eslint: [`react/self-closing-comp`](https://github.com/jsx-eslint/eslint-plugin-react/blob/master/docs/rules/self-closing-comp.md)

  ```jsx
  // bad
  <Foo variant="stuff"></Foo>

  // good
  <Foo variant="stuff" />
  ```

- If your component has multiline properties, close its tag on a new line. eslint: [`react/jsx-closing-bracket-location`](https://github.com/jsx-eslint/eslint-plugin-react/blob/master/docs/rules/jsx-closing-bracket-location.md)

  ```jsx
  // bad
  <Foo
    bar="bar"
    baz="baz" />

  // good
  <Foo
    bar="bar"
    baz="baz"
  />
  ```

## Methods

- Use arrow functions to close over local variables. It is handy when you need to pass additional data to an event handler. Although, make sure they [do not massively hurt performance](https://www.bignerdranch.com/blog/choosing-the-best-approach-for-react-event-handlers/), in particular when passed to custom components that might be PureComponents, because they will trigger a possibly needless rerender every time.

  ```jsx
  function ItemList(props) {
    return (
      <ul>
        {props.items.map((item, index) => (
          <Item
            key={item.key}
            onClick={(event) => {
              doSomethingWith(event, item.name, index);
            }}
          />
        ))}
      </ul>
    );
  }
  ```

- Bind event handlers for the render method in the constructor. eslint: [`react/jsx-no-bind`](https://github.com/jsx-eslint/eslint-plugin-react/blob/master/docs/rules/jsx-no-bind.md)

  > Why? A bind call in the render path creates a brand new function on every single render. Do not use arrow functions in class fields, because it makes them [challenging to test and debug, and can negatively impact performance](https://medium.com/@charpeni/arrow-functions-in-class-properties-might-not-be-as-great-as-we-think-3b3551c440b1), and because conceptually, class fields are for data, not logic.

  ```jsx
  // bad
  class extends React.Component {
    onClickDiv() {
      // do stuff
    }

    render() {
      return <div onClick={this.onClickDiv.bind(this)} />;
    }
  }

  // very bad
  class extends React.Component {
    onClickDiv = () => {
      // do stuff
    }

    render() {
      return <div onClick={this.onClickDiv} />
    }
  }

  // good
  class extends React.Component {
    constructor(props) {
      super(props);

      this.onClickDiv = this.onClickDiv.bind(this);
    }

    onClickDiv() {
      // do stuff
    }

    render() {
      return <div onClick={this.onClickDiv} />;
    }
  }
  ```

- Do not use underscore prefix for internal methods of a React component.

  > Why? Underscore prefixes are sometimes used as a convention in other languages to denote privacy. But, unlike those languages, there is no native support for privacy in JavaScript, everything is public. Regardless of your intentions, adding underscore prefixes to your properties does not actually make them private, and any property (underscore-prefixed or not) should be treated as being public. See issues [#1024](https://github.com/airbnb/javascript/issues/1024), and [#490](https://github.com/airbnb/javascript/issues/490) for a more in-depth discussion.

  ```jsx
  // bad
  React.createClass({
    _onClickSubmit() {
      // do stuff
    },

    // other stuff
  });

  // good
  class extends React.Component {
    onClickSubmit() {
      // do stuff
    }

    // other stuff
  }
  ```

- Be sure to return a value in your `render` methods. eslint: [`react/require-render-return`](https://github.com/jsx-eslint/eslint-plugin-react/blob/master/docs/rules/require-render-return.md)

  ```jsx
  // bad
  render() {
    (<div />);
  }

  // good
  render() {
    return (<div />);
  }
  ```

## Ordering

- Ordering for `class extends React.Component`:

1. optional `static` methods
1. `constructor`
1. `getChildContext`
1. `componentWillMount`
1. `componentDidMount`
1. `componentWillReceiveProps`
1. `shouldComponentUpdate`
1. `componentWillUpdate`
1. `componentDidUpdate`
1. `componentWillUnmount`
1. _event handlers starting with 'handle'_ like `handleSubmit()` or `handleChangeDescription()`
1. _event handlers starting with 'on'_ like `onClickSubmit()` or `onChangeDescription()`
1. _getter methods for `render`_ like `getSelectReason()` or `getFooterContent()`
1. _optional render methods_ like `renderNavigation()` or `renderProfilePicture()`
1. `render`

- How to define `propTypes`, `defaultProps`, `contextTypes`, etc...

  ```jsx
  import React from "react";
  import PropTypes from "prop-types";

  const propTypes = {
    id: PropTypes.number.isRequired,
    url: PropTypes.string.isRequired,
    text: PropTypes.string,
  };

  const defaultProps = {
    text: "Hello World",
  };

  class Link extends React.Component {
    static methodsAreOk() {
      return true;
    }

    render() {
      return (
        <a href={this.props.url} data-id={this.props.id}>
          {this.props.text}
        </a>
      );
    }
  }

  Link.propTypes = propTypes;
  Link.defaultProps = defaultProps;

  export default Link;
  ```

- Ordering for `React.createClass`: eslint: [`react/sort-comp`](https://github.com/jsx-eslint/eslint-plugin-react/blob/master/docs/rules/sort-comp.md)

1. `displayName`
1. `propTypes`
1. `contextTypes`
1. `childContextTypes`
1. `mixins`
1. `statics`
1. `defaultProps`
1. `getDefaultProps`
1. `getInitialState`
1. `getChildContext`
1. `componentWillMount`
1. `componentDidMount`
1. `componentWillReceiveProps`
1. `shouldComponentUpdate`
1. `componentWillUpdate`
1. `componentDidUpdate`
1. `componentWillUnmount`
1. _clickHandlers or eventHandlers_ like `onClickSubmit()` or `onChangeDescription()`
1. _getter methods for `render`_ like `getSelectReason()` or `getFooterContent()`
1. _optional render methods_ like `renderNavigation()` or `renderProfilePicture()`
1. `render`

## `isMounted`

- Do not use `isMounted`. eslint: [`react/no-is-mounted`](https://github.com/jsx-eslint/eslint-plugin-react/blob/master/docs/rules/no-is-mounted.md)

> Why? [`isMounted` is an anti-pattern][anti-pattern], is not available when using ES6 classes, and is on its way to being officially deprecated.

[anti-pattern]: https://facebook.github.io/react/blog/2015/12/16/ismounted-antipattern.html

**[⬆ back to top](#table-of-contents)**
