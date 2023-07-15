# Question 1:

Asynchronous programming is a programming paradigm that allows multiple tasks or operations to be executed concurrently, without blocking the execution of the main program or thread. In traditional synchronous programming, tasks are executed one after the other, and the program waits for each task to complete before moving on to the next one. In contrast, asynchronous programming enables tasks to be started and completed independently, with the program continuing its execution while waiting for the results.

In asynchronous programming, operations that may take time to complete, such as I/O operations or network requests, are initiated and then executed in the background. The program doesn't halt or waste time waiting for these operations to finish. Instead, it registers a callback function or uses other mechanisms to receive the result or notification when the task is completed. This approach allows the program to perform other tasks or respond to user input while waiting for the asynchronous operations to complete.

Asynchronous programming is particularly beneficial in scenarios where long-running or potentially blocking operations are involved, such as fetching data from a remote server, reading from or writing to a file, or waiting for user input. It can help improve the responsiveness and efficiency of applications, as it allows them to perform other tasks while waiting for potentially slow operations to finish.

# Question 2:

Callbacks in JavaScript are functions that are passed as arguments to other functions and are executed or called at a specific point within the containing function. They are commonly used to handle asynchronous operations and ensure that certain code runs after a particular task is completed.

Here's an easy example that demonstrates the use of a callback function in JavaScript:

```javascript
function greet(name, callback) {
  console.log('Hello, ' + name + '!');

  callback();
}

function sayGoodbye() {
  console.log('Goodbye!');
}

// Passing the `sayGoodbye` function as a callback to `greet`
greet('Harsh', sayGoodbye);
```

In this example, we have a function called `greet` that accepts two arguments: `name` and `callback`. It logs a greeting message with the provided name using `console.log`. After that, it invokes the `callback` function.

We define another function called `sayGoodbye` that logs a farewell message using `console.log`.

When we call the `greet` function, we pass the name `'Harsh'` as the first argument and the `sayGoodbye` function as the second argument. The `sayGoodbye` function is passed as a callback.

When the `greet` function is executed, it logs the greeting message, in this case, "Hello, Harsh!" using `console.log`. Then it invokes the `callback` function, which is the `sayGoodbye` function in this case.

As a result, the output of running this code would be:

```
Hello, Harsh!
Goodbye!
```

The important thing to note is that the `sayGoodbye` function is not executed directly when it is passed as an argument to `greet`. Instead, it is invoked at a specific point within the `greet` function, which gives us control over the execution flow.

This example demonstrates a simple use case of a callback, where the `sayGoodbye` function is called as a callback after the greeting message is logged. However, in more complex scenarios, callbacks are often used with asynchronous operations, such as making AJAX requests or reading files, to handle the results or perform further actions once the operation is complete.


# Question 3:

In JavaScript, a Promise is an object that represents the eventual completion (or failure) of an asynchronous operation and its resulting value. Promises provide a way to handle asynchronous code in a more organized and readable manner compared to traditional callbacks.

A Promise can be in one of three different states:

1. **Pending**: The initial state of a Promise. It is neither fulfilled nor rejected; it is still in progress.

2. **Fulfilled**: The Promise has successfully completed the asynchronous operation and has a resolved value. This state is also referred to as "resolved."

3. **Rejected**: The Promise has encountered an error or failure during the asynchronous operation and has a reason for the rejection.

Promises have built-in methods that can change their state:

1. **resolve**: The `resolve` method is used to change a Promise's state to fulfilled. It takes an optional value as an argument and sets the resolved value of the Promise.

2. **reject**: The `reject` method is used to change a Promise's state to rejected. It takes an optional reason (typically an error object) as an argument and sets the reason for the rejection.

These methods are typically used within the executor function when creating a new Promise. The executor function is passed as an argument to the Promise constructor and is responsible for initiating the asynchronous operation.

Here's an example that demonstrates the creation of a Promise and the usage of these methods:

```javascript
const promise = new Promise((resolve, reject) => {
  // Simulating an asynchronous operation
  setTimeout(() => {
    const randomNumber = Math.random();
    
    if (randomNumber < 0.5) {
      resolve(randomNumber); // Change state to fulfilled
    } else {
      reject(new Error('Random number is greater than or equal to 0.5')); // Change state to rejected
    }
  }, 2000);
});

promise.then(
  (resolvedValue) => {
    console.log('Promise resolved with value:', resolvedValue);
  },
  (rejectionReason) => {
    console.log('Promise rejected with reason:', rejectionReason);
  }
);
```

In this example, we create a new Promise using the Promise constructor. Inside the executor function, we simulate an asynchronous operation using `setTimeout`. If the generated random number is less than 0.5, we call `resolve` with the random number as the resolved value. Otherwise, we call `reject` with an error object as the reason for rejection.

After creating the Promise, we use the `then` method to attach two separate callbacks: one for handling the fulfillment (resolved value) and one for handling the rejection (rejection reason). Depending on the state change, either the resolve callback or the reject callback will be executed.

When the Promise resolves, the resolve callback is called, and the resolved value is logged to the console. If the Promise rejects, the reject callback is called, and the rejection reason (an error object) is logged to the console.

By using Promises and their state-changing methods, we can handle asynchronous operations more effectively and write more readable and maintainable asynchronous code.

# Question 4:

```javascript

const myPromise = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve("Hello Javascript");
  }, 5000);
});

myPromise.then((resolvedValue) => {
  console.log("Length of the resolved string:", resolvedValue.length);
});

```

**OUTPUT**

```

Length of the resolved string: 16

```

# Question 5:

Callback hell, also known as the "pyramid of doom," is a situation that arises when working with multiple asynchronous operations using traditional callbacks in JavaScript. It occurs when callbacks are nested within each other, resulting in deeply nested and indented code that becomes hard to read, understand, and maintain.

In callback hell, the code structure becomes convoluted due to the need to handle multiple asynchronous operations sequentially. Each asynchronous operation relies on the completion of the previous one, and their callbacks are nested within each other. This nesting grows deeper as more asynchronous operations are added, leading to code that is difficult to follow, debug, and modify.

Here's an example of callback hell:

```javascript
asyncOperation1(arg1, (result1) => {
  // Callback of asyncOperation1
  asyncOperation2(arg2, (result2) => {
    // Callback of asyncOperation2
    asyncOperation3(arg3, (result3) => {
      // Callback of asyncOperation3
      // ... and so on
    });
  });
});
```

As you can see, each callback relies on the completion of the previous operation, resulting in multiple levels of indentation and a loss of code clarity.

Promises provide a more elegant and readable alternative to dealing with asynchronous operations, helping to alleviate callback hell. Promises allow us to chain multiple asynchronous operations together in a sequential manner without the need for deeply nested callbacks.

Using promises, the same code can be refactored to a more readable and maintainable structure:

```javascript
asyncOperation1(arg1)
  .then((result1) => {
    // Promise chain
    return asyncOperation2(arg2);
  })
  .then((result2) => {
    return asyncOperation3(arg3);
  })
  .then((result3) => {
    // ...
  })
  .catch((error) => {
    // Error handling
  });
```

In this example, each asynchronous operation is wrapped in a Promise. The `then` method is used to chain the promises together sequentially. Each `then` callback receives the resolved value of the previous operation as an argument, allowing us to perform the next operation in the chain. The code becomes more linear and easier to follow, with clear separation between each asynchronous operation.

The use of promises helps reduce callback hell by providing a more structured and readable way of handling asynchronous operations. Promises enable code to be written in a more declarative style, making it easier to understand and reason about asynchronous code flow. Additionally, promises also provide built-in error handling through the `catch` method, which allows for centralized error handling for the entire promise chain.

Furthermore, with the introduction of async/await syntax in modern JavaScript, working with promises becomes even more concise and readable, offering a further reduction in callback hell.

# Question 6:

The main difference between `Promise.all()` and `Promise.allSettled()` lies in how they handle the fulfillment or rejection of multiple promises.

`Promise.all()`:
- Resolves when all the promises in the given iterable (e.g., an array) have resolved.
- If any of the promises in the iterable rejects, `Promise.all()` immediately rejects with the reason of that rejected promise.
- The resolved value of `Promise.all()` is an array containing the resolved values of all the input promises, in the same order as the original iterable.

`Promise.allSettled()`:
- Resolves when all the promises in the given iterable have settled (i.e., either fulfilled or rejected).
- Unlike `Promise.all()`, even if some promises in the iterable reject, `Promise.allSettled()` still resolves with an array of objects representing the outcome of each promise.
- The resolved value of `Promise.allSettled()` is an array of objects, where each object has a `status` property representing the outcome of the promise (`"fulfilled"` or `"rejected"`) and a `value` or `reason` property containing the resolved value or rejection reason.

Here's an example to illustrate the difference:

```javascript
const promises = [
  Promise.resolve('Resolved 1'),
  Promise.reject(new Error('Rejected 1')),
  Promise.resolve('Resolved 2'),
];

Promise.all(promises)
  .then((values) => {
    console.log('Promise.all resolved:', values);
  })
  .catch((error) => {
    console.log('Promise.all rejected:', error);
  });

Promise.allSettled(promises)
  .then((results) => {
    console.log('Promise.allSettled:', results);
  });
```

In this example, we have an array called `promises` that contains three promises. The first and third promises resolve successfully, while the second promise is intentionally rejected with an error.

When we use `Promise.all()`, it waits for all the promises to either resolve or reject. If any promise rejects, the entire `Promise.all()` operation is immediately rejected. In this case, the rejection is caught in the `.catch()` callback. If all promises resolve, the resolved values are collected into an array, which is passed to the `.then()` callback.

When we use `Promise.allSettled()`, it also waits for all the promises to settle, regardless of whether they fulfill or reject. It doesn't reject the overall operation just because some promises reject. Instead, it creates an array of objects representing the outcome of each promise. Each object in the resulting array has a `status` property indicating whether the promise was fulfilled or rejected, and a `value` or `reason` property containing the resolved value or rejection reason.

# Question 7:

```javascript

function checkAge(age) {
  if (age > 80) {
    throw new SyntaxError("You are too old.");
  }
}

try {
  checkAge(85);
} catch (error) {
  console.log(error.message); // Output: You are too old.
}


```

# Question 8:

* The output of this code will be:

```

Part 2 is resolved.

```

The reason for this output is that the `Promise.any()` method returns a new Promise that is fulfilled as soon as any of the input promises are fulfilled. It ignores any rejections until all input promises have rejected. In this case, there are two promises passed to `Promise.any()`.

The first promise is set to reject after a delay of 2000 milliseconds (2 seconds) with the rejection message "Part 1 is rejected." The second promise is set to resolve after a delay of 5000 milliseconds (5 seconds) with the resolution message "Part 2 is resolved."

Since `Promise.any()` resolves as soon as any promise fulfills, the faster-resolving promise, which is the second promise, determines the fulfillment of the returned Promise. Therefore, the output logs the resolved message "Part 2 is resolved."

* If we replace `Promise.any()` with `Promise.race()`, the output of the code will still be:
  
```

Part 2 is resolved.

```

The reason is that `Promise.race()` also returns a new Promise that settles when the first promise from the input iterable (array) settles, whether it's fulfilled or rejected. It does not wait for all promises to either fulfill or reject.

In this case, even though the first promise rejects after 2 seconds and the second promise resolves after 5 seconds, `Promise.race()` settles as soon as the first promise settles, regardless of its outcome. Therefore, it resolves with the result of the faster promise, which is the resolved message "Part 2 is resolved."

The output for this case is generated faster when using `Promise.race()` compared to `Promise.any()`. This is because `Promise.race()` doesn't wait for all promises to settle, while `Promise.any()` requires all promises to either fulfill or reject before it settles. Since the second promise resolves earlier than the first promise rejects, the output is generated faster with `Promise.race()`.

# Question 9:

* The output of the above code snippet will be:

```

Part a

```

The reason for this output is that in a Promise, the `resolve` function should only be called once to fulfill the Promise with a particular value. In the given code, there are two consecutive `resolve` calls within the Promise's executor function. However, only the first `resolve("Part a")` call will be effective, and the second `resolve("Part b")` call will be ignored.

When the Promise is constructed and executed, the first `resolve` call is encountered, fulfilling the Promise with the value "Part a". After that, the Promise is considered resolved, and subsequent `resolve` calls have no effect. Therefore, the `.then()` callback will be triggered with the resolved value "Part a", and it will log "Part a" to the console.

* To get both resolved results, you can modify the code to use an array to hold multiple values and resolve the Promise with that array. Here's an example:

```javascript

const p = new Promise((resolve, reject) => {
  const results = ["Part a", "Part b"];
  resolve(results);
});

p.then((res) => console.log(res));

```

In this updated code, an array called `results` is created within the Promise's executor function, containing the desired resolved values "Part a" and "Part b". Instead of calling `resolve` multiple times, the Promise is resolved with the `results` array by passing it as the argument to the `resolve` function. As a result, the `.then()` callback will receive the array as the resolved value and log the entire array to the console. The output will be:
```
[ 'Part a', 'Part b' ]
```
By resolving the Promise with an array or any other suitable data structure that holds multiple values, you can obtain all the resolved results and process them accordingly.

# Question 10:


```javascript

async function fetchJoke() {
  try {
    const response = await fetch("https://official-joke-api.appspot.com/random_joke");
    if (!response.ok) {
      throw new Error("Request failed with status " + response.status);
    }
    const data = await response.json();
    console.log(data);
  } catch (error) {
    console.log("An error occurred:", error.message);
  }
}

fetchJoke();


```

**OUTPUT**

```

(4) {type: "general", setup: "How many h...}
type:"general"
setup:"How many hipsters does it take to change a lightbulb?"
punchline:"Oh, it's a really obscure number. You've probably never heard of it."
id:140
[[Prototype]]:{}

```
