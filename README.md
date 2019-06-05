# University of Haifa Code Style Guide!

This is the TypeScript style guide that we use internally at University of Haifa. It is important that we keep a consistent look/feel of our code and follow the latest best practices in development environment.

## Introduction

When developing software as an organization, the value of the software produced is directly affected by the quality of the codebase. Consider a project that is developed over many years and handled/seen by many different people. If the project uses a consistent coding convention it is easier for new developers to read, preventing a lot of time/frustration spent figuring out the structure and characteristics of the code. For that purpose, we need to make sure we adhere to the same coding conventions across all of our products. This will not only help new developers, but it will also aid in quickly identifying potential flaws in the code, thereby reducing the brittleness of the code.

## General Remarks 

> - Use [Angular official Code Style Guide](https://angular.io/guide/styleguide).
> - Do not build by yourself features that already exist in Angular.
> - Mind the final size of the compiled application. Install only packages that are extremely required.
>  - There is no need for additional CSS frameworks, use only our [University of Haifa Angular Theme](https://www.npmjs.com/package/@uoh/ngx-theme).


## Browser Compatibility

- Target [evergreen browsers](https://www.techopedia.com/definition/31094/evergreen-browser) `ie >= 11`, `chrome`, `firefox`, `safari`.
- Avoid targeting older browsers `ie < 10`.

## Files

-   All TypeScript files must have a ".ts" or ".tsx" extension.
-   They should be all lower case, and only include letters, numbers, and periods.
-   It is OK (even recommended) to separate words with periods (e.g.  `my.view.html`).
-   **All files should end in a new line.**  This is necessary for some Unix systems.

## Project Structure

- Angular does not have a strict guide for the file structure. We developed our own methodology of building the project file structure.
```
├── README.md
├── angular.json
├── e2e
│   ├── protractor.conf.js
│   ├── src
│   │   ├── app.e2e-spec.ts
│   │   └── app.po.ts
│   └── tsconfig.e2e.json
├── package-lock.json
├── package.json
├── proxy
│   ├── index.js
│   └── proxy.conf.json
├── src
│   ├── app
│   │   ├── app.component.html
│   │   ├── app.component.scss
│   │   ├── app.component.ts
│   │   ├── app.module.ts
│   │   ├── pages
│   │   ├── routing
│   │   │   ├── guards
│   │   │   └── resolvers
│   │   └── shared
│   │       ├── components
│   │       ├── directives
│   │       ├── interceptors
│   │       ├── models
│   │       ├── pipes
│   │       ├── services
│   │       └── validators
│   ├── assets
│   ├── browserslist
│   ├── environments
│   │   ├── environment.prod.ts
│   │   └── environment.ts
│   ├── favicon.ico
│   ├── index.html
│   ├── karma.conf.js
│   ├── main.ts
│   ├── polyfills.ts
│   ├── styles.scss
│   ├── test.ts
│   ├── tsconfig.app.json
│   ├── tsconfig.spec.json
│   └── tslint.json
├── tsconfig.json
└── tslint.json
```

## Indentation

- The unit of indentation is two spaces.
- **Never use tabs**, as this can lead to trouble when opening files in different IDEs/Text editors. Most text editors have a configuration option to change tabs to spaces.

## Line Length

-   Lines must not be longer than 140 characters.
-   When a statement runs over 140 characters on a line, it should be broken up, ideally after a comma or operator.

## Quotes

-   Use single-quotes  `''`  for all strings, and use double-quotes  `""`  for strings within strings.
-   When you need to use an apostrophe inside a string it is recommended to use double-quotes.
-   Use template literals only when using expression interplation  `${}`

```
// bad
let greeting = "Hello World!";

// good
let greeting = 'Hello World!';

// bad
let phrase = 'It\'s Friday!';

// good
let phrase = "It's Friday!";

// bad
let html = "<div class='bold'>Hello World</div>";

// bad
let html = '<div class=\'bold\'>Hello World</div>';

// good
let html = '<div class="bold">Hello World</div>';

// bad
let template = `string text string text`;

// good
let template = `string text ${expression} string text`;
```

## Commas

-   Use trailing commas always. DO NOT USE leading commas.
-   Always use an additional trailing comma.

```
// bad
const person = {
  firstName: 'John'
, lastname: 'Smith'
, email: 'john.smith@outlook.com'
};

// bad
const person = {
  firstName: 'John',
  lastname: 'Smith',
  email: 'john.smith@outlook.com'
};

// good
const person = {
  firstName: 'John',
  lastname: 'Smith',
  email: 'john.smith@outlook.com',
};
```

## Comments

-   Comments are strongly encouraged. It is very useful to be able to read comments and understand the intentions of a given block of code.
-   Comments need to be clear, just like the code they are annotating.
-   Make sure your comments are meaningful.

The following example is a case where a comment is completely erroneous, and can actually make the code harder to read.

```
// Set index to zero.
let index = 0;
```
-   All **public functions** must have a comment block  `/**...*/`  using  [JSDoc](http://usejsdoc.org/)  style comments.
```
/**
 * Takes in a name and returns a greeting string.
 *
 * @param name The name of the greeted person.
 */
getGreeting(name: string): string {
  return 'Hello ' + name + '!';
}
```

## Class

-   All classes must have block comments  `/**...*/`  for all public variables and functions.
-   All public functions should use  [JSDoc](http://usejsdoc.org/)  style comments.
-   Functions need to have a comment explaining what the function does, and all of the input parameters need to be annotated with  `@param`.
-   The class should include a block comment containing the description of the class
-   The constructor should contain a JSDoc comment annotating any input parameters.

```
/**
 * Contains properties of a Person.
 */
class Person {
  /**
   * Returns a new Person with the specified name.
   *
   * @param name The name of the new Person.
   */
  public static GetPerson(name: string): Person {
    return new Person(name);
  }

  /**
   * @param name The name of the new Person.
   */
  constructor(public name: string) { }

  /**
   * Instructs this Person to walk for a certain amount
   * of time.
   *
   * @param millis The number of milliseconds the Person
   * should walk.
   */
  public walkFor(millis: number): void {
    console.log(this.name + ' is now walking.');

    setTimeout(() => {
      console.log(this.name + ' has stopped walking.');
    }, millis);
  }
}
```

## Inline

-   Inline comments are comments inside of complex statements (loops, functions, etc).
-   Use  `//`  for all inline comments.
-   Keep comments clear and concise.
-   Place inline comments on a newline above the line they are annotating
-   Put an empty line before the comment.

```
// bad
let lines: Array<string>; // Holds all the lines in the file.

// good
// Holds all the lines in the file.
let lines: Array<string>;

// bad
walkFor(name: string, millis: number): void {
  console.log(name + ' is now walking.');
  // Wait for millis milliseconds to stop walking
  setTimeout(() => {
    console.log(name + ' has stopped walking.');
  }, millis);
}

// good
walkFor(name: string, millis: number): void {
  console.log(name + ' is now walking.');

  // Wait for millis milliseconds to stop walking
  setTimeout(() => {
    console.log(name + ' has stopped walking.');
  }, millis);
}
```

## Todo and XXX

`TODO`  and  `XXX`  annotations help you quickly find things that need to be fixed/implemented.

-   Use  `// TODO:`  to annotate solutions that need to be implemented.
-   Use  `// XXX:`  to annotate problems the need to be fixed.
-   It is best to write code that doesn't need  `TODO`  and  `XXX`  annotations, but sometimes it is unavoidable.


## Variable Declarations

-   All variables must be declared prior to using them. This aids in code readability and helps prevent undeclared variables from being hoisted onto the global scope.
```
// bad
console.log(a + b);

let a = 2;
let b = 4;

// good
let a = 2;
let b = 4;

console.log(a + b);
```

-   Implied global variables should never be used.
-   You should never define a variable on the global scope from within a smaller scope.
```
// bad
add(a: number, b: number): number {
  // c is on the global scope!
  c = 6;

  return a + b + c;
}
```
-   Declare each variable on a newline.
-   Use  `let`  or  `const`  to declare each variable. This can save you a lot of trouble when refactoring.
```
// bad
let a = 2,
  b = 2,
  c = 4;

// good
let a = 2;
let b = 2;
let c = 4;

// bad
// b will be defined on global scope.
let a = b = 2, c = 4;
```

## Names

-   All variable and function names should be formed with alphanumeric  `A-Z, a-z, 0-9`  and underscore  `_`  charcters.

### [](https://github.com/Platypi/style_typescript#variables-modules-and-functions)Variables, Modules, and Functions

-   Variable, module, and function names should use lowerCamelCase.

### [](https://github.com/Platypi/style_typescript#use-of-var-let-and-const)Use of var, let, and const

-   Use  `const`  where appropriate, for values that never change
-   Use  `let`  everywhere else
-   Avoid using  `var`

### Interfaces

-   Interfaces should use UpperCamelCase.
-   Interfaces should be prefaced with the capital letter I.
-   Only  `public`  members should be in an interface, leave out  `protected`  and  `private`  members.
```
interface IPerson {
    firstName: string;
    lastName: string;
    toString(): string;
}
```
## === and !== Operators

-   It is better to use  `===`  and  `!==`  operators whenever possible.
-   `==`  and  `!=`  operators do type coercion, which can lead to headaches when debugging code.

## Promises
- Do not use promises in projects, only use `Observables` as denoted in the [Angular Guidelines](https://angular.io/guide/observables-in-angular). 

## Eval

-   **Never use eval**
-   **Never use the Function constructor**
-   **Never pass strings to  `setTimeout`  or  `setInterval`**

## Proxy
Use Proxy in order to avoid the CORS block (block-all-mixed-content) in the browser when developing frontend locally and the API is located on a remote server:
#### index.js:
```
const  express  =  require('express');
const  request  =  require('request');
const  app  =  express();
const  PORT  = process.env.PORT  ||  3000;
const  SERVER  =  'YOUR_API_URL';

console.log(`## Proxy initialized on http://localhost:${PORT} ##`);

app.use('/proxy',  function(req,  res)  {
  const  url  =  `${SERVER}${req.url}`;
  console.log(`Proxy to url: ${url}`);
  try  {
    req
      .pipe(request(url))
      .on('error',  err  =>  console.log(`error ${err}`))
      .pipe(res);
  }  catch (e) 
    console.log('Error: '  +  e);
  }
});
app.listen(PORT);
```

## TSLint

-   Always use a Linter

Linting your code is very helpful for preventing minor issues that can escape the eye during development. We use [TSLint](https://palantir.github.io/tslint/) for our linter.

## Prettier

-   Always use a formatter

Formatting your code is very helpful for readability. When working in teams, it is nice to be able to look at code that is in the same format across the entire application.

-   Prettier:  [https://github.com/prettier/prettier](https://github.com/prettier/prettier)
