# Question 1:

In JavaScript, there is a concept called "hoisting" which refers to the behavior of moving variable and function declarations to the top of their containing scope during the compilation phase. However, it's important to note that hoisting treats function declarations and function expressions differently.

When using function declaration syntax, the entire function declaration is hoisted to the top of the scope, allowing you to call the function before its actual declaration in the code. Here's an example:

```javascript
hoistedFunction(); // Function call before declaration

function hoistedFunction() {
  console.log('This is a hoisted function.');
}
```

In the above code, the function `hoistedFunction` is called before its actual declaration. However, due to hoisting, it will still work as expected because the function declaration is moved to the top by the JavaScript engine during compilation.

On the other hand, when using function expression syntax, only the variable declaration is hoisted, not the function assignment. Here's an example to illustrate this:

```javascript
nonHoistedFunction(); // TypeError: nonHoistedFunction is not a function

var nonHoistedFunction = function() {
  console.log('This is a non-hoisted function.');
};
```

In this case, the variable `nonHoistedFunction` is hoisted to the top, but since it is assigned a function expression later in the code, attempting to call it before the assignment results in a `TypeError`.


# Question 2:

* Date.now():
The `Date.now()` function is a static method of the `Date` object in JavaScript. It returns the number of milliseconds elapsed since January 1, 1970, 00:00:00 UTC (Coordinated Universal Time). This method is often used to measure time intervals or to generate unique timestamps. Here's an example:

```javascript
const timestamp = Date.now();
console.log(timestamp); // Output: 1626189508976 (this value will vary)
```

In the example above, `Date.now()` is called and the returned timestamp is stored in the `timestamp` variable. The value printed to the console represents the current timestamp in milliseconds.

* ?? (nullish coalescing operator):
The nullish coalescing operator `??` is a logical operator introduced in JavaScript to provide a convenient way to assign default values to variables when the value on the left-hand side is either `null` or `undefined`. It allows you to check for nullish values explicitly. Here's an example:

```javascript
const defaultValue = 'Default Value';
let userInput;

const result = userInput ?? defaultValue;
console.log(result); // Output: 'Default Value'
```

In the code above, `userInput` is `undefined`, and the `??` operator is used to assign `defaultValue` to `result`. Since `userInput` is `undefined`, the expression `userInput ?? defaultValue` evaluates to `defaultValue`.

* ?. (optional chaining operator):
The optional chaining operator `?.` is a useful operator introduced in JavaScript to simplify accessing properties or calling methods of an object when the object may be `null` or `undefined`. It allows you to safely navigate nested property chains without throwing an error if any intermediate property is `null` or `undefined`. Here's an example:

```javascript
const user = {
  id: 1,
  name: 'Alice',
  address: {
    street: '123 Main St',
    city: 'Exampleville',
    country: 'Exampleland'
  },
  getFullName() {
    return this.name;
  }
};

// Accessing nested properties
const city = user.address?.city;
console.log(city); // Output: 'Exampleville'

// Calling a method
const fullName = user.getFullName?.();
console.log(fullName); // Output: 'Alice'

// Accessing non-existent property
const postalCode = user.address?.postalCode;
console.log(postalCode); // Output: undefined

```

In the code above, `person.address?.city` safely accesses the `city` property of the `address` object. If `address` were `null` or `undefined`, the expression would short-circuit, and `city` would be `undefined`. The optional chaining operator allows us to avoid potential `TypeError` when accessing nested properties.


# Question 3:

* (a)
```javascript

const sentence = "I love going walkies";
const wordsArray = sentence.split(" ");
console.log(wordsArray);

```

* (b)

```javascript

const [word1, word2, word3, word4] = wordsArray;
console.log(word1, word2, word3, word4);

```

# Question 4:

```javascript

const myObject = {
  x1: 'Samba',
  x2: {
    x3: {
      x4: {},
      x5: 'Rails',
    },
    x6: {
      x7: -1,
      x8: [25, 8, 4, 10],
    },
  },
};

// (a)
const { x2: { x3: y } } = myObject;
console.log(y);

// (b)
var second = myObject.x2.x6.x8[1];
console.log(second)

```

# Question 5:

```javascript

const myObject = {
  x1: 'Samba',
  x2: {
    x3: {
      x4: {},
      x5: 'Rails',
    },
    x6: {
      x7: -1,
      x8: [25, 8, 4, 10],
    },
  },
};

var newObject = {
  ...myObject, 
  x20: "Shinko",
  x21: [5, 40, 73, 19]
}


console.log(newObject)

```

# Question 6:

```javascript

const myObject = {
  x1: 'Samba',
  x2: {
    x3: {
      x4: {},
      x5: 'Rails',
    },
    x6: {
      x7: -1,
      x8: [25, 8, 4, 10],
    },
  },
};

var newObject = {
  ...myObject, 
  x20: "Shinko",
  x21: [5, 40, 73, 19]
}


var newArray = myObject.x2.x6.x8.concat(newObject.x21);
console.log(newArray)

```

# Question 7:

* Out of the two functions, `f1` is pure, and `f2` is impure. 

The reason `f1` is considered pure is that it only operates on the input parameter `num` and performs a simple calculation without modifying any external state or having side effects. It relies solely on the input provided and returns a predictable output based on that input. The function does not mutate any variables outside its scope or access any external resources.

On the other hand, `f2` is impure because it modifies the external variable `aRandomNum` by multiplying it with 3. This modification of the external state is a side effect that can impact the behavior of other parts of the program. Additionally, the function accesses and modifies a global variable, which introduces coupling and can make the code harder to reason about.

* The output of the program will be:

```
111
111
333
```

* The first call to `f1(aRandomNum)` passes the initial value of `aRandomNum`, which is 37. It logs the result of the calculation `37 * 3`, which is 111.
* Then, the call to `f2()` modifies the value of `aRandomNum` by multiplying it with 3, making it 111. It logs the new value of `aRandomNum`, which is also 111.
* Finally, the second call to `f1(aRandomNum)` passes the updated value of `aRandomNum`, which is 111. It performs the calculation `111 * 3` and logs the result, which is 333.

# Question 8:

In arrow functions, the parentheses for function parameters can be omitted in certain cases:

**When there is only one parameter:**

```javascript
const singleParam = param => {
  console.log(param);
};

singleParam('Hello');
```
In this example, since there is only one parameter (`param`), the parentheses around it can be omitted.

**When there are no parameters:**
```javascript
const noParams = () => {
  console.log('No parameters');
};

noParams();
```
In this example, since there are no parameters, the parentheses are omitted altogether.

**When there are multiple parameters, parentheses are always required:**
```javascript
const multipleParams = (param1, param2) => {
  console.log(param1, param2);
};

multipleParams('Hello', 'World');
```
In this case, where there are multiple parameters (`param1` and `param2`), the parentheses are required.


# Question 9:

* Arrow functions have a lexical `this` binding:
   This means that the value of `this` inside an arrow function is determined by its surrounding (lexical) scope. It does not have its own `this` value. Instead, it inherits the `this` value from the enclosing scope where the arrow function is defined.

* Regular functions have dynamic `this` binding:
   Regular functions, on the other hand, have dynamic `this` binding. The value of `this` inside a regular function is determined dynamically based on how the function is called or invoked. It can vary depending on the execution context, such as the object calling the function or how the function is explicitly bound.

To understand the difference, let's consider an example:

```javascript
const obj = {
  val: "hello",
  fun1() {return this.val},
  fun2: () => this.val
  
}


console.log(obj.fun1()) // Output is hello
console.log(obj.fun2()) // Output is undefined
```

In this example, `obj` is an object with two methods, `fun1` and `fun2`. When `obj.fun1()` is called, the `this` value inside the regular function refers to the object `obj` itself. Therefore, it correctly logs the value `Hello` associated with `obj.value`.

However, when `obj.fun2()` is called, the `this` value inside the arrow function does not refer to `obj`. Since arrow functions have a lexical `this` binding, it inherits the `this` value from the surrounding (lexical) scope, which in this case is the global or enclosing scope. Therefore, it logs `undefined` because `this.value` is not defined in the global scope.

In summary, arrow functions inherit the `this` value from their surrounding scope, while regular functions have a dynamic `this` binding that depends on how they are called or invoked. This difference in `this` binding behavior is important to consider when using arrow functions as object methods or when accessing the `this` value within functions.
