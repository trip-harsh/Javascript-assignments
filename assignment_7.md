# Question 1:

**index.html**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <input type="text" name="str" id = "str" placeholder="Enter Text Here">
    <button id = "submit_button">Click here to submit</button>
    <ul id = "list"></ul>
    
    <script src="script.js"></script>
</body>
</html>
```
**script.js**

```javascript
const text_box = document.getElementById("str")
const item_list = document.getElementById("list")
const submit_btn = document.getElementById("submit_button")

submit_btn.addEventListener('click', add_to_list);

function add_to_list()
{
    const inp = text_box.value;
    const list_ele = document.createElement('li');
    list_ele.textContent = inp;
    
    item_list.appendChild(list_ele)
    text_box.value = '';
}
```

# Question 2:

```javascript
const styler = document.getElementById("text")
const btn = document.getElementById("jsstyle")

btn.addEventListener('click', () => {
    styler.setAttribute("style", `background-color: aqua; 
                                  font-family: Arial;
                                  font-size: 20px`);
});


```

# Question 3:

**index.html**
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    
    <div style="width: 40px; display: grid; align-items: center;">
        <input type="number" id="length" placeholder="Enter Length here">
        <input type="number" id="breadth" placeholder="Enter Breadth here">
        <button id="calculate">Calculate</button>
        <p id="result"></p>
    </div>

    <script src="script.js"></script>
</body>
</html>
```

**script.js**

```javascript
const len = document.getElementById("length")
const bth = document.getElementById("breadth")

const res = document.getElementById("result")

const btn = document.getElementById("calculate")


btn.addEventListener('click', ()=>{
    const area = len.value * bth.value
    res.textContent = `The area of rectangle is ${area}`
})

```

# Question 4:

**index.html**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    
    <form id="sample" style="display: inline-flex; flex-direction: column; flex-wrap: wrap;">
        <label>Name</label>
        <input placeholder="Enter your name">
        <label>Age</label>
        <input placeholder="Enter your age">
        <button id="submit">Submit</button>
    </form>
    <script src="script.js"></script>
</body>
</html>
```

**script.js**

```javascript
const btn = document.getElementById("submit")

btn.addEventListener('click', ()=>{
    alert("Form has been submitted.")
})
```

# Question 5:

**script.js**
```javascript
window.addEventListener('resize', ()=>{
    alert("Window resized!")
})
```

# Question 6:

**index.html**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <p id="test">This is the text which will be changed.</p>
    <button id = "btn" style="align-items: center;">Click to read</button>
    <script src="script.js"></script>
</body>
</html>
```

**script.js**

```javascript
const btn = document.getElementById("btn");

btn.addEventListener('click', ()=>
{
    var httpReq = new XMLHttpRequest();
    httpReq.open("GET", "file:///E:/test.txt", true)
    
    httpReq.onload = ()=>{
        {
            document.getElementById("test").textContent = this.responseText;

        }
    }

    httpReq.send();
})
```

# Question 7:

**index.html**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <button id = "btn" style="align-items: center;">Click to read</button>
    <div id="imageContainer"></div>
    <script src="script.js"></script>
</body>
</html>
```

**script.js**

```javascript
const btn = document.getElementById("btn");
btn.addEventListener('click', ()=>
{
    var httpReq = new XMLHttpRequest();
    
    httpReq.open("GET", "https://www.fanboy.com/wp-content/uploads/2013/10/Sherlock-Benedict-Cumberbatch-Martin-Freeman-1200x1920.jpg", true);
    
    httpReq.responseType = "blob";

    httpReq.onload = ()=>{
        const image = document.createElement("img");
        const url = URL.createObjectURL(httpReq.response);

        image.src = url;

        document.getElementById("imageContainer").appendChild(image);
        
    }

    httpReq.send();
})
```
