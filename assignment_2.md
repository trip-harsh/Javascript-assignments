# Question 1:

When we execute this code:
``` javascript
var text = 'outside';
function logIt()
{
  console.log(text);
  var text = 'inside';
}

logIt();
```

We will get the output as:
```
undefined
```

# Question 2:
```javascript
const fullName = 'Harsh Tripathi';
const rev_name = fullName.replace(/(\w+)\s+(\w+)/, '$2 $1');

console.log(rev_name);
```

**OUTPUT**
```
Tripathi Harsh
```

# Question 3:
The regular expression for email address validation is as follows:
```
([^\s@]+@[^\s@]+\.[a-zA-Z]+)
```

# Question 4:

```javascript

var x = 100;
console.log(x);
function test()
{
  var x = 250;
  console.log(x);
  if (x > 100) 
  {
    let x = 350;
    console.log(x);
  }
  console.log(x);
}
test();
console.log(x);
```

**OUTPUT**
```
100
250
350
250
100
```

# Question 5:

# a)
```
True
```

# b)
```
false
```

# c)
```
true
```

The == operator will compare for equality after doing any necessary type conversions. The === operator will not do the conversion, so if two values are not the same type === will simply return false.

# Question 6:
In JavaScript, NaN stands for "Not a Number." It is a special value that represents the result of an operation that is mathematically undefined or cannot be represented as a valid number.

NaN is typically returned as a result when performing arithmetic operations or mathematical functions that involve non-numeric values. For example:
```javascript
const result = 10 / "hello";
console.log(result);
```
**OUTPUT**
```
NaN
```
In this example, dividing the number 10 by a non-numeric value ("hello") results in NaN because the division operation is not defined for strings.
