# What is HTML?
HTML (HyperText Markup Language)
Determines the layout of your structure. 

# Hello World!
```html
<!DOCTYPE html>
<html>
    <head>
        <title> Webpage Title </title>
    </head>
    <body>
        <h1> Heading </h1>
        <p> Web Conent </p>
    </body>
</html>
```

# User Input 
```html
<input type="text" placeholder="Enter Text Here">
```

# Buttons
Basic construction:
```html
<button> Click Me! </button>
```

Attaching Javascript function:
```html
<button onclick="myFunction()">Click me</button>
```

# Lists
`<ul>` is an unordered (bulleted) list. `<li>` is each list item inside it (often created dynamically with JavaScript).
```html
<ul id="task-list">
    <li>Buy milk</li>
    <li>Walk the dog</li>
</ul>
```

# span

`<span>` is an **inline** HTML element used for inline selection or highlighting. Useful for selecting small parts of your page that are meant to be dynamic.

**Example (updating text with JavaScript):**

```html
<p>Result: <span id="result">---</span></p>

<script>
    // Update only the span's text
    document.getElementById("result").textContent = "Hello!";
</script>
```
