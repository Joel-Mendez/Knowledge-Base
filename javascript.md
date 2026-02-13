# JavaScript
Programming language for the more dynamic aspect of frontend developement. 

# Defining Variables
```javascript
let x = 5 // can be reassigned 
const y = 10 // cannot be reassigned
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
fetch("/reverse", {
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
