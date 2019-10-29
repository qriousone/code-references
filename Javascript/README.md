# Javascript

## Class Inheritance
Instances inherit from classes (like a blueprint — a description of the class), and create sub-class relationships: hierarchical class taxonomies. Instances are typically instantiated via constructor functions with the `new` keyword. Class inheritance may or may not use the `class` keyword from ES6.

**When is classical inheritance an appropriate choice?**
The answer is never, or almost never. Certainly never more than one level. Multi-level class hierarchies are an anti-pattern. I’ve been issuing this challenge for years, and the only answers I’ve ever heard fall into one of several common misconceptions. More frequently, the challenge is met with silence.

---

Elliott, Eric. "10 Interview Questions Every JavaScript Developer Should Know. Medium, Medium, Oct 2, 2015,
https://medium.com/javascript-scene/10-interview-questions-every-javascript-developer-should-know-6fa6bdf5ad95


## Closures
A closure is an inner function that has access to the outer (enclosing) function’s variables—scope chain. The closure has three scope chains: it has access to its own scope (variables defined between its curly brackets), it has access to the outer function’s variables, and it has access to the global variables.

---

Bovell, Richard. "Understand JavaScript Closures With Ease." JavaScript Is Sexy, JavaScript Is Sexy, Feb 2, 2013, http://javascriptissexy.com/understand-javascript-closures-with-ease/

## Coercion
Coercion is the term that is used for unexpected type casting in JavaScript. Coercion refers to those not-obvious type casts that happen as a side-effect of different operations.

---
Kondov, Alexander. "Understanding JS: Coercion." Hackernoon, Hackernoon, Oct 14, 2019,
https://hackernoon.com/understanding-js-coercion-ff5684475bfc

## Currying
Binding some of the arguments to the first function invoke, so that those values are fixed for the next invocation.
```javascript
let dragon =
    name =>
        size =>
            element =>
                name + ' is a ' +
                size + ' dragon that breathes ' +
                element + '!'
// This allows this function with a a specific argument to be reused
let fluffykinsDragon = dragon('fluffykins');
let tinyDragon = fluffykinsDragon('tiny');
```

---

Brainwave, Kristina. "Currying in JavaScript." Medium, Medium, Oct 11, 2013,
https://medium.com/@kbrainwave/currying-in-javascript-ce6da2d324fe

## Debounce and Throttle
**Debouncing** enforces that a function not be called again until a certain amount of time has passed. Time resets on trigger.

**Throttling** Enforces a maximum number of times a function can be called over time.

---
Coyier, Chris. "The Difference Between Throttling and Debouncing." CSS Tricks, CSS Tricks, Jun 10, 2015,
https://css-tricks.com/the-difference-between-throttling-and-debouncing/


## Declarative Programming
Tells the machine WHAT to do it

## Factory Functions
Functions that create objects and return them. Simpler and less convoluted than classes. Variables are properly private to the factory function which isn’t in a class. Better off using factory rather than classes.

---

Johansson, Mattias. "Factory Functions in JavaScript." YouTube, Fun Fun Function, Sep 14, 2015,
https://www.youtube.com/watch?v=ImwrezYhw4w

## Functional Programming
Functional programming is the process of building software by composing pure functions, avoiding shared state, mutable data, and side-effects. Functional programming is declarative rather than imperative, and application state flows through pure functions. Contrast with object oriented programming, where application state is usually shared and colocated with methods in objects.

---

Elliot, Eric. "Master the JavaScript Interview: What is Functional Programming?" Medium, Medium, Jan 3, 2017,
https://medium.com/javascript-scene/master-the-javascript-interview-what-is-functional-programming-7f218c68b3a0
