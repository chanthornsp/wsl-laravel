# PHP for Beginners (2023)

## What is PHP?

PHP is a server-side scripting language that is used to create dynamic web pages.

## First PHP Tag

- PHP tags start with `<?php` and end with `?>`

```php
<?php
    echo "Hello World!";
?>
```

## Variables

- Variables start with `$` sign
- Variables are case sensitive (`$name` is different from `$NAME`)
- Variables can't start with a number
- Variables can't contain spaces
- Variables can only contain letters, numbers and underscores
- Variables can't contain special characters like `!@#$%^&*()`

```php
<?php
    $name = "John";
    $age = 25;
    echo $name;
    echo $age;
?>
```

### Single quotes vs Double quotes

- Example of single quotes

```php
<?php
    $name = "John";
    echo 'My name is $name';
?>
```

- Output: `My name is $name`

- Example of double quotes

```php
<?php
    $name = "John";
    echo "My name is $name";
?>
```

- Output: `My name is John`

## [Data Types](dataType.md)

- String
- Integer
- Float
- Boolean
- Array
- Object
- NULL
- Resource

## Conditional Statements

- If Statement
- If...Else Statement
- If...ElseIf...Else Statement
- Switch Statement

### If Statement

- The `if` statement is a conditional statement that allows you to execute block of code if a specified condition is `TRUE`

```php
<?php
    $age = 25;
    if ($age > 18) {
        echo "You can vote!";
    }
?>
```

### If...Else Statement

```php
<?php
    $age = 15;
    if ($age > 18) {
        echo "You can vote!";
    } else {
        echo "You can't vote!";
    }
?>
```

### If...ElseIf...Else Statement

```php
<?php
    $age = 15;
    if ($age > 18) {
        echo "You can vote!";
    } elseif ($age == 18) {
        echo "You are 18 years old!";
    } else {
        echo "You can't vote!";
    }
?>
```

### Switch Statement

The `switch` statement is used when you have a single expression that you want to compare to multiple possible values. It provides a cleaner way to handle multiple conditions based on the same variable.

```php
<?php
    $favColor = "red";
    switch ($favColor) {
        case "red":
            echo "Your favorite color is red!";
            break;
        case "blue":
            echo "Your favorite color is blue!";
            break;
        case "green":
            echo "Your favorite color is green!";
            break;
        default:
            echo "Your favorite color is neither red, blue, nor green!";
    }
?>
```

## Arrays

- `array` is a special type of variable that can hold multiple values in a single variable.

```php
<?php
    $names = ["John", "David", "Amy"];
    echo $names[0];
?>
```

- Multidimensional array

```php
<?php
    $books = [
        ["Harry Potter", "J. K. Rowling", 200],
        ["Lord of the Rings", "J. R. R. Tolkien", 150],
        ["The Hobbit", "J. R. R. Tolkien", 100]
    ];
    echo $books[0][0];
?>
```

- Associative Arrays

```php
<?php
    $book = [
        [
            "title" => "Harry Potter",
            "author" => "J. K. Rowling",
            "pages" => 200
        ],
        [
            "title" => "Lord of the Rings",
            "author" => "J. R. R. Tolkien",
            "pages" => 150
        ],
        [
            "title" => "The Hobbit",
            "author" => "J. R. R. Tolkien",
            "pages" => 100
        ]
    ];
    echo $book[0]["title"];
    echo $book[0]["author"];
    echo $book[0]["pages"];
?>
```

## Loops

- `foreach` loop is used to iterate through each element of an array

```php
<?php
    foreach ($books as $book){
      echo $book['title'];
      echo $book['author'];
      echo $book['pages'];
    }
```

## Functions

- A function is a block of code that performs a specific task
- A function will not execute automatically when a page loads
- A function will be executed by a call to the function

```php
<?php
    function sayHello() {
        echo "Hello World!";
    }
    sayHello();
```

- Function with parameters

```php
<?php
    function sayHello($name) {
        echo "Hello $name!";
    }
    sayHello("John");
?>
```

## Classes and Objects

- A class is a template for objects
- An object is an instance of a class

```php
<?php
    class Book {
        public $title;
        public $author;
        public $pages;

        function __construct($aTitle, $aAuthor, $aPages) {
            $this->title = $aTitle;
            $this->author = $aAuthor;
            $this->pages = $aPages;
        }

    }
    $book1 = new Book("Harry Potter", "J. K. Rowling", 200);
    echo $book1->title;
    echo $book1->author;
    echo $book1->pages;

    $book2 = new Book("Lord of the Rings", "J. R. R. Tolkien", 150);
    echo $book2->title;
    echo $book2->author;
    echo $book2->pages;
?>
```

## Interfaces

- An interface is a collection of abstract methods
- An interface can't be used directly
- An interface needs to be implemented by a class

```php
<?php
    interface Animal {
        public function makeSound();
    }

    class Cat implements Animal {
        public function makeSound() {
            echo "Meow";
        }
    }

    $cat = new Cat();
    $cat->makeSound();
```
