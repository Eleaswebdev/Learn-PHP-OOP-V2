# Learn-PHP-OOP-V2

# PHP OOP Concepts

## Table of Contents
1. [Introduction to PHP OOP](#1-introduction-to-php-oop)
2. [Classes and Objects](#2-classes-and-objects)
3. [Visibility Keywords](#3-visibility-keywords)
4. [Static Methods and Properties](#4-static-methods-and-properties)
5. [Inheritance](#5-inheritance)
6. [Namespace](#6-namespace)
7. [Traits](#7-traits)
8. [Interfaces](#8-interfaces)
9. [Choosing Between Traits and Interfaces](#9-choosing-between-traits-and-interfaces)
10. [Constants in Classes](#10-constants-in-classes)

---

## 1. Introduction to PHP OOP

Object-Oriented Programming (OOP) in PHP allows you to organize and structure your code into reusable components. It focuses on using **classes** and **objects** to encapsulate data and behaviors. OOP provides features like **encapsulation**, **inheritance**, **polymorphism**, and **abstraction**.

---

## 2. Classes and Objects

### What is a Class?

A **class** is a blueprint for creating objects. It contains **properties** (data) and **methods** (functions) that define the behavior of the objects.

### What is an Object?

An **object** is an instance of a class. It is created from a class and represents a specific entity with its own properties and behaviors.

### Example
```php
class Car {
    public $brand;
    public $color;

    // Constructor
    public function __construct($brand, $color) {
        $this->brand = $brand;
        $this->color = $color;
    }

    // Method
    public function drive() {
        echo "The {$this->color} {$this->brand} is driving.";
    }
}

// Create an object
$myCar = new Car('Toyota', 'red');
$myCar->drive();
3. Visibility Keywords
Visibility keywords control how class properties and methods can be accessed:

Public
Accessible from anywhere (inside the class, in child classes, and outside the class).
php
Copy
Edit
class Example {
    public $name = "Public Property";

    public function display() {
        echo $this->name;
    }
}

$obj = new Example();
$obj->display(); // Output: Public Property
Protected
Accessible only within the class and its child classes.
php
Copy
Edit
class ParentClass {
    protected $name = "Protected Property";

    protected function display() {
        echo $this->name;
    }
}

class ChildClass extends ParentClass {
    public function show() {
        $this->display(); // Accessing protected method
    }
}

$obj = new ChildClass();
$obj->show(); // Output: Protected Property
Private
Accessible only within the class in which it is defined. Not accessible in child classes.
php
Copy
Edit
class Example {
    private $name = "Private Property";

    private function display() {
        echo $this->name;
    }

    public function show() {
        $this->display();
    }
}

$obj = new Example();
$obj->show(); // Output: Private Property
4. Static Methods and Properties
Static methods and properties belong to the class rather than any specific object. They can be accessed without instantiating the class.

Static Property
php
Copy
Edit
class Counter {
    public static $count = 0;

    public static function increment() {
        self::$count++;
    }
}

// Access static property and method
Counter::increment();
echo Counter::$count; // Output: 1
Static Method
php
Copy
Edit
class Math {
    public static function add($a, $b) {
        return $a + $b;
    }
}

echo Math::add(5, 10); // Output: 15
5. Inheritance
Inheritance allows a class to inherit properties and methods from another class using the extends keyword.

Example
php
Copy
Edit
class Animal {
    public $name;

    public function __construct($name) {
        $this->name = $name;
    }

    public function eat() {
        echo "{$this->name} is eating.";
    }
}

class Dog extends Animal {
    public function bark() {
        echo "{$this->name} is barking.";
    }
}

$dog = new Dog('Buddy');
$dog->eat(); // Output: Buddy is eating.
$dog->bark(); // Output: Buddy is barking.
6. Namespace
Namespaces help organize your code and prevent name conflicts by grouping related classes, interfaces, and functions.

Example
php
Copy
Edit
namespace MyApp;

class User {
    public function greet() {
        echo "Hello, User!";
    }
}

// Use the namespace in another file
use MyApp\User;

$user = new User();
$user->greet(); // Output: Hello, User!
7. Traits
Traits are used to share methods or properties across multiple classes without using inheritance.

Example
php
Copy
Edit
trait Logger {
    public function log($message) {
        echo "Log: $message";
    }
}

class User {
    use Logger;
}

$user = new User();
$user->log("This is a log message."); // Output: Log: This is a log message.
8. Interfaces
An interface defines a set of methods that a class must implement.

Example
php
Copy
Edit
interface PaymentGateway {
    public function processPayment($amount);
}

class PayPal implements PaymentGateway {
    public function processPayment($amount) {
        echo "Processing payment of $amount via PayPal.";
    }
}

$payment = new PayPal();
$payment->processPayment(100); // Output: Processing payment of 100 via PayPal.
9. Choosing Between Traits and Interfaces
When to Use Traits
To share reusable code with actual implementations.
Example: Logging, utility functions.
When to Use Interfaces
To enforce a contract for specific behavior without providing implementations.
Example: Payment gateways, notification systems.
10. Constants in Classes
Constants are used to define values that do not change during the execution of a program.

Example
php
Copy
Edit
class Config {
    const VERSION = "1.0.0";

    public static function getVersion() {
        return self::VERSION;
    }
}

echo Config::VERSION; // Output: 1.0.0
echo Config::getVersion(); // Output: 1.0.0
