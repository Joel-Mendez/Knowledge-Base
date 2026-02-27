# JavaScript
Programming language for the more dynamic aspect of frontend developement. 

# Defining Variables
```javascript
let x = 5 // can be reassigned 
const y = 10 // cannot be reassigned

// When retrieving a dynamic value
const input = document.getElementByID("id").value
```
## Arrays
```javascript
const myArray = [1, 2, 3] // Creating an array 
myArray[0] // Accessing the first element (1)
myArray.push(4) // Adding a new element to the end of the array
```
**forEach** — iterates over every item in an array and runs a function on each one.
```javascript
const items = ["a", "b", "c"]
items.forEach(item => {
    console.log(item)  // runs once per item
})
```

# Functions
```javascript
function function_name(input) {
    return output
}
```

# JSON
JavaScript Object Notation

Example: 
```javascript
{message: "hello"}
```
**stringify** - turns JSON object into a string so that it can be sent and interpreted

Example: 
```javascript
JSON.stringify({ message: input })
```

**Parsing a response back to JSON**
```javascript
res.json()
```

# Web API
**fetch HTTP request**

Fetching a response from the specified `/url`. 

`method` determines the type of [HTTP request](http.md). 

`headers` explains to the backend what type of content is being transmitted 

`body` is the content of the message. 

Note: the latter two won't be necessary for other requests such as GET http requests
```javascript
fetch("/your-route", {
  method: "POST",
  headers: { "Content-Type": "application/json" },
  body: JSON.stringify({ message: input })
})
```

# Promise
JavaScript object that "promises" a future value. Typically for asyncronous tasks. The value is in a pending state until the "promised" value is obtained. 

**.then()**

Promise method that specifies what to do with the promised response once it arrives. 

Example: 
```javascript
fetch("/api/data")
  .then(res => res.json()) // When the response arrives, parse JSON
  .then(data => {
    console.log(data); // Take the JSON and print it on the console
  }); // When 
```
More general example: 
```javascript
fetch("/url")                  // start an async request to /url (returns a Promise)
  .then(x => func(x))          // when the response arrives, call it "x" and apply func(x)
  .then(y => y.func());        // when the result of func(x) is ready, call it "y" and call y.func()
```

# DOM Manipulation
The DOM (Document Object Model) is the live representation of the HTML page that JavaScript can read and modify.

**createElement** — creates a new HTML element (not yet on the page).
```javascript
const item = document.createElement("li")  // creates <li></li>
item.textContent = "Buy milk"              // sets its text
```

**appendChild** — attaches a created element inside a parent element on the page.
```javascript
const list = document.getElementById("task-list")
list.appendChild(item)  // adds <li>Buy milk</li> inside the <ul>
```

**innerHTML** — reads or overwrites all the HTML content inside an element.
```javascript
list.innerHTML = ""        // clears everything inside the element
list.innerHTML = "<li>hi</li>"  // replaces content with new HTML
```

# Running Code on Page Load
Any JavaScript written at the top level of a `<script>` block (not inside a function) runs automatically when the page loads.
```javascript
function loadTasks() { /* ... */ }

loadTasks()  // called here at the top level — runs immediately when the page opens
```

# Other
`document.getElementById(...)`: retrieves an HTML element by ID.

- document = the web page
- getElementById = lookup by ID
- .value / .textContent = read or write its content

Example HTML:
```html
<input id = "inputString">
```

Example JavaScript:
```JavaScript
document.getElementById("inputString")
```
