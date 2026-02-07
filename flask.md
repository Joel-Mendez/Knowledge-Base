# What is Flask? 
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
