# Question 1:

**index.html**

```html

<!DOCTYPE html>
<html>
<head>
  <title>Change Background Color on Click</title>
  <script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
  <script src="src/script"></script>
</head>
<body>
  <button id="clickMe">Click Me</button>
</body>
</html>


```

**script.js**

```javascript

$(document).ready(function() {
      $('#clickMe').click(function() {
        $('body').css('background-color', 'red');
      });
    });  

```

# Question 2:

**index.html**

```html

<!DOCTYPE html>
<html>
<head>
  <title>Append Paragraph Using jQuery</title>
  <script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
  <script src="src/script.js"></script>
</head>
<body>
  <p id="myPara">This is the original paragraph.</p>
  <button id="myButton">Append Paragraph</button>
</body>
</html>

```

**script.js**

```javascript

$(document).ready(function() {
      $('#myButton').click(function() {
        var text = $('#myPara').text();
        var newParagraph = $('<p>').attr('id', 'newPara').text(text);
        $('#myPara').after(newParagraph);
      });
    });

```

# Question 3:

**index.html**

```html

<!DOCTYPE html>
<html>
<head>
  <title>Submit Form with jQuery</title>
  <script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
  <script src="src/script.js"></script>
</head>
<body>
  <form id="myForm">
    <input type="text" id="myInput">
    <button type="submit">Submit</button>
  </form>
</body>
</html>


```

**script.js**

```javascript

$(document).ready(function() {
      $('#myForm').submit(function(event) {
        event.preventDefault();
        var userInput = $('#myInput').val();
        alert('You entered: ' + userInput);
      });
    });

```

# Question 4:

**index.html**

```html

<!DOCTYPE html>
<html>
<head>
  <title>Highlight List Items with jQuery</title>
  <style>
    .highlight {
      color: red;
    }
  </style>
  <script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
  <script src="src/script"></script>
</head>
<body>
  <ul id="myList">
    <li>List Item 1</li>
    <li>List Item 2</li>
    <li>List Item 3</li>
    <li>List Item 4</li>
    <li>List Item 5</li>
  </ul>
</body>
</html>


```

**script.js**

```javascript

$(document).ready(function() {
      $('#myList li:first-child, #myList li:last-child').addClass('highlight');
    });

```

# Question 5:

**index.html**

```html

<!DOCTYPE html>
<html>
<head>
  <title>Add Row to Table with jQuery</title>
  <script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
  <script src="src/script.js"></script>
</head>
<body>
  <table id="myTable">
    <thead>
      <tr>
        <th>Name</th>
        <th>Age</th>
        <th>Occupation</th>
      </tr>
    </thead>
    <tbody>
    </tbody>
  </table>
  <button id="addRowButton">Add Row</button>
</body>
</html>


```

**script.js**

```javascript

$(document).ready(function() {
      $('#addRowButton').click(function() {
        var newRow = $('<tr>').append(
          $('<td>').text('John'),
          $('<td>').text('30'),
          $('<td>').text('Developer')
        );
        $('#myTable').append(newRow);
      });
    });

```
