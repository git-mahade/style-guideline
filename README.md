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

---

# TypeScript Style Guide

## Table of Contents

1. [Types-next](#types-next)
1. [Functions-next](#functions-next)
1. [Variables-next](#variables-next)
1. [Null & Undefined](#null--undefined)
1. [Naming](#naming)
1. [React Components](#react-components)
1. [Comments-next](#comments-next)
1. [Source File Structure](#source-file-structure-and-best-practices)

---

# React/JSX Style Guide

## Table of Contents

1. [Basic Rules](#basic-rules)
1. [Component definition](#component-definition)
1. [Project organization](#project-organization)
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
1. [Use ES6 classes.](#use-es2015-classes)
1. [Component method and property ordering](#component-method-and-property-ordering)
1. [Name handlers handleEventName.](#name-handlers-handleeventname)
1. [Name handlers in props onEventName.](#name-handlers-in-props-oneventname)
1. [Open elements on the same line.](#open-elements-on-the-same-line)
1. [Align and sort HTML properties.](#align-and-sort-html-properties)
1. [Only export a single react class.](#only-export-a-single-react-class)
1. [Make "presentation" components pure.](#make-presentation-components-pure)
1. [Prefer <a href="http://facebook.github.io/react/docs/interactivity-and-dynamic-uis.html#what-components-should-have-state">props to state</a>.](#prefer-props-to-state)
1. [<em>Never</em> store state in the DOM.](#never-store-state-in-the-dom)
1. [Use Flow instead of PropTypes](#use-flow-instead-of-proptypes)
1. [Annotate `children`](#annotate-children)
1. [Props must be plain JSON](#props-must-be-plain-json)
1. [Pure functions of props and state](#pure-functions-of-props-and-state)
1. [Side effect free until `componentDidMount`](#side-effect-free-until-componentdidmount)
1. [Do not use Backbone models.](#do-not-use-backbone-models)
1. [Minimize use of jQuery.](#minimize-use-of-jquery)
1. [Reuse standard components.](#reuse-standard-components)
1. [80 columns, soft tabs of 2 spaces](#80-columns-soft-tabs-of-2-spaces)
1. [Camel case instead of dash-case for class names](#camel-case-instead-of-dash-case-for-class-names)
1. [Never use ID and tag name as root selectors!](#never-use-id-and-tag-name-as-root-selectors)
1. [When using multiple selectors, give each selector its own line](#when-using-multiple-selectors-give-each-selector-its-own-line)
1. [Break lines in CSS function arguments](#break-lines-in-css-function-arguments)
1. [When writing rules, be sure to](#when-writing-rules-be-sure-to)
1. [The parent constrains the child](#the-parent-constrains-the-child)
1. [The parent doesn't assume child structure](#the-parent-doesnt-assume-child-structure)
1. [Components never leak margin](#components-never-leak-margin)
1. [The parent spaces the children](#the-parent-spaces-the-children)
1. [Nested classes aren't for providing scope](#nested-classes-arent-for-providing-scope)
1. [Variables, lots of variables!](#variables-lots-of-variables)

---

# NEXT JS Style Guide

## Table of Contents

1. [Next.js Lazy Loading](#nextjs-lazy-loading)
1. [Next.js Code Splitting with `next/dynamic`](#nextjs-code-splitting-with-nextdynamic)
1. [Lazy Loading of Images](#lazy-loading-of-images)
1. [Using Built-in Components](#using-built-in-components)
1. [Use CSS Modules](#use-css-modules)
1. [Caching Data in Next.js](#caching-data-in-nextjs)
1. [Use Route Handlers](#use-route-handlers)
1. [Use Multiple Data Rendering Modes](#use-multiple-data-rendering-modes)
1. [TypeScript Support](#typescript-support)
1. [Enhance SEO in Next.js](#enhance-seo-in-nextjs)
1. [Remove Unused Dependencies & Code](#remove-unused-dependencies--code)
1. [Deploy Your Next.js App to Vercel](#deploy-your-nextjs-app-to-vercel)
1. [Client Component Placement Strategy in Next.js](#client-component-placement-strategy-in-nextjs)

---

# JavaScript

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
# TypeScript

## Types

When creating types, we aim to accurately describe our code, which brings several benefits to the codebase:

- **Increased Type Safety**: Catch errors at compile-time by using narrowed types that provide specific information about data shape and behavior.
- **Improved Code Clarity**: Reduce cognitive load with clearer boundaries and constraints on data, making code easier to understand.
- **Easier Refactoring**: Types that are narrow make code changes less risky, allowing for confident refactoring.
- **Optimized Performance**: Narrow types can sometimes help TypeScript generate more optimized JavaScript code.

### Type Inference

As a rule of thumb, explicitly declare a type when it helps narrow it:

```typescript
// ❌ Avoid - Don't explicitly declare a type, it can be inferred.
const userRole: string = 'admin'; // Type 'string'
const employees = new Map<string, number>([['Gabriel', 32]]);
const [isActive, setIsActive] = useState<boolean>(false);

// ✅ Use type inference.
const USER_ROLE = 'admin'; // Type 'admin'
const employees = new Map([['Gabriel', 32]]); // Type 'Map<string, number>'
const [isActive, setIsActive] = useState(false); // Type 'boolean'

// ❌ Avoid - Don't infer a (wide) type, it can be narrowed.
const employees = new Map(); // Type 'Map<any, any>'
employees.set('Lea', 'foo-anything');
type UserRole = 'admin' | 'guest';
const [userRole, setUserRole] = useState('admin'); // Type 'string'

// ✅ Use explicit type declaration to narrow the type.
const employees = new Map<string, number>(); // Type 'Map<string, number>'
employees.set('Gabriel', 32);
type UserRole = 'admin' | 'guest';
const [userRole, setUserRole] = useState<UserRole>('admin');
```

### Data Immutability

Majority of the data should be immutable with use of `Readonly`, `ReadonlyArray`.

Using `readonly` type prevents accidental data mutations, which reduces the risk of introducing bugs related to unintended side effects.

When performing data processing always return new array, object etc. To keep cognitive load for future developers low, try to keep data objects small.

As an exception mutations should be used sparingly in cases where truly necessary: complex objects, performance reasoning etc.

#### Examples

```typescript
// ❌ Avoid data mutations
const removeFirstUser = (users: Array<User>) => {
  if (users.length === 0) {
    return users;
  }
  return users.splice(1);
};

// ✅ Use readonly type to prevent accidental mutations
const removeFirstUser = (users: ReadonlyArray<User>) => {
  if (users.length === 0) {
    return users;
  }
  return users.slice(1);
  // Using arr.splice(1) errors - Function 'splice' does not exist on 'users'
};
```

### Return Types

Including return type annotations is highly encouraged, although not required (eslint rule).

Consider benefits when explicitly typing the return value of a function:

- Return values make it clear and easy to understand to any calling code what type is returned.
- In cases where there is no return value, the calling code doesn't try to use the undefined value when it shouldn't.
- Surface potential type errors faster in the future if there are code changes that change the return type of the function.
- Easier to refactor, since it ensures that the return value is assigned to a variable of the correct type.
- Similar to writing tests before implementation (TDD), defining function arguments and return type gives you the opportunity to discuss the feature functionality and its interface ahead of implementation.
- Although type inference is very convenient, adding return types can save TypeScript compiler a lot of work.

### Discriminated Union

If there is only one TypeScript feature to choose, embrace discriminated unions.

Discriminated unions are a powerful concept to model complex data structures and improve type safety, leading to clearer and less error-prone code.

You may encounter discriminated unions under different names such as tagged unions or sum types in various programming languages like C, Haskell, Rust (in conjunction with pattern-matching).

#### Example

```typescript
type Circle = { kind: 'circle'; radius: number };
type Square = { kind: 'square'; size: number };
type Triangle = { kind: 'triangle'; base: number; height: number };

// Create discriminated union 'Shape', with 'kind' property to discriminate the type of object.
type Shape = Circle | Square | Triangle;

// TypeScript warns us with errors in calculateArea function
const calculateArea = (shape: Shape) => {
  // Error - Switch is not exhaustive. Cases not matched: "triangle"
  switch (shape.kind) {
    case 'circle':
      return Math.PI * shape.radius ** 2;
    case 'square':
      return shape.size * shape.width; // Error - Property 'width' does not exist on type 'square'
  }
};
```

### Avoid code complexity introduced by flag variables

- Clear code intent, as it becomes easier to read and understand by explicitly indicating the possible cases for a given type.
- TypeScript can narrow down union types, ensuring code correctness at compile time.
- Discriminated unions make refactoring and maintenance easier by providing a centralized definition of related types. When adding or modifying types within the union, the compiler reports any inconsistencies throughout the codebase.
- IDEs can leverage discriminated unions to provide better autocompletion and type inference.

### Template Literal Types

Embrace using template literal types, instead of just (wide) string type.
Template literal types have many applicable use cases e.g. API endpoints, routing, internationalization, database queries, CSS typings ...

#### Examples

```typescript
// ❌ Avoid
const userEndpoint = '/api/usersss'; // Type 'string' - Since typo 'usersss', route doesn't exist and results in runtime error
// ✅ Use
type ApiRoute = 'users' | 'posts' | 'comments';
type ApiEndpoint = `/api/${ApiRoute}`; // Type ApiEndpoint = "/api/users" | "/api/posts" | "/api/comments"
const userEndpoint: ApiEndpoint = '/api/users';

// ❌ Avoid
const homeTitle = 'translation.homesss.title'; // Type 'string' - Since typo 'homesss', translation doesn't exist and results in runtime error
// ✅ Use
type LocaleKeyPages = 'home' | 'about' | 'contact';
type TranslationKey = `translation.${LocaleKeyPages}.${string}`; // Type TranslationKey = `translation.home.${string}` | `translation.about.${string}` | `translation.contact.${string}`
const homeTitle: TranslationKey = 'translation.home.title';

// ❌ Avoid
const color = 'blue-450'; // Type 'string' - Since color 'blue-450' doesn't exist and results in runtime error
// ✅ Use
type BaseColor = 'blue' | 'red' | 'yellow' | 'gray';
type Variant = 50 | 100 | 200 | 300 | 400;
type Color = `${BaseColor}-${Variant}` | `#${string}`; // Type Color = "blue-50" | "blue-100" | "blue-200" ... | "red-50" | "red-100" ... | #${string}
const iconColor: Color = 'blue-400';
const customColor: Color = '#AD3128';
```

### Type `any` & `unknown`

- `any` data type must not be used as it represents literally “any” value that TypeScript defaults to and skips type checking since it cannot infer the type. As such, `any` is dangerous and can mask severe programming errors.
- When dealing with ambiguous data types, use `unknown`, which is the type-safe counterpart of `any`.
- `unknown` doesn't allow dereferencing all properties (anything can be assigned to `unknown`, but `unknown` isn’t assignable to anything).

#### Examples

```typescript
// ❌ Avoid any
const foo: any = 'five';
const bar: number = foo; // no type error

// ✅ Use unknown
const foo: unknown = 5;
const bar: number = foo; // type error - Type 'unknown' is not assignable to type 'number'

// Narrow the type before dereferencing it using:
// Type guard
const isNumber = (num: unknown): num is number => {
  return typeof num === 'number';
};
if (!isNumber(foo)) {
  throw Error(`API provided a fault value for field 'foo': ${foo}. Should be a number!`);
}
const bar: number = foo;

// Type assertion
const bar: number = foo as number;
```

### Type & Non-nullability Assertions

Type assertions (`user as User`) and non-nullability assertions (`user!.name`) are unsafe. Both only silence TypeScript compiler and increase the risk of crashing application at runtime. They can only be used as an exception (e.g. third-party library types mismatch, dereferencing `unknown` etc.) with strong rationale why being introduced into codebase.

#### Example

```typescript
type User = { id: string; username: string; avatar: string | null };
// ❌ Avoid type assertions
const user = { name: 'Nika' } as User;
// ❌ Avoid non-nullability assertions
renderUserAvatar(user!.avatar); // Runtime error

const renderUserAvatar = (avatar: string) => {...};
```

### Type Error

If TypeScript error can't be mitigated, as last resort use `@ts-expect-error` to suppress

 it (eslint rule). If at any future point suppressed line becomes error-free, TypeScript compiler will indicate it.
`@ts-ignore` is not allowed, where `@ts-expect-error` must be used with provided description (eslint rule).

#### Example

```typescript
// ❌ Avoid @ts-ignore
// @ts-ignore
const newUser = createUser('Gabriel');

// ✅ Use @ts-expect-error with description
// @ts-expect-error: The library type definition is wrong, createUser accepts string as an argument.
const newUser = createUser('Gabriel');
```

### Type Definition

TypeScript offers two options for type definitions - `type` and `interface`. As they come with some functional differences in most cases they can be used interchangeably. We try to limit syntax difference and pick one for consistency.

All types must be defined with type alias (eslint rule).

#### Example

```typescript
// ❌ Avoid interface definitions
interface UserRole = 'admin' | 'guest'; // invalid - interface can't define (commonly used) type unions

interface UserInfo {
  name: string;
  role: 'admin' | 'guest';
}

// ✅ Use type definition
type UserRole = 'admin' | 'guest';

type UserInfo = {
  name: string;
  role: UserRole;
};

// In case of declaration merging (e.g. extending third-party library types) use interface and disable lint rule.

// types.ts
declare namespace NodeJS {
  // eslint-disable-next-line @typescript-eslint/consistent-type-definitions
  export interface ProcessEnv {
    NODE_ENV: 'development' | 'production';
    PORT: string;
    CUSTOM_ENV_VAR: string;
  }
}

// server.ts
app.listen(process.env.PORT, () => {...});
```

### Array Types

Array types must be defined with generic syntax (eslint rule).

#### Example

```typescript
// ❌ Avoid
const x: string[] = ['foo', 'bar'];
const y: readonly string[] = ['foo', 'bar'];

// ✅ Use
const x: Array<string> = ['foo', 'bar'];
const y: ReadonlyArray<string> = ['foo', 'bar'];
```


### Services

Documentation becomes outdated the moment it's written, and worse than no documentation is wrong documentation. The same can be said about types when describing modules your app interacts with (APIs, messaging systems, databases).

For external API services e.g. REST, GraphQL etc. it's crucial to generate types from their contracts, whether it's Swagger, schemas, or other sources (e.g. openapi-ts, graphql-config...). Avoid manually declaring and maintaining them, as it's easy to get them out of sync.

As an exception, manually declare types only when there is truly no documentation provided by the external service.

**[⬆ back to top](#table-of-contents)**

## Functions

### General
- Function should have single responsibility.
- Function should be stateless where the same input arguments return the same value every single time.
- Function should accept at least one argument and return data.
- Function should not have side effects, but be pure. Its implementation should not modify or access variable values outside its local environment (global state, fetching etc.).

### Single Object Arg
To keep functions readable and easily extensible for the future (adding/removing args), strive to have a single object as the function argument, instead of multiple args. As an exception, this does not apply when having only one primitive single arg (e.g. simple functions like `isNumber(value)`, implementing currying etc.).

```typescript
// ❌ Avoid having multiple arguments
transformUserInput('client', false, 60, 120, null, true, 2000);

// ✅ Use options object as argument
transformUserInput({
  method: 'client',
  isValidated: false,
  minLines: 60,
  maxLines: 120,
  defaultInput: null,
  shouldLog: true,
  timeout: 2000,
});
```

### Required & Optional Args
- Strive to have the majority of args required and use optional sparingly.
- If a function becomes too complex, it probably should be broken into smaller pieces.
- An exaggerated example where implementing 10 functions with 5 required args each is better than implementing one "can do it all" function that accepts 50 optional args.

### Args as Discriminated Union
When applicable, use discriminated union type to eliminate optional args, which will decrease complexity on function API and only necessary/required args will be passed depending on its use case.

```typescript
// ❌ Avoid optional args as they increase complexity of function API
type StatusParams = {
  data?: Products;
  title?: string;
  time?: number;
  error?: string;
};

// ✅ Strive to have majority of args required, if that's not possible,
// use discriminated union for clear intent on function usage
type StatusParamsSuccess = {
  status: 'success';
  data: Products;
  title: string;
};

type StatusParamsLoading = {
  status: 'loading';
  time: number;
};

type StatusParamsError = {
  status: 'error';
  error: string;
};

type StatusParams = StatusParamsSuccess | StatusParamsLoading | StatusParamsError;

export const parseStatus = (params: StatusParams) => {...};
```
**[⬆ back to top](#table-of-contents)**

## Variables

### Const Assertion
Strive to use const assertion as `const`:
- Type is narrowed.
- Object gets readonly properties.
- Array becomes readonly tuple.

```typescript
// ❌ Avoid declaring constants without const assertion
const FOO_LOCATION = { x: 50, y: 130 }; // Type { x: number; y: number; }
FOO_LOCATION.x = 10;

const BAR_LOCATION = [50, 130]; // Type number[]
BAR_LOCATION.push(10);

const RATE_LIMIT = 25;
const RATE_LIMIT_MESSAGE = `Max number of requests/min is ${RATE_LIMIT}.`; // Type string

// ✅ Use const assertion
const FOO_LOCATION = { x: 50, y: 130 } as const; // Type '{ readonly x: 50; readonly y: 130; }'
FOO_LOCATION.x = 10; // Error

const BAR_LOCATION = [50, 130] as const; // Type 'readonly [10, 20]'
BAR_LOCATION.push(10); // Error

const RATE_LIMIT = 25;
const RATE_LIMIT_MESSAGE = `Max number of requests/min is ${RATE_LIMIT}.` as const; // Type 'Rate limit exceeded! Max number of requests/min is 25.'
```

### Enums & Const Assertion
Const assertion must be used over enum.

```typescript
// .eslintrc.js
'no-restricted-syntax': [
  'error',
  {
    selector: 'TSEnumDeclaration',
    message: 'Use const assertion or a string union type instead.',
  },
],

// ❌ Avoid using enums
enum UserRole {
  GUEST,
  MODERATOR,
  ADMINISTRATOR,
}

enum Color {
  PRIMARY = '#B33930',
  SECONDARY = '#113A5C',
  BRAND = '#9C0E7D',
}

// ✅ Use const assertion
const USER_ROLES = ['guest', 'moderator', 'administrator'] as const;
type UserRole = (typeof USER_ROLES)[number]; // Type "guest" | "moderator" | "administrator"

// Use satisfies if UserRole type is already defined - e.g. database schema model
type UserRoleDB = ReadonlyArray<'guest' | 'moderator' | 'administrator'>;
const AVAILABLE_ROLES = ['guest', 'moderator'] as const satisfies UserRoleDB;

const COLOR = {
  primary: '#B33930',
  secondary: '#113A5C',
  brand: '#9C0E7D',
} as const;
type Color = typeof COLOR;
type ColorKey = keyof Color; // Type "primary" | "secondary" | "brand"
type ColorValue = Color[ColorKey]; // Type "#B33930" | "#113A5C" | "#9C0E7D"
```

## Type Union & Boolean Flags

Strive to use type union variables instead of multiple boolean flag variables.

```typescript
// ❌ Avoid introducing multiple boolean flag variables
const isPending, isProcessing, isConfirmed, isExpired;

// ✅ Use type union variable
type UserStatus = 'pending' | 'processing' | 'confirmed' | 'expired';
const userStatus: UserStatus;
```

When maintaining code that makes the number of possible states grow quickly because of flags, there are almost always unhandled states. Utilize discriminated unions.

## Null & Undefined

In TypeScript, types `null` and `undefined` can often be used interchangeably. Strive to:
- Use `null` to explicitly state it has no value - assignment, return function type etc.
- Use `undefined` assignment when the value doesn't exist. E.g. exclude fields in form, request payload, database query (Prisma differentiation)

**[⬆ back to top](#table-of-contents)**

## Naming

Strive to keep naming conventions consistent and readable, with important context provided, because another person will maintain the code you have written.

### Named Export

Named exports must be used to ensure that all imports follow a uniform pattern (eslint rule).

```javascript
// .eslintrc.js
overrides: [
  {
    files: ["src/pages/**/*"],
    rules: { "import/no-default-export": "off" },
  },
],
```

### Naming Conventions

While it's often hard to find the best name, try to optimize code for consistency and future readers by following conventions:

### Variables

- Locals: Camel case (`products`, `productsFiltered`)
- Booleans: Prefixed with `is`, `has` etc. (`isDisabled`, `hasProduct`)

```javascript
// .eslintrc.js
'@typescript-eslint/naming-convention': [
  'error',
  {
    selector: 'variable',
    types: ['boolean'],
    format: ['PascalCase'],
    prefix: ['is', 'should', 'has', 'can', 'did', 'will'],
  },
],
```

### Constants

- Capitalized (`PRODUCT_ID`)
- Object constants: Singular, capitalized with const assertion.

```typescript
const ORDER_STATUS = {
  pending: 'pending',
  fulfilled: true,
  error: 'Shipping Error',
} as const;

// If object type exists, use satisfies operator in conjunction with const assertion to ensure the object matches its type.
type OrderStatus = {
  pending: 'pending' | 'idle';
  fulfilled: boolean;
  error: string;
};

const ORDER_STATUS = {
  pending: 'pending',
  fulfilled: true,
  error: 'Shipping Error',
} as const satisfies OrderStatus;
```

### Functions

- Camel case (`filterProductsByType`, `formatCurrency`)
- Types: Pascal case (`OrderStatus`, `ProductItem`)

```javascript
// .eslintrc.js
'@typescript-eslint/naming-convention': [
  'error',
  {
    selector: 'typeAlias',
    format: ['PascalCase'],
  },
],
```

### Generics

A generic variable must start with the capital letter T followed by a descriptive name (`TRequest`, `TFooBar`).

```typescript
// ❌ Avoid naming generics with one letter
const createPair = <T, K extends string>(first: T, second: K): [T, K] => {
  return [first, second];
};
const pair = createPair(1, 'a');

// ✅ Name starts with the capital letter T followed by a descriptive name
const createPair = <TFirst, TSecond extends string>(first: TFirst, second: TSecond): [TFirst, TSecond] => {
  return [first, second];
};
const pair = createPair(1, 'a

');

// .eslintrc.js
'@typescript-eslint/naming-convention': [
  'error',
  {
    // Generic type parameter must start with letter T, followed by any uppercase letter.
    selector: 'typeParameter',
    format: ['PascalCase'],
    custom: { regex: '^T[A-Z]', match: true },
  },
],
```

### Abbreviations & Acronyms

Treat acronyms as whole words, with the capitalized first letter only.

```javascript
// ❌ Avoid
const FAQList = ['qa-1', 'qa-2'];
const generateUserURL(params) => {...}

// ✅ Use
const FaqList = ['qa-1', 'qa-2'];
const generateUserUrl(params) => {...}

// In favor of readability, strive to avoid abbreviations, unless they are widely accepted and necessary.

// ❌ Avoid
const GetWin(params) => {...}

// ✅ Use
const GetWindow(params) => {...}
```

### React Components

#### Prop Types

React component names should follow the "Props" postfix convention (`[ComponentName]Props` - `ProductItemProps`, `ProductsPageProps`).

#### Callback Props

- Event handler (callback) props are prefixed as `on*` - e.g. `onClick`.
- Event handler implementation functions are prefixed as `handle*` - e.g. `handleClick` (eslint rule).

```javascript
// ❌ Avoid inconsistent callback prop naming
<Button click={actionClick} />
<MyComponent userSelectedOccurred={triggerUser} />

// ✅ Use prop prefix 'on*' and handler prefix 'handle*'
<Button onClick={handleClick} />
<MyComponent onUserSelected={handleUserSelected} />
```

### React Hooks

- Camel case, prefixed as 'use' (eslint rule), symmetrically convention as `[value, setValue] = useState()` (eslint rule).

```javascript
// ❌ Avoid inconsistent useState hook naming
const [userName, setUser] = useState();
const [color, updateColor] = useState();
const [isActive, setActive] = useState();

// ✅ Use
const [name, setName] = useState();
const [color, setColor] = useState();
const [isActive, setIsActive] = useState();

// Custom hook must always return an object:

// ❌ Avoid
const [products, errors] = useGetProducts();
const [fontSizes] = useTheme();

// ✅ Use
const { products, errors } = useGetProducts();
const { fontSizes } = useTheme();
```
**[⬆ back to top](#table-of-contents)**

## Comments

In general, try to avoid comments by writing expressive code and naming things what they are.

Use comments when you need to add context or explain choices that cannot be expressed through code (e.g. config files). Comments should always be complete sentences. As a rule of thumb, try to explain why in comments, not how and what.

```javascript
// ❌ Avoid
// convert to minutes
const m = s * 60;
// avg users per minute
const myAvg = u / m;

// ✅ Use - Expressive code and name things what they are
const SECONDS_IN_MINUTE = 60;
const minutes = seconds * SECONDS_IN_MINUTE;
const averageUsersPerMinute = noOfUsers / minutes;

// ✅ Use - Add context to explain why in comments
// TODO: Filtering should be moved to the backend once API changes are released.
// Issue/PR - https://github.com/foo/repo/pulls/55124
const filteredUsers = frontendFiltering(selectedUsers);
// Use Fourier transformation to minimize information loss - https://github.com/dntj/jsfft#usage
const frequencies = signal.FFT();
```
Here's the TypeScript source file structure and best practices formatted with markup for clarity:

---
**[⬆ back to top](#table-of-contents)**

## Source File Structure and Best Practices

Files should adhere to a structured format for clarity and maintainability.

### Copyright Information

If necessary, include license or copyright information within a JSDoc at the top of the file.

```javascript
/**
 * @fileoverview Copyright (c) 2024 Your Company. All rights reserved.
 * @license Licensed under the MIT License.
 */
```

### @fileoverview JSDoc

Optionally provide a high-level description of the file's content, dependencies, or usage.

```javascript
/**
 * @fileoverview Description of file content, usage, or dependencies.
 * Detailed description if needed, wrapped as necessary.
 */
```

### Imports

Imports should precede the file's implementation.

#### TypeScript Imports

Four types of imports are commonly used in ES6 and TypeScript:

- Module import: `import * as foo from '...';`
- Named import: `import {SomeThing} from '...';`
- Default import: `import SomeThing from '...';`
- Side-effect import: `import '...';`

```javascript
// Good: Example of imports
import * as ng from '@angular/core';
import {Foo} from './foo';
import Button from 'Button';
import 'jasmine';
```

### Import Paths

Use relative paths (`./foo`) for TypeScript imports within the same project to maintain flexibility.

```javascript
// Example of import paths
import {Symbol1} from 'path/from/root';
import {Symbol2} from '../parent/file';
import {Symbol3} from './sibling';
```

### Namespace vs Named Imports

Prefer named imports for clarity and avoid excessively long namespace imports.

```javascript
// Prefer named imports
import {describe, it, expect} from './testing';
```

### Renaming Imports

Rename imports to avoid naming collisions or improve readability.

```javascript
// Example of renaming imports
import {Item as TableviewItem} from './tableview';
```

### Exports

Use named exports exclusively for clear and maintainable code.

```typescript
// Example of named exports
export class Foo { ... }
```

### Export Visibility

Export symbols only if they are used outside the module to minimize API surface.

```typescript
// Example of export visibility
export const SOME_CONSTANT = ...
```

### Mutable Exports

Avoid mutable exports to prevent unexpected behavior and maintain code clarity.

```typescript
// Avoid mutable exports
export let foo = 3;
```

### Import and Export Type

Differentiate between importing types and values using `import type` and `export type`.

```typescript
// Example of import type and export type
import type {Foo} from './foo';
export type {AnInterface} from './foo';
```

### Use Modules, Not Namespaces

Organize code using ES6 modules (`import` and `export`) instead of namespaces (`namespace`).

```typescript
// Example of using modules instead of namespaces
import {foo} from 'bar';
```

---

**[⬆ back to top](#table-of-contents)**

# React

## Basic Rules

- Only include one React component per file.
  - However, multiple [Stateless, or Pure, Components](https://facebook.github.io/react/docs/reusable-components.html#stateless-functions) are allowed per file. eslint: [`react/no-multi-comp`](https://github.com/jsx-eslint/eslint-plugin-react/blob/master/docs/rules/no-multi-comp.md#ignorestateless).
- Always use JSX syntax.
- Do not use `React.createElement` unless you’re initializing the app from a file that is not JSX.
- [`react/forbid-prop-types`](https://github.com/jsx-eslint/eslint-plugin-react/blob/master/docs/rules/forbid-prop-types.md) will allow `arrays` and `objects` only if it is explicitly noted what `array` and `object` contains, using `arrayOf`, `objectOf`, or `shape`.

## Component definition

All components (presentation, containers or pages) should **always** be
defined as a directory, named with pascal casing. The main component file
should be `index.js`, main stylesheet `style.css`. CSS custom properties
can be kept in `properties.css`:

```
AwesomeCard/
├── index.js
├── properties.css
└── style.css
```

* Styles should always be defined in a separate CSS file
* Avoid prefixing or suffixing component names
  - E.g.: `lib/pages/UserPage` or `lib/container/UserContainer`
* On conflict rename on import time
  - `import UserContainer from '...'`
  - `import { User as UserContainer } from '...'`

**[⬆ back to top](#table-of-contents)**

## Project organization

Your project components should be separated in at least three directories:

```
awesome-react-project/
└── src/
   ├── components/
   ├── containers/
   └── pages/
```

Each of these directories have special types of components:

### `components/`

Stateless components. Shouldn't store state. Most components in this
directory will be function-based components. Stuff like buttons, inputs,
labels and all presentational components goes here. This components can
also accept functions as props and dispatch events, but no state should
be held inside.

### `containers/`

Container components can store state. Containers are built mostly from
the composition of presentational components with some styles to layout
them together. Containers can also store internal state and access refs
to provide additional logic, but all actions should be accepted as
component callbacks.

### `pages/`

Page components can store state, receive route parameters and dispatch
Redux actions when applicable. Pages are the highest level of application's
components. They represent the application routes and most times are
displayed by a router. Pages are also responsible for handling container
components callbacks and flowing data into children containers.

**[⬆ back to top](#table-of-contents)**

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

  **[⬆ back to top](#table-of-contents)**

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

**[⬆ back to top](#table-of-contents)**

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

**[⬆ back to top](#table-of-contents)**

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

**[⬆ back to top](#table-of-contents)**

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

## Use ES2015 classes.

1. Use static properties for `defaultProps`.
2. Use an instance property for `state`.
3. Use flow for `props` and `state`.
4. Autobind event handlers and callbacks.

   Example:

   ```jsx
   import React, { Component } from "react";

   class Foo extends Component {
     static defaultProps = {};

     state = {};

     state: {};
     props: {};

     handleClick = (e) => {
       // handle the click
     };
   }
   ```

5. If `state` depends on `props`, define it in the constructor.

   Example:

   ```jsx
   class Bar extends Component {
     constructor(props) {
       super(props); // must be called first
       this.state = {
         value: props.value,
       };
     }
   }
   ```

6. Use higher order components instead of mixins.
   ES6 style classes do not support mixins. See the [mixins considered harmful](https://facebook.github.io/react/blog/2016/07/13/mixins-considered-harmful.html)
   blog post for details of how to convert mixins to higher order components.

**Codemods**

Converting legacy components to use ES2015 classes? There's a codemod for that.

Convert one or more files with the following command:

```bash
$ tools/react-codemod.js class path/to/file path/to/other/file
```

## Component method and property ordering

Ordering within a React component is strict. The following example
illustrates the precise ordering of various component methods and
properties:

```js
class Foo extends Component {
    // Static properties
    static defaultProps = {}

    // The `constructor` method
    constructor() {
        super();
    }

    // Instance properties
    state = { hi: 5}

    // Flow `state` annotation
    // NOTE: `state` is special. All other Flow annotations live below.
    state: { hi: number }

    // React lifecycle hooks.
    // They should follow their chronological ordering:
    // 1. componentWillMount
    // 2. componentDidMount
    // 3. componentWillReceiveProps
    // 4. shouldComponentUpdate
    // 5. componentWillUpdate
    // 6. componentDidUpdate
    // 7. componentWillUnmount
    componentDidMount() { ... }

    // All other Flow annotations
    props: { ... }
    someRandomData: string,

    // All other instance methods
    handleClick = (e) => { ... }

    // Finally, the render method
    render() { ... }
}
```

## Name handlers `handleEventName`.

Example:

```jsx
<Component
  onClick={this.handleClick}
  onLaunchMissiles={this.handleLaunchMissiles}
/>
```

## Name handlers in props `onEventName`.

This is consistent with React's event naming: `onClick`, `onDrag`,
`onChange`, etc.

Example:

```jsx
<Component onLaunchMissiles={this.handleLaunchMissiles} />
```

#### Open elements on the same line.

The 80-character line limit is a bit tight, so we opt to conserve the extra 4.

Yes:

```jsx
return <div>...</div>;
```

No:

```jsx
return (
  // "div" is not on the same line as "return"
  <div>...</div>
);
```

## Align and sort HTML properties.

Fit them all on the same line if you can. If you can't, put each
property on a line of its own, indented four spaces, in sorted order.
The closing angle brace should be on a line of its own, indented the
same as the opening angle brace. This makes it easy to see the props
at a glance.

Yes:

```jsx
<div className="highlight" key="highlight-div">
<div
    className="highlight"
    key="highlight-div"
>
<Image
    className="highlight"
    key="highlight-div"
/>
```

No:

```jsx
<div className="highlight"      // property not on its own line
     key="highlight-div"
>
<div                            // closing brace not on its own line
    className="highlight"
    key="highlight-div">
<div                            // property is not sorted
    key="highlight-div"
    className="highlight"
>
```

## Only export a single react class.

Every .jsx file should export a single React class, and nothing else.
This is for testability; the fixture framework requires it to
function.

Note that the file can still define multiple classes, it just can't export
more than one.


## Make "presentation" components pure.

It's useful to think of the React world as divided into ["logic"
components and "presentation" components](https://medium.com/@dan_abramov/smart-and-dumb-components-7ca2f9a7c7d0).

"Logic" components have application logic, but do not emit HTML
themselves.

"Presentation" components are typically reusable, and do emit HTML.

Logic components can have internal state, but presentation components
never should.

## Prefer [props to state](http://facebook.github.io/react/docs/interactivity-and-dynamic-uis.html#what-components-should-have-state).

You almost always want to use props. By avoiding state when possible,
you minimize redundancy, making it easier to reason about your
application.

A common pattern — which matches the "logic" vs. "presentation"
component distinction — is to create several stateless components
that just render data, and have a stateful component above them in the
hierarchy that passes its state to its children via props. The
stateful component encapsulates all of the interaction logic, while
the stateless components take care of rendering data in a declarative
way.

Copying data from props to state can cause the UI to get out of sync
and is especially bad.

## _Never_ store state in the DOM.

Do not use `data-` attributes or classes. All information
should be stored in JavaScript, either in the React component itself,
or in a React store if using a framework such as Redux.


## Type-checking with [Flow](https://flow.org/)

Flow is a type-checker that runs at compile-time to catch issues
and prevent bugs. It should be used on all new components.

For more information on how we use Flow, check the [Javascript
style guide](https://github.com/Khan/style-guides/blob/master/style/javascript.md#flow-rules)

## Use Flow instead of PropTypes

Props can now be validated with Flow instead of React's PropTypes.
Flow provides a much more expressive way to set types for props,
with the additional benefits of being able to annotate state (and
any additional methods or data).

Types can be defined on the class itself:

```jsx
class Foo extends Component {
  props: {
    name: string,
    uniqueId: number,
    complexData: {
      setOfThings: Array<string>,
    },
  };
}
```

If you're writing a Stateless Functional Component, or if you use
lifecycle methods that reference props (eg. `componentDidUpdate`),
you may find it helpful to define a Props type, and reference it:

```jsx
type Props = {
    numbers: Array<number>,
};

class Foo extends Component {
    props: Props

    shouldComponentUpdate(nextProps: Props) {
        ...
    }
}

const StatelessFoo = ({numbers}: Props) => {
    ...
};

```

## Annotate `children`

`children` is something of a special prop in React. Most often,
you'll want to pass a React element (or an array of React elements).

This can be annotated like so:

```js
children: React$Element<any> | Array<React$Element<any>>
```

Note that this is only the most common use-case for children.
Children can also be other types (like a string, or a function).


## Server-side rendering

To make components safe to render server-side, they must adhere
to a few more restrictions than regular components.

## Props must be plain JSON

In order to render server-side, the props are serialized and
deserialized from JSON. This means that e.g. dates must be
passed as timestamps as opposed to JS `Date` objects.

Note that this only applies to the root component being
rendered with server-side rendering. If the root component
constructs more complex data structures from props, and
passes those constructs down to child components, that won't
cause problems.

## Pure functions of props and state

Components must be pure functions of their `props` and `state`.
This means the output of their `render()` function must not
depend on either KA-specific globals, on browser-specific
state, or browser-specific APIs.

Examples of KA-specific globals include anything attached to
the `KA` global, e.g. `KA.getUserId()`, or data extracted from
the DOM such as `data-` properties attached to other DOM nodes.

Examples of browser-specific state include the user agent,
the screen resolution, the device pixel density etc.

An example of a browser-specific API is `canvas.getContext()`.

The output must be deterministic. One way to get
non-deterministic output is to generate random
IDs in `getInitialState()`, and have the output
of render depend on that ID. Don't do this.

## Side effect free until `componentDidMount`

The parts of the React component lifecycle that are run to
render on the server must be free from side effects.

Examples of side effects that must be avoided:

- Sending an AJAX request
- Mutating global JS state
- Injecting elements into the DOM
- Changing the page title
- `alert()`

The lifecycle methods that run on the server are currently:

- `getInitialState()`
- `getDefaultProps()`
- `componentWillMount()`
- `render()`

If you need to execute any of the above listed side effects,
you must do so in `componentDidMount` or later in the component
lifecycle. These functions are not executed server-side.


## Do not use Backbone models.

Use redux actions, or `fetch` directly, instead.

We are trying to remove Backbone from our codebase entirely.

## Minimize use of jQuery.

_Never_ use jQuery for DOM manipulation.

Try to avoid using jQuery plugins. When necessary, wrap the jQuery
plugin with a React component so you only have to touch the jQuery
once.

Use the [fetch API](https://developer.mozilla.org/en-US/docs/Web/API/GlobalFetch/fetch) (accessible via khanFetch) instead of `$.ajax`.

For more information on khanFetch, see the [javascript style guide](https://github.com/Khan/style-guides/blob/master/style/javascript.md#use-khanfetch-instead-of-ajaxgetpostgetjson).

## Reuse standard components.

If possible, re-use existing components, especially low-level, pure
components that emit HTML directly. If you write a new such one, and
it finds a use in a different project, put it in a shared location
such as the react.js package.

The standard shared location for useful components that have been
open sourced is the `react-components.js` package in
`javascript-packages.json`. This includes components such as these:

- `SetIntervalMixin` - provides a setInterval method so something can be
  done every x milliseconds
- `$_` - the i18n wrapper to allow for translating text in React.
- `TimeAgo` - “five minutes ago”, etc - this replaces $.timeago

Reusable components that have not (yet) been open sourced are in the
(poorly named) `react.js` package. This include components such as
these:

- `KUIButton` - render a Khan Academy styled button.
- `Modal` - create a modal dialog.

**[⬆ back to top](#table-of-contents)**


## CSS are modules!

We use CSS modules everywhere. CSS modules are great because they provide
scope to CSS and allow us to create compartmentalized styles that don't
leak to global scope. Here are our good practices of doing CSS modules:

## 80 columns, soft tabs of 2 spaces

Keep your code lines under 80 columns wide. This helps when opening multiple splits.
Use soft tabs of 2 spaces to save some space! :stuck_out_tongue:

## Camel case instead of dash-case for class names

With CSS modules, camel case makes much more sense:

<table>
<thead>
<th colspan="2"><strong>GOOD</strong></th>
</thead>
<thead>
<th><code>lib/components/Input/index.js</code></th>
<th><code>lib/components/Input/style.css</code></th>
</thead>
<tbody>
<tr>
<td>

```js
import style from './style.css'

const Item = ({ children }) =>
  <li className={style.circleBullet}>
    {children}
  </li>

export default Item
```

</td>
<td>

```css
.circleBullet {
  list-style-type: disc;
}
```

</td>
</tr>
</tbody>
</table>

**[⬆ back to top](#table-of-contents)**

## Never use ID and tag name as root selectors!

Using ID and tag name at the selector's root makes the rule to be applied
globally.

<table>
<thead>
<th colspan="2"><strong>GOOD</strong></th>
</thead>
<thead>
<th><code>lib/components/Item/index.js</code></th>
<th><code>lib/components/Item/style.css</code></th>
</thead>
<tbody>
<tr>
<td>

```js
import style from './style.css'

const Item = ({ title, thumbnail }) =>
  <div className={style.container}>
    <img src={thumbnail} alt={title} />
  </div>

export default Item
```

</td>
<td>

```css
.container > img {
  background-color: #CCCCCC;
}
```

</td>
</tr>
</tbody>
<th colspan="2"><strong>BAD</strong></th>
</thead>
<thead>
<th><code>lib/components/Item/index.js</code></th>
<th><code>lib/components/Item/style.css</code></th>
</thead>
<tbody>
<tr>
<td>

```js
import style from './style.css'

const Item = ({ title, thumbnail }) =>
  <div className={style.container}>
    <img src={thumbnail} alt={title} />
  </div>

export default Item
```

</td>
<td>

```css
img {
  background-color: #CCCCCC;
}
```

</td>
</tr>
</tbody>
</table>

**[⬆ back to top](#table-of-contents)**

## When using multiple selectors, give each selector its own line

Organize one selector per line, even when placing all of them at the same line doesn't
exceed 80 columns.

<table>
<thead>
<th><strong>GOOD</strong></th>
<th><strong>BAD</strong></th>
</thead>
<tbody>
<tr>
<td>

```css
.container > img,
.container > div,
.container > section {
  background-color: #CCCCCC;
}
```

</td>
<td>

```css
.container > img, .container > div, .container > section {
  background-color: #CCCCCC;
}
```

</td>
</tr>
</tbody>
</table>

**[⬆ back to top](#table-of-contents)**

## Break lines in CSS function arguments

Sometimes, not to exceed the 80 columns limit, you need to break lines. While at it, be sure to do it right after the colon, and keep at one argument per line.

<table>
<thead>
<th><strong>GOOD</strong></th>
<th><strong>BAD</strong></th>
</thead>
<tbody>
<tr>
<td>

```css
.container {
  background-color:
    linear-gradient(
      0deg,
      var(--color-light-yellow-12),
      var(--color-light-yellow-10),
    );
}
```

</td>
<td>

```css
.container {
  background-color: linear-gradient(0deg, --color-light...
}

.container {
  background-color: linear-gradient(
    0deg, var(--color-light-yellow-12), var(--color-lig...
}
```

</td>
</tr>
</tbody>
</table>

**[⬆ back to top](#table-of-contents)**

## When writing rules, be sure to

* Put a space before the opening brace `{`
* In properties put a space after (but not before) the `:` character
* Put closing braces `}` of rule declarations on a new line
* Leave **ONE** blank line in between rule declarations

<table>
<thead>
<th><strong>GOOD</strong></th>
<th><strong>BAD</strong></th>
</thead>
<tbody>
<tr>
<td>

```css
.container {
  font-size: 12pt;
}

.thumbnail {
  width: 160px;
  height: 90px;
}
```

</td>
<td>

```css

.container{
  font-size:12pt;}
.thumbnail{
  width:160px;
  height:90px;}

```

</td>
</tr>
</thead>
<tbody>
</table>

**[⬆ back to top](#table-of-contents)**

## CSS Design Patterns

## The parent constrains the child

Leaf components shouldn't constrain width or height (unless it makes
sense). That said, most components should default to fill the parent:

<table>
<thead>
<th colspan="2"><strong>GOOD</strong></th>
</thead>
<thead>
<th><code>lib/components/Input/index.js</code></th>
<th><code>lib/components/Input/style.css</code></th>
</thead>
<tbody>
<tr>
<td>

```js
import style from './style.css'

const Input = ({ children }) =>
  <input className={style.input}>
    {children}
  </input>

export default Input
```

</td>
<td>

```css
.input {
  box-sizing: border-box;
  padding: 10px;
  width: 100%;
}
```

</td>
</tr>
</tbody>
</table>

**[⬆ back to top](#table-of-contents)**

## The parent doesn't assume the child's structure

Sometimes we don't want to fill the whole width by default. An example is
the button component, which we want to resize itself based on title width.

In this cases, we should allow the parent component to inject styles into
the child component's container. The child is responsible for choosing where
parent styles are injected.

For merging styles, always use [`classnames`][classnames] package. The
rightmost arguments overrides the leftmost ones.

<table>
<thead>
<th colspan="2"><strong>GOOD</strong></th>
</thead>
<thead>
<th><code>lib/components/Button/index.js</code></th>
<th><code>lib/components/Button/style.css</code></th>
</thead>
<tbody>
<tr>
<td>

```js
import classNames from 'classnames'
import style from './style.css'

const Button = ({ children, className }) =>
  <button className={classNames(style.button, className)}>
    {children}
  </button>

export default Button
```

</td>
<td>

```css
.button {
  box-sizing: border-box;
  padding: 10px;
  width: 100%;
}
```

</td>
</tr>
</tbody>
</table>

**[⬆ back to top](#table-of-contents)**

## Components never leak margin

All components are self-contained and their final size should never suffer
margin leakage! This allows the components to be much more reusable!

<table>
<thead>
  <th><strong>BAD</strong></th>
  <th><strong>GOOD</strong></th>
</thead>
<tbody>
<tr>
<td>

```
|--|-content size-|--| margin
 ____________________
|   ______________   | | margin
|  |              |  |
|  |              |  |
|  |              |  |
|  |______________|  |
|____________________| | margin

|---container size---|
```

</td>

<td>

```

   |-content size-|
    ______________
   |              |
   |              |
   |              |
   |______________|



```

</td>
</tr>
</tbody>
</table>

**[⬆ back to top](#table-of-contents)**

### The parent spaces the children

When building lists or grids:

* Build list/grid items as separate components
* Use the the list/grid container to space children
* To space them horizontally, use `margin-left`
* To space them vertically, use `margin-top`
* Select the `first-child` to reset margins

<table>
<thead>
<th colspan="2"><strong>GOOD</strong></th>
</thead>
<thead>
<th><code>lib/containers/Reviews/index.js</code></th>
<th><code>lib/containers/Reviews/style.css</code></th>
</thead>
<tbody>
<tr>
<td>

```js
import style from './style.css'

const Reviews = ({ items }) =>
  <div className={style.container}>
    {items.map(item =>
      <img src={item.image} alt={item.title} />
    )}
  </div>

export default Reviews
```

</td>
<td>

```css
.container > img {
  margin-left: 10px;
}

.container > img:first-child {
  margin-left: unset;
}
```

</td>
</tr>
</tbody>
</table>

**[⬆ back to top](#table-of-contents)**

## Nested classes aren't for providing scope

CSS modules already provides us scope. We don't need to use nested classes
for providing scope isolation. Use nested class selectors for modifying
children based on parent class. A use case is when a component is in
error or success state:

<table>
<thead>
<th colspan="2"><strong>BAD</strong></th>
</thead>
<thead>
<th><code>lib/components/Button/index.js</code></th>
<th><code>lib/components/Button/style.css</code></th>
</thead>
<tbody>
<tr>
<td>

```js
import style from './style.css'

const Button = ({ children }) =>
  <button className={style.button}>
    <img className={style.icon} />
    {children}
  </button>

export default Button
```

</td>
<td>

```css
.button {
  box-sizing: border-box;
  padding: 10px;
  width: 100%;
}

.button .icon {
  width: 22px;
  height: 22px;
}
```

</td>
</tr>
</tbody>
<thead>
<th colspan="2"><strong>GOOD</strong></th>
</thead>
<tbody>
<thead>
<th><code>lib/components/Input/index.js</code></th>
<th><code>lib/components/Input/style.css</code></th>
</thead>
<tbody>
<tr>
<td>

```js
import style from './style.css'

const Input = ({ value, onChange, error }) =>
  <div className={classNames({ [style.error]: error })}>
    <input onChange={onChange} />
    <p>{error}</p>
  </div>

export default Input
```

</td>
<td>

```css
.error p {
  color: red;
  display: unset;
}
```

</td>
</tr>
</tbody>
</table>

**[⬆ back to top](#table-of-contents)**

## Variables, lots of variables!

We encourage the "variabilification". Always define variables to increase
reuse and make styles more consistent. The CSS4 specification defines a way
to declare native variables. We adopted them as the standard.

To define a variable accessible globally:

<table>
<thead>
<th colspan="2"><strong>GOOD</strong></th>
</thead>
<thead>
<th><code>app/App/variables.css</code></th>
<th><code>app/components/Button/styles.css</code></th>
</thead>
<tbody>
<tr>
<td>

```css
:root {
  --color-green-1: #6CCFAE;
  --color-green-2: #6B66B5;
  --color-green-3: #AAC257;
  --color-green-4: #68B5C1;
}
```

</td>
<td>

```css
.container {
  background-color:
    linear-gradient(
      0deg,
      var(--color-green-1),
      var(--color-green-2)
    );
}
```

</td>
</tr>
</tbody>
</table>

**[⬆ back to top](#table-of-contents)**

# Next.js Best Practices for Excellence

Next.js is a powerful framework that enables developers to build performant and scalable web applications. To make the most out of Next.js, it’s essential to follow best practices that ensure code quality, maintainability, and optimal performance. Here are some Next.js best practices to help you achieve excellence in your projects:

## Next.js Lazy Loading

In Next.js, there’s a neat technique called lazy loading. It means that instead of bringing everything onto the webpage all at once, things only show up when you really need them. This helps the webpage use less data and load faster.

Next.js makes this happen using something called dynamic imports. Think of it like getting deliveries – you only ask for a package when you’re ready to use it, not all of them at once. By doing this, you can split your website’s code into smaller parts. Each part only shows up when it’s actually required. This makes your webpage start up faster because it doesn’t have to load everything from the beginning. It’s like setting up your webpage piece by piece instead of all at the same time.

**[⬆ back to top](#table-of-contents)**

## Next.js Code Splitting with `next/dynamic`

Next.js code splitting is a technique used to split the JavaScript code of a Next.js application into smaller chunks, allowing the browser to load only the necessary code for each page or component.

Next.js uses automatic code splitting by default. When you build your Next.js application, it analyzes your pages and components and generates separate bundles for each one. These bundles are then loaded on-demand as the user navigates through the application.

`next/dynamic` is a feature offered by Next.js that allows you to import components dynamically. This is useful when you want to load a component only when it’s needed, such as when the user scrolls to a certain point on the page. To use `next/dynamic`, follow these steps:

1. Import the `dynamic` function from `next/dynamic` in your Next.js component file:

    ```javascript
    import dynamic from 'next/dynamic';
    ```

2. Wrap the component you want to dynamically load with the `dynamic` function:

    ```javascript
    const DynamicComponent = dynamic(() => import('./YourComponent'));
    ```

3. Render the `DynamicComponent` in your component’s JSX:

    ```javascript
    <DynamicComponent />
    ```

That’s it! Now, the `YourComponent` will be lazy loaded and rendered only when it’s needed.

You can also pass additional configuration options to the `dynamic` function. For example, you can specify a loading component to be shown while the `DynamicComponent` is being loaded:

```javascript
const DynamicComponent = dynamic(() => import('./YourComponent'), {
  loading: () => <div>Loading...</div>,
});
```

Additionally, you can configure other options like `ssr` (server-side rendering), `ssg` (static site generation), and `noSsr` (disable server-side rendering).

**[⬆ back to top](#table-of-contents)**

## Lazy Loading of Images

Next.js provides a component called `Image` that makes it easy to implement lazy loading of images. The `Image` component automatically optimizes and lazy loads images based on the viewport of the user’s device.

To use the `Image` component, follow these steps:

1. Import the `Image` component in your Next.js page or component file:

    ```javascript
    import Image from 'next/image';
    ```

2. Replace the `img` tag with the `Image` component and specify the `src` and `alt` attributes:

    ```javascript
    <Image src="/path/to/image.jpg" alt="Description of the image" />
    ```

3. You can specify the `width` and `height` attributes of the image. This helps Next.js optimize the image and generate multiple sizes for responsive layouts:

    ```javascript
    <Image src="/path/to/image.jpg" alt="Description of the image" width={500} height={300} />
    ```

That’s it! Next.js will take care of lazy loading the image and optimizing it for performance. The `Image` component also provides additional features like automatic responsive layouts, priority loading, and placeholder images.

If you want to learn about chart libraries using React with Next.js, you should go through the React chart libraries guide that we’ve published previously.

**[⬆ back to top](#table-of-contents)**

## Using Built-in Components

In Next.js, there are several built-in components that provide useful functionality out of the box. Here are some commonly used ones along with their use cases and code examples:

### Image Component

The `Image` component allows optimized image loading and lazy loading, improving performance and user experience. It automatically optimizes images based on the device and network conditions.

```javascript
import Image from 'next/image';

const MyComponent = () => (
  <div>
    <Image src="/path/to/image.jpg" alt="Description" width={500} height={300} />
  </div>
);
```

### Link Component

The `Link` component is used for client-side navigation in Next.js applications. It ensures that navigation between pages is faster by pre-fetching the necessary data.

```javascript
import Link from 'next/link';

const MyComponent = () => (
  <div>
    <Link href="/about">
      About
    </Link>
  </div>
);
```

### Script Component

The `Script` component is used to load external scripts into your Next.js application. It ensures that the scripts are loaded asynchronously and won’t block the rendering of the page.

```javascript
import Script from 'next/script';

export default function MyApp({ Component, pageProps }) {
  return (
    <>
      <Component {...pageProps} />
      <Script src="https://example.com/script.js" />
    </>
  );
}
```

This script will load and execute when any route in your application is accessed. Next.js will ensure the script will only load once, even if a user navigates between multiple pages.

### Head Component

The `Head` component allows you to modify the `<head>` tag of the document. It is useful for adding meta tags, managing the document title, and including external stylesheets or scripts.

```javascript
import Head from 'next/head';

function IndexPage() {
  return (
    <div>
      <Head>
        <title>My page title</title>
      </Head>
      <p>Hello world!</p>
    </div>
  );
}

export default IndexPage;
```

To avoid duplicate tags in your head you can use the `key` property, which will make sure the tag is only rendered once, as in the following example:

```javascript
import Head from 'next/head';

function IndexPage() {
  return (
    <div>
      <Head>
        <title>My page title</title>
        <meta property="og:title" content="My page title" key="title" />
      </Head>
      <Head>
        <meta property="og:title" content="My new title" key="title" />
      </Head>
      <p>Hello world!</p>
    </div>
  );
}

export default IndexPage;
```

These built-in components in Next.js provide convenient ways to handle common tasks and improve the performance and user experience of your application.

**[⬆ back to top](#table-of-contents)**

## Use CSS Modules

CSS Modules are a technique for localizing the scope of CSS class names in your web applications. They provide a way to encapsulate styles and prevent them from conflicting with each other when building complex user interfaces. CSS Modules are particularly useful in projects where multiple developers are working on different parts of the application, as they reduce the risk of inadvertently affecting styles in other components.

Here’s a Next.js example of how to use CSS Modules:

1. Open or create `styles.module.css` and add some CSS code:

    ```css
    /* styles.module.css */
    .button {
      background-color: blue;
      color: white;
      padding: 10px 20px;
      border: none;
      cursor: pointer;
    }
    ```

2. Create a new React component that uses the CSS Module:

    ```javascript
    import styles from '../styles/styles.module.css';

    export default function Home() {
      return (
        <div>
          <button className={styles.button}>Click me</button>
        </div>
      );
    }
    ```

In this example, the `styles.button` class is imported from the `styles.module.css` file using the `styles` object. This allows you to use the CSS classes defined in the module as properties of the `styles` object. This approach ensures that the class names are scoped to the component and won’t clash with global styles.

**[⬆ back to top](#table-of-contents)**

## Caching Data in Next.js

Caching data is an effective technique to improve the performance and user experience of Next.js applications. By storing frequently accessed data in a cache, subsequent requests can be served faster, reducing the load on the server and improving overall performance. Next.js provides various methods and strategies to implement caching in your application.

### Client-Side Caching

Next.js utilizes client-side caching to store and reuse data fetched from APIs or server-side rendering. This caching mechanism reduces the need to make repetitive API calls, resulting in faster page rendering and improved user experience.

To implement client-side caching in Next.js, you can take advantage of the SWR library. SWR is a powerful data fetching library that provides caching, revalidation, and deduplication of requests. Here’s a Next.js example of how to use SWR for caching data:

```javascript
import useSWR from 'swr';

const fetcher = (url) => fetch(url).then((res) => res.json());

function MyComponent() {
  const { data } = useSWR('/api/data', fetcher);

  if (!data) {
    return <div>Loading...</div>;
  }

  return (
    <div>
      {data.map((item) => (
        <

div key={item.id}>{item.name}</div>
      ))}
    </div>
  );
}
```

In the example above, the `useSWR` hook is used to fetch data from the `/api/data` endpoint. The `fetcher` function is responsible for performing the actual API call. The fetched data is automatically cached by SWR, and subsequent renders of the component will reuse the cached data until it expires.

### Server-Side Caching

By default, Next.js automatically caches the returned values of `fetch` in the Data Cache on the server. This means that the data can be fetched at build time or request time, cached, and reused on each data request.

```javascript
// 'force-cache' is the default, and can be omitted
fetch('https://...', { cache: 'force-cache' })
```

`fetch` requests that use the POST method are also automatically cached. Unless it’s inside a Route Handler that uses the POST method, then it will not be cached.

If you are using Next.js 12 or an older version, here’s an example of how to use `getServerSideProps` for server-side caching:

```javascript
// pages/index.js

import React from 'react';

function HomePage({ data }) {
  return (
    <div>
      <h1>Server Side Caching Example</h1>
      <ul>
        {data.map((item) => (
          <li key={item.id}>{item.title}</li>
        ))}
      </ul>
    </div>
  );
}

export async function getServerSideProps() {
  // Fetch data from an API or any other source
  const response = await fetch('https://api.example.com/data');
  const data = await response.json();

  // Cache the data for 10 seconds
  const maxAge = 10;
  const cacheControl = `public, max-age=${maxAge}`;

  return {
    props: {
      data,
    },
    // Set the cache control header
    headers: {
      'Cache-Control': cacheControl,
    },
  };
}

export default HomePage;
```

In the above example, the `getServerSideProps` function fetches data from an API and sets the `Cache-Control` header to cache the data for 10 seconds. The fetched data is then passed as props to the `HomePage` component.

Server-side caching is just one approach to improving performance in Next.js applications. You can also use client-side caching libraries like SWR to cache data on the client side.

**[⬆ back to top](#table-of-contents)**

## Use Route Handlers

Route Handlers allow you to create custom request handlers for a given route using the Web Request and Response APIs. They are defined in a [route.js|ts file](https://nextjs.org/docs/app/api-reference/file-conventions/route) inside the app directory.

Here is an example:

```typescript
// app/items/route.ts

import { NextResponse } from 'next/server'
 
export async function GET() {
  const res = await fetch('https://data.mongodb-api.com/...', {
    headers: {
      'Content-Type': 'application/json',
      'API-Key': process.env.DATA_API_KEY,
    },
  })
  const data = await res.json()
 
  return NextResponse.json({ data })
}

// POST Request 
export async function POST() {
  const res = await fetch('https://data.mongodb-api.com/...', {
    method: 'POST',
    headers: {
      'Content-Type': 'application/json',
      'API-Key': process.env.DATA_API_KEY,
    },
    body: JSON.stringify({ time: new Date().toISOString() }),
  })
 
  const data = await res.json()
 
  return NextResponse.json(data)
}
```

**[⬆ back to top](#table-of-contents)**

## Use Multiple Data Rendering Modes

Data fetching and rendering data on the webpage is a core part of any application. Here’s how you can fetch, cache, and revalidate data in React and Next.js:

### Fetching Data on the Server with `fetch`

Next.js extends the native [fetch Web API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API) to allow you to configure the caching and revalidating behavior for each fetch request on the server. React extends fetch to automatically memoize fetch requests while rendering a React component tree.

```typescript
async function getData() {
  const res = await fetch('https://api.example.com/...')
  // The return value is *not* serialized
  // You can return Date, Map, Set, etc.
 
  if (!res.ok) {
    // This will activate the closest `error.js` Error Boundary
    throw new Error('Failed to fetch data')
  }
 
  return res.json()
}
 
export default async function Page() {
  const data = await getData()
 
  return <main>{/* render data here */}</main>
}
```

### Revalidating Data

Revalidation is the process of purging the Data Cache and re-fetching the latest data. This is useful when your data changes and you want to ensure you show the latest information.

```typescript
fetch('https://...', { next: { revalidate: 3600 } })
```

Alternatively, to revalidate all fetch requests in a route segment, you can use the Segment Config Options:

```typescript
export const revalidate = 3600 // revalidate at most every hour
```

### Fetching Data on the Server with Third-Party Libraries

If you’re using a third-party library that doesn’t support or expose fetch (for example, a database, CMS, or ORM client), you can configure the caching and revalidating behavior of those requests using the Route Segment Config Option and React’s cache function.

```typescript
import { cache } from 'react'
 
export const revalidate = 3600 // revalidate the data at most every hour
 
export const getItem = cache(async (id: string) => {
  const item = await db.item.findUnique({ id })
  return item
})
```

### Fetching Data on the Client with Route Handlers

If you need to fetch data in a client component, you can call a Route Handler from the client. Route Handlers execute on the server and return the data to the client. This is useful when you don’t want to expose sensitive information to the client, such as API tokens.

```typescript
// app/data/route.ts

import { NextResponse } from 'next/server'
 
export async function GET() {
  const res = await fetch('https://data.mongodb-api.com/...', {
    headers: {
      'Content-Type': 'application/json',
      'API-Key': process.env.DATA_API_KEY,
    },
  })
  const data = await res.json()
 
  return NextResponse.json({ data })
}
```

### Fetching Data on the Client with Third-Party Libraries

You can also fetch data on the client using a third-party library such as SWR or React Query. These libraries provide their own APIs for memoizing requests, caching, revalidating, and mutating data.

Example using SWR:

```typescript
import useSWR from 'swr'
 
function Profile() {
  const { data, error, isLoading } = useSWR('/api/user', fetcher)
 
  if (error) return <div>failed to load</div>
  if (isLoading) return <div>loading...</div>
  return <div>hello {data.name}!</div>
}
```

**[⬆ back to top](#table-of-contents)**

## TypeScript Support

One of the best practices when working with Next.js projects is to leverage TypeScript for an enhanced development experience and improved code quality. TypeScript is a statically-typed superset of JavaScript that adds type annotations to the language. It provides several benefits that make it a best practice for Next.js projects:

### Type Safety

TypeScript introduces static typing, allowing developers to catch errors during development rather than at runtime. By specifying types for variables, function parameters, and return values, TypeScript helps identify potential bugs and provides better code completion and refactoring tools. This reduces the likelihood of runtime errors, leading to more reliable and maintainable code.

```typescript
// Example: TypeScript Type Annotation
function greet(name: string): string {
  return `Hello, ${name}!`;
}
```

### Better Tooling and IntelliSense

TypeScript integrates well with modern development tools and IDEs such as Visual Studio Code. These tools provide powerful features like IntelliSense, autocompletion, and code navigation, making it easier to write, refactor, and maintain code. TypeScript’s type system enables tools to provide accurate suggestions and catch potential errors, resulting in a more productive development experience.

### Improved Collaboration

In a collaborative project, TypeScript can greatly enhance the development process. With type annotations, developers can understand the structure and expected behavior of functions and objects without having to dive into the implementation details. This improves communication between team members and reduces the chances of misinterpreting code.

### Ecosystem and Community Support

TypeScript has gained significant popularity and has a thriving ecosystem and community. Many popular libraries and frameworks have official TypeScript support, including Next.js. This means that when using TypeScript in Next.js projects, you can take advantage of type definitions and improved interoperability with these libraries. Additionally, the TypeScript community provides helpful resources, tutorials, and support, making it easier to learn and troubleshoot.

**[⬆ back to top](#table-of-contents)**

## Enhance SEO in Next.js

To enhance SEO in a Next.js app, one effective approach is to use the [next-seo](https://www.npmjs.com/package/next-seo) package. This package provides a set of components and utilities that make it easy to add meta tags, structured data, and other SEO-related elements to your Next.js application.

To implement meta tags using [next-seo](https://www.npmjs.com/package/next-seo), you can make use of the NextSeo component provided by the package. This component allows you to define meta tags such as the title, description, and canonical URL for each page of your application.

Here’s an example of how you can implement meta tags using [next-seo](https://www.npmjs.com/package/next-seo):

```typescript
import { NextSeo } from 'next-seo';

function MyPage() {
  return (
    <>
      <NextSeo
        title="My Page"
        description="This is my awesome page"
        canonical="https://www.example.com/my-page"
      />
      {/* Rest of your page content */}
    </>
  );
}

export default MyPage;
```

### Benefits of Better SEO

- **Visibility**: SEO helps your website appear higher in search engine results. Better SEO increases the chances of your site showing up, leading to more visibility and organic traffic.
- **Organic Traffic**: Search engines like Google are major sources of traffic. Improving your SEO means you’re more likely to attract visitors who are actively looking for the content or products your website offers.
- **Credibility**: High-ranking websites often appear more credible to users. People tend to trust search engine results, so a strong presence in these results can positively impact your site’s credibility and reputation.
- **User Experience**: Many SEO practices focus on improving the structure and usability of your website. This benefits not only search engines but also your visitors. A well-optimized site is easier to navigate and provides a better user experience.
- **Long-Term Benefits**: SEO is an investment that can pay off over time. While it might take time to see significant results, the efforts you put into optimizing your site can have lasting benefits.
- **Cost-Effective**: Organic traffic from search engines is essentially free. While you might invest in SEO strategies, the long-term benefits often outweigh the initial costs, making it a cost-effective marketing approach.
- **Ad Blockers**: Many users employ ad blockers or simply ignore online ads. Having a strong organic presence through effective SEO ensures that your website still gets seen even when users avoid ads.
- **Analytics and Insights**: Properly implemented SEO often comes with analytics tools that provide insights into your website’s performance and user behavior. This data can help you refine your strategies and improve your site further.

**[⬆ back to top](#table-of-contents)**

## Remove Unused Dependencies & Code

The act of removing unused dependencies and files within a software project holds substantial importance for a variety of reasons:

- **Efficiency and Performance**: Unused dependencies and files can bloat the application’s package size, slowing down loading times. By eliminating these

 extraneous elements, the codebase becomes more streamlined, resulting in quicker load times and enhanced overall performance.
- **Resource Management**: Unused dependencies consume storage space within the project’s structure, and while this might seem negligible in smaller projects, it can accumulate and pose challenges in larger endeavors. Effective resource management is essential for maintaining a well-organized and clutter-free codebase.
- **Security**: Each dependency introduced into a project carries potential security risks. By removing unused dependencies, the attack surface is reduced, minimizing vulnerabilities and enhancing the application’s overall security posture.

Use the [depcheck](https://www.npmjs.com/package/depcheck) package to find unused dependencies in your project, and use [unimported](https://www.npmjs.com/package/unimported) to remove all the unimported files.

**[⬆ back to top](#table-of-contents)**

## Deploy Your Next.js App to Vercel

Deploying your Next.js app to Vercel is a seamless and efficient way to bring your website or application to life. Vercel, a cloud platform for static sites and serverless functions, is the perfect choice for hosting your Next.js projects. Here are a few reasons why deploying to Vercel is a great option:

### Easy Deployment Process

Vercel provides a simple and intuitive deployment process for Next.js apps. With just a few clicks, you can deploy your app and have it up and running in no time. Vercel automatically handles the build and deployment process, so you can focus on developing your app without worrying about complex deployment configurations.

### Automatic Scaling

Vercel's infrastructure is designed to scale your app effortlessly. Whether you have a small personal blog or a high-traffic e-commerce website, Vercel can handle the load. With automatic scaling, your app will be able to handle increased traffic without any performance issues.

### Global Network

Vercel has a global network of edge servers that ensure fast and reliable content delivery to users worldwide. This means that your app will load quickly regardless of the user’s geographical location. With Vercel, you can provide a smooth and optimized user experience to your visitors.

### Serverless Functions

Vercel supports serverless functions, allowing you to build and deploy serverless APIs alongside your Next.js app. This enables you to create dynamic and interactive features without the need for a separate backend infrastructure.

### Custom Domains and SSL

Vercel makes it easy to connect your custom domain to your Next.js app. You can easily configure your domain settings and enable SSL certificates for secure communication. This gives your app a professional and polished look while ensuring the privacy and security of your users.

### Real-time Collaboration

Vercel provides a collaborative environment where you can work with your team members on the same project. You can easily share preview URLs and collaborate on code changes, making it a breeze to iterate and ship your app faster.

Overall, deploying your Next.js app to Vercel offers a range of benefits, including an easy deployment process, automatic scaling, global network, serverless functions, custom domains, SSL support, and real-time collaboration. With Vercel, you can focus on building your app while enjoying the power and flexibility of a reliable hosting platform.

## Client Component Placement Strategy in Next.js

To ensure optimal performance and efficient rendering in a Next.js application, it's crucial to structure your components in a way that maximizes the benefits of server-side rendering and client-side interactivity. One effective approach is to place client components as lower leaves in the component tree hierarchy. This strategy leverages Next.js's ability to pre-render pages at build time or request time while allowing dynamic components to handle interactive features on the client side.

### Why Place Client Components as Lower Leaves

Placing client components, such as those utilizing dynamic data fetching or state management, as lower leaves in the component tree offers several advantages:

- **Enhanced Initial Page Load**: Components rendered on the server provide faster initial page load times as they are pre-rendered and delivered to the client.
  
- **Improved SEO and Accessibility**: Server-rendered content is accessible to search engines and users with JavaScript disabled, ensuring better SEO performance and accessibility compliance.

- **Progressive Enhancement**: By loading basic content server-side and enhancing it with client-side interactivity, you provide a smooth user experience that gracefully degrades for users with slower connections or less capable devices.

### Example Implementation

```jsx
import React from 'react';
import { useEffect, useState } from 'react';

const DynamicContent = () => {
  const [data, setData] = useState([]);

  useEffect(() => {
    fetchData();
  }, []);

  const fetchData = async () => {
    // Example: Fetch data dynamically on the client side
    const response = await fetch('https://api.example.com/data');
    const newData = await response.json();
    setData(newData);
  };

  return (
    <div>
      {data.map((item) => (
        <div key={item.id}>{item.name}</div>
      ))}
    </div>
  );
};

export default DynamicContent;
```

In this example, `DynamicContent` fetches data dynamically on the client side, making it suitable for placement as a lower leaf component in a Next.js application. This ensures that server-side rendering optimizes initial page load performance while maintaining flexibility for client-side interactions.