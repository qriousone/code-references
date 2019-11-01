# Methods
## Java
```java
public MyClass {
    // method
    public void showMessage(final String message) {
        System.out.print(message);
    }
    // method with return
    public String showMessage(final String message) {
        System.out.print(message);
        return message;
    }
}

// call
MyClass myClassObj = new MyClass();
myClassObj.showMessage("Hello");
```
Java methods must be located inside a Java class. Parameters must be prefixed with a data type. Parameter values can be change but should be done carefully because it could lead to confusing code.
- **void** tells the compiler that a function will not be returning any value after it is executed.
- **final** *(optional — not often used)* parameter cannot be changed. Values inside an object reference can still be changed.
- **return** statement determines what value returns by the method. Requires return-type to be define before the method's namespace

### method overloading
```java
public MyClass {
    public void showMessage(final String message) {
        System.out.print(message);
    }
    public void showMessage(final String greeting, final String name) {
        System.out.print(message + " " + name);
    }
}
// call
MyClass myClassObj = new MyClass();
myClassObj.showMessage("Hello"); // Hello
myClassObj.showMessage("Hello", "Maurice"); // Hello Maurice
```
Java allows for method overloading. A method name can be meaningful for a couple sets of similar but different operations that perform the same single action.

**Different types of overloading**:
- Difference in the number of parameters
- Difference in data type(s)
- Difference in sequence of data type(s)
- **Type promotion** smaller size data type is promoted to data type of bigger size when there's no matching argument type. Example below shows the float value got promoted to double type because of no matching type.
    ```java
    public MyClass {
        public void showMessage(int a, double b) {
            System.out.print("Method A");
        }
        public void showMessage(int a, double b, double c) {
            System.out.print("Method B");
        }
    }
    // call
    MyClass myClassObj = new MyClass();
    myClassObj.showMessage(100, 20.67f); // Method A
    ```
    **Byte size of float and double data types**  
    
    Floating point numbers (Aka floating point literals or real numbers). `Float` and `double` supports decimals. Floats are use for precision because it allows for more numbers. Float data type is a single numbers that occupies 4 bytes or 32 bits in computer memory. A bit stores a single value (0 or 1). Bits are grouped in groups of 8 to make one byte. Double data type is a double precision format that occupies 8 bytes of 64 bits in computer memory — twice the number of bytes occupied by floats. A float data type stores a decimal value with no more than 7 total digits of precision. 12.123456f can be saved as a float but 1.123456789f can't. Decimals will be stored as a double if not appended with an 'f'. Double data types stores up to 16 digits of precision.

## JavaScript
```javascript
    // es5 function expression
    var showMessage = function(message) {
        message = (typeof message !== 'undefined') ? message : 'hello world';
        console.log(message);
        return message;
    };
    // es5 function declaration
    function showMessage(message) {
        message = (typeof message !== 'undefined') ? message : 'hello world';
        console.log(message);
    }
    // es6 arrow function
    const showMessage = (message = 'hello world') => {
        console.log(message);
        return message;
    }
    // call
    showMessage('hello');
```
### function expression
Is set to a variable, because of this it must be terminated with a semicolon (In JS, semicolon is use to terminate a statement — sometimes optional because of automatic-semicolon-insertion (ASI)). The function has to be created before the function is used.
- **default parameter** requires a check in the function body. The type of parameter checks if an argument is passed to it. If not,
- **return** statement ends function execution and specifies a value to be returned to the function caller.
### function declaration
a function declaration is prefixed with the `function` keyword. The function can be called anytime, before or after its creation.
### arrow function (aka 'fat arrow')
is also a function expression. Option to omit both `function` and `return` keywords and curly brackets (as they are implicit in arrow functions).  
- **default parameter** can simply be defined in the function head by assigning the default value to the parameter.
- **`=>`** In a concise body, only an expression is specified, which becomes the implicit return value. In a block body, you must use an explicit return statement.
    ```javascript
    // concise body syntax, implied "return"
    var func = x => x * x;                  
    // with block body, explicit "return" needed
    var func = (x, y) => { return x + y; };
    ```
    --  
    *MDN contributors. "Arrow function expressions" MDC web docs, MDN contributors, Oct 25, 2019,*  
    *https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions*
