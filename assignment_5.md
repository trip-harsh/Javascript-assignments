# Question 1:

An IIFE (Immediately Invoked Function Expression) is a JavaScript function that is executed immediately after it is defined. It is a self-invoking anonymous function that encapsulates its code within a local scope and does not pollute the global scope.

The primary reason to use an IIFE is to create a new scope for your code, keeping variables and functions within that scope private and preventing them from conflicting with variables or functions in the global scope. It helps in avoiding naming collisions and provides a way to organize code modules.

Here's an example of an IIFE in JavaScript:

```javascript

(function() {
  const message = "Hello, World!";
  console.log(message);
})();

```
In this example, we define an anonymous function inside parentheses (function(){...}), followed by an additional set of parentheses () at the end to invoke the function immediately. This creates an IIFE. Within the IIFE, we have a variable message with the value "Hello, World!". The console.log() statement inside the IIFE prints the message to the console.

# Question 2:

The bind(), call(), and apply() methods in JavaScript are used to manipulate the context (the value of this) and arguments of a function. Although they serve a similar purpose, they have some differences in how they work.

bind(): The bind() method creates a new function that has a bound context (this value) and, optionally, pre-set arguments. It does not immediately invoke the function but returns a new function that can be called later with the bound context and arguments.

Example:

```javascript
const obj = { name: 'John' };

function greet() {
  console.log(`Hello, ${this.name}!`);
}

const boundGreet = greet.bind(obj);
boundGreet(); // Output: Hello, John!
```
call(): The call() method invokes a function immediately with a specified context (this value) and individual arguments provided as separate arguments. It allows you to explicitly set the context and pass arguments one by one.

Example:

```javascript
const obj = { name: 'John' };

function greet() {
  console.log(`Hello, ${this.name}!`);
}

greet.call(obj); // Output: Hello, John!
```

apply(): The apply() method is similar to call(), but it takes the context as the first argument and an array (or an array-like object) of arguments as the second argument. It allows you to explicitly set the context and pass arguments as an array.

Example:

``` javascript
const obj = { name: 'John' };

function greet() {
  console.log(`Hello, ${this.name}!`);
}

greet.apply(obj); // Output: Hello, John!
```
The main differences between bind(), call(), and apply() are in how they handle the function execution and argument passing. While bind() returns a new function with the bound context, call() and apply() immediately invoke the function with the specified context and arguments.

# Question 3

In JavaScript, a Higher-Order Function (HOF) is a function that either takes one or more functions as arguments or returns a function as its result. HOFs treat functions as first-class citizens, allowing them to be manipulated and used like any other data type. This concept of functions accepting or returning functions is known as "higher-order programming."

The key difference between regular functions and Higher-Order Functions is that regular functions typically operate on data, performing specific operations or calculations, whereas Higher-Order Functions operate on functions themselves, enabling composition, abstraction, and the creation of more reusable and flexible code.

Here's an example to illustrate the concept of a Higher-Order Function:

```javascript

// Higher-Order Function: map()
function map(array, transform) {
  const result = [];
  for (let i = 0; i < array.length; i++) {
    result.push(transform(array[i]));
  }
  return result;
}

function double(number) {
  return number * 2;
}

const numbers = [1, 2, 3, 4, 5];
const doubledNumbers = map(numbers, double);

console.log(doubledNumbers); 
```

**Output:** 
```
[2, 4, 6, 8, 10]
```

# Question 5:

```javascript
function multiplyBy(a)
{
  return function(b)
  {
    return a*b;
  }
}

const m_by2 = multiplyBy(2)
console.log(m_by2(5))
```

**OUTPUT**
```
10
```

# Question 5:

```javascript
function sortArray(numbers, ascending)
{
  return ((arr) => 
  {
    var n = arr.length
    for(var i=0; i<n; i++)
    {
      for(var j=i+1; j<n; j++)
      {
        if((ascending && arr[j] < arr[i]) || (!ascending && arr[j] > arr[i]))
        {
          var temp = arr[j];
          arr[j] = arr[i]
          arr[i] = temp
        }
      }
    }
    return arr
  })(numbers)
}

var nums = [1,2,2,7,4,2]

console.log(sortArray(nums, true))
console.log(sortArray(nums, false))
```

**OUTPUT**
```
(6) [1, 2, 2, 2, 4, 7]
(6) [7, 4, 2, 2, 2, 1]
```
