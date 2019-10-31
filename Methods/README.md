# Methods
## JavaScript
```js
    // es5 function expression
    var showMessage = function(message) {
        message = (typeof message !== 'undefined') ? message : 'hello world';
        console.log(message)
    };
    // es5 function declaration
    function showMessage(message) {
        message = (typeof message !== 'undefined') ? message : 'hello world';
        console.log(message)
    }
    // es6 arrow function
    const showMessage = (message = 'hello world') => {
        console.log(message)
    }
```
### function expression
Is set to a variable, because of this it must be terminated with a semicolon (In JS, semicolon is use to terminate a statement — sometimes optional because of automatic-semicolon-insertion (ASI)). The function has to be created before the function is used.
- **default parameter** requires a check in the function body. The type of parameter checks if an argument is passed to it. If not, parameter is assigned a default value.
### function declaration
a function declaration is prefixed with the `function` keyword. The function can be called anytime, before or after its creation.
### arrow function (aka 'fat arrow')
is also a function expression. Option to omit both `function` and `return` keywords and curly brackets (as they are implicit in arrow functions).
    - **default parameter** can simply be defined in the function head by assigning the default value to the parameter.
