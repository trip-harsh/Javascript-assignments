# Question 1:

``` Javascript

var a = "Azad Ram Madiha Yash"
var arr = a.split(" ")
for(var k of arr)
{
  console.log(k[0] + " ")
}

```

**OUTPUT**

```

A 
R 
M 
Y 

```

# Question 2:

```javascript
var arr = [1, -4, 12, 0, -3, 29, -150]
var ans = arr.reduce((a, b)=>{
  if(b > 0) a += b  
  return a
})

console.log(ans)
```

**OUTPUT**
```
42
```

# Question 3:

```javascript
var arr = [1, 2, 3, 4, 5]
var ans = arr.map(a => a*a)
console.log(ans)
```

**OUTPUT**

```
(5) [1, 4, 9, 16, 25]
```

# Question 4:

```javascript
var arr =  [{ id: 2100, name: 'President Jacqueline' }, 
            { id: 2114, name:'Vice-president James' }, 
            { id: 3016, name: 'House-captain Otis' }, 
            { id: 4818, name: 'Prefect Finneas' }]

//Method 1
var ans1 = []
for(var a of arr)  ans1.push(a.id)
console.log(ans1)

//Method 2
var ans2 = arr.map((a) => a.id)
console.log(ans2)
```

**OUTPUT**
```
(4) [2100, 2114, 3016, 4818]
(4) [2100, 2114, 3016, 4818]
```
