# Question 1:

```javascript

// (a)
class AlertBox
{
  constructor(applicationName)
  {
    this.applicationName = applicationName;
  }

  showAlertBox(message)
  {
    alert(`${this.applicationName} : ${message}`);
  }
}

// (b)
var obj = new AlertBox("Javascript")
obj.showAlertBox("DONE")

```

# Question 2:

```javascript

class AlertBox
{
  constructor(applicationName)
  {
    this.applicationName = applicationName;
  }

  showAlertBox(message)
  {
    alert(`${this.applicationName} : ${message}`);
  }
}


class SuccessMessage extends AlertBox
{
  showAlertBox(message)
  {
    alert(`Success: ${message}`);
  }
}

var obj = new SuccessMessage()
obj.showAlertBox("Done")

```

# Question 3:

Inheritance is a fundamental concept in object-oriented programming (OOP) that allows objects or classes to inherit properties and behaviors from other objects or classes. It enables code reuse, promotes modularity, and helps create hierarchical relationships between objects.

Prototypes, in the context of JavaScript, are mechanisms that allow objects to inherit properties and methods from other objects. Every JavaScript object has an internal link to another object called its prototype. When you access a property or method on an object, and it doesn't exist on that object itself, JavaScript will look for it in the prototype chain.

Yes, we can achieve inheritance using prototypes in JavaScript. Prototypal inheritance is a core feature of the JavaScript language. Here's an example to demonstrate inheritance using prototypes:

```javascript
// Parent class
function Animal(name) {
  this.name = name;
}

// Method defined in the prototype of Animal
Animal.prototype.eat = function() {
  console.log(this.name + ' is eating.');
};

// Child class inheriting from Animal
function Dog(name) {
  Animal.call(this, name);
}

// Inherit prototype from Animal
Dog.prototype = Object.create(Animal.prototype);

// Method defined in the prototype of Dog
Dog.prototype.bark = function() {
  console.log(this.name + ' is barking.');
};

// Create instances of Dog
const dog1 = new Dog('Buddy');
const dog2 = new Dog('Max');

// Access inherited method and child method
dog1.eat(); // Output: Buddy is eating.
dog1.bark(); // Output: Buddy is barking.

dog2.eat(); // Output: Max is eating.
dog2.bark(); // Output: Max is barking.
```

In this example, we have a parent class `Animal` and a child class `Dog`. The `Animal` class has a constructor and a method `eat()` defined in its prototype. The `Dog` class uses `Object.create()` to inherit the prototype of `Animal`, and it also has a constructor and a method `bark()` defined in its prototype.

When we create instances of `Dog`, they inherit the properties and methods from `Animal` through the prototype chain. Thus, the instances can access the inherited method `eat()` as well as their own method `bark()`.
