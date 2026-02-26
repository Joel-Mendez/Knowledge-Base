# Hello World!
`print('howdy howdy')`

# Running .py file
`python3 main.py`

# Functions
```python
def function_name(input1, input2, inputN):
		#function logic
		
		return return_variable
```

# Strings
- Reverse a string: `my_string[::-1]`

# Tuples
- An immutable, ordered collection of values. Example: `example_tuple = (value1, value2)`
- Single-element tuples require a trailing comma. Without it, Python treats the parentheses as just grouping, not a tuple.

```python
single = (name,)   # tuple with one element — the comma is required
not_a_tuple = (name)  # this is just 'name' in parentheses, not a tuple
```

# Importing Local Modules
- You can import your own `.py` files the same way you import standard libraries (just use the filename without the `.py` extension). 
- Functions and variables defined in that file are then accessible via `module.function()`.

```python
# tasks.py exists in the same directory
import tasks

tasks.create_task("Buy milk")  # calls create_task() from tasks.py
```