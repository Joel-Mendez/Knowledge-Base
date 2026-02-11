# Flask 
A python framework used for frontend integration.  

# Basic Flask App
```python
from flask import Flask

app = Flask(__name__)  # Create the app

@app.route("/")        # Define a route (homepage)
def home():
    return "Hello, world!"  # What the browser will show

if __name__ == "__main__":
    app.run(debug=True)     # Start the app in debug mode
```

# App Routes
- Routes map URL paths to python functions. The backend function then returns a response to the frontend.
- Methods specify the type of HTTP request (GET, POST, etc.) that the route can handle. By default, it's GET.

```python
@app.route("/url", methods=["GET", "POST"]) 
def new_route():
    return "This is a new route!" # What the browser will show when visiting /url
```

# Request (flask.request)
A `request` objects captures the information from the incoming HTTP request. Can retrieve request information such as:
- request.method – HTTP method used (GET, POST, etc.)
- request.args – Query parameters from the URL (e.g. ?q=test)
- request.form – Data sent from HTML forms (usually POST)
- request.json – JSON data sent in the request body
- request.data – Raw request body
- request.headers – HTTP headers
- request.files – Uploaded files
- request.cookies – Cookies sent by the client
- request.path / request.url – Requested path / full URL

```python
# Importing the request object to handle incoming data
from flask import Flask, request
```
```python
request.args  # To access query parameters
data = request.get_json()  # To get JSON data from a POST request
```

# Templates (flask.render_template)
Renders HTML templates with dynamic data. Note: the HTML templates should be stored in a 'templates' folder in the same root directory of your app
```python
from flask import Flask, render_template  

Example: 
@app.route("/greet/<name>")
def greet(name):
    return render_template("greet.html", name=name)  # Pass 'name' to the template
```
# Other 
- `jsonify` is used to convert Python dictionaries to JSON format
```python
from flask import Flask, jsonify
@app.route("/api/data")
def api_data():
    data = {"key": "value", "number": 42}
    return jsonify(data)  # Return JSON response
