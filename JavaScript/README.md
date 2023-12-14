# JavaScirpt (ES6)

## Variables

- `var` keyword (old way)

  - when you declare a variable with `var` keyword, it is scoped to the function in which it is declared
    Example:

  ```javascript
  function foo() {
    if (true) {
      var a = 1;
      console.log(a); // 1
    }
    console.log(a); // 1
  }
  ```

  -`var` keyword is function scoped

- `let` keyword

  - when you declare a variable with `let` keyword, it is scoped to the block in which it is declared
    Example:

  ```javascript
  function foo() {
    if (true) {
      let a = 2;
      console.log(a); // 2
    }
    console.log(a); // ReferenceError: a is not defined
  }
  ```

  - `let` keyword is block scoped

- `const` keyword (constant)

  - when you declare a variable with `const` keyword, it is scoped to the block in which it is declared
  - `const` keyword is block scoped
  - `const` is immutable, meaning that the value of the variable cannot be changed once it is assigned.

    Example:

    ```javascript
    const names = ["John", "Jane", "Mark"];
    names = ["Bob", "Alice"]; // TypeError: Assignment to constant variable
    ```

  - However, the properties of a `const` object can be changed

    Example:

    ```javascript
    const person = {
      name: "John",
      age: 25,
    };
    person.name = "Bob";
    person.age = 30;
    console.log(person); // {name: "Bob", age: 30}
    ```

## Arrow Functions

- Arrow is a concise way to write anonymouse functions in JavaScript
- Arrow functions was introduced in ES6

  Example:

  ```javascript
  // Normal function
  function add(a, b) {
    return a + b;
  }

  // Arrow function
  const add = (a, b) => {
    return a + b;
  };
  // or if the function body has only one statement
  const add = (a, b) => a + b;

  const numbers = [1, 2, 3, 4, 5];

  const squared = numbers.map((num) => num * num);
  console.log(squared); // [1, 4, 9, 16, 25]
  ```

## Template Literals (Template Strings)

- Template literals are string literals that allow embedded expressions
- Template literals was introduced in ES6

  Example:

  ```javascript
  const name = "John";
  const age = 25;
  console.log(`My name is ${name}. I am ${age} years old.`); // My name is John. I am 25 years old.
  ```

## Spread

Example:

```javascript
function sum(...numbers) {
  // reduce() method reduces the array to a single value
  return numbers.reduce((prev, current) => prev + current);
}

console.log(sum(1, 2, 3, 4, 5)); // 15
```

## Destructuring

- Destructuring is a convenient way of extracting multiple values from data stored in objects and arrays

Example:

```javascript
const person = {
  firstName: "John",
  lastName: "Doe",
  age: 25,
};

const { firstName, lastName, age } = person;
console.log(firstName, lastName, age); // John Doe 25
```

## Object Enhancements

- Object enhancements was introduced in ES6

Example:

```javascript
function getPerson() {
  const name = "John";
  const age = 25;

  return {
    name,
    age,
    greet() {
      console.log(`Hello, my name is ${this.name}.`);
    },
  };
}

const person = getPerson();

console.log(person.name); // John
```

## Classes

- Classes was introduced in ES6

Example:

```javascript
// old way
function Person(name, age) {
  this.name = name;
  this.age = age;
}

Person.prototype.greet = function () {
  console.log(`Hello, my name is ${this.name}.`);
};

const person = new Person("John", 25);
person.greet(); // Hello, my name is John.

// new way

class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }

  greet() {
    console.log(`Hello, my name is ${this.name}.`);
  }
}

const person = new Person("John", 25);
person.greet(); // Hello, my name is John.
```
