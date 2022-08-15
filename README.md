# FlaskWebDev
Flask Web Development by Miguel Grinberg

## Part I, Introduction to Flask

### Chapter 1. Installation

1. Create a project in pycharm "FlaskWebDev", with a new virtual environment.
2. Install Python Packages with pip
* Install Flask
```commandline
pip install flask
```

* Dependencies
```commandline
pip freeze
```

* Safe-check
```python
import flask
```


### Chapter 2. Basic Application Structure

#### Initialization

* Creation of application instance
```python
from flask import Flask
app = Flask(__name__)
```

#### Routes and View Functions

* Route declaration
```python
@app.route('/')
def index():
    return '<h1>Hello World!</h1>'
```

* Traditional way
```python
def index():
    return '<h1>Hello Wolrd!</h1>'

app.add_url_rule('/', 'index', index)
```

* Dynamic component
```python
@app.route('/user/<name>')
def user(name):
    return '<h1>Hello, {}!</h1>'.format(name)
```

#### A Complete Application

* A complete Flask application
```python
# hello.py
from flask import Flask
app = Flask(__name__)

@app.route('/'):
def index():
    return '<h1>Hello World!</h1>'
```

#### Development Web Server

* Windows Development Server
```commandline
set FLASK_APP=hello.py
flask run
```

* Automatic Development Server
```python
if __name__ == '__main__':
    app.run()
```

#### Dynamic Routes

* Flask application with dynamic route
```python
from flask import Flask
app = Flask(__name__)

@app.route('/')
def index():
    return '<h1>Hello World!</h1>'

@app.route('/user/<name>')
def user(name):
    return '<h1>Hello, {}!</h1>'.format(name)
```

#### Debug Mode

* Reloader and debugger is enabled by default.
* Reloader watches source code and updates.
* Debugger appears in the browser when error occurs.
```commandline
set FLASK_APP=hello.py
```

#### Command-Line Options

* ```flask``` command supports a lot of options.

#### The Request-Response Cycle

#### Application and Request Contexts

* Flask uses contexts to temporarily make certain objects globally accessible.
```python
from flask import request

@app.route('/')
def index():
    user_agent = request.headers.het('User-Agent')
    return '<p>Your browser is {}'.format(user_agent)
```
* Context enable Flask to make certain variables globally accessible to a thread without interfering with other threads.

#### Request Dispatching

#### The Request Object

#### Request Hooks

#### Responses

```python
from flask import Flask

@app.route('/')
def index():
    response = make_response('<h1>This document carries a cookie!</h1>')
    response.set_cookie('answer', '42')
    return response
```

```python
from flask improt Flask

@app.route('/')
def index():
    return redirect('http://www.example.com')
```

```python
from flask import abort

@app.route('/user/<id>')
def get_user(id):
    user = load_user(id)
    if not user:
        abort(404)
    return '<h1>Hello, {}</h1>'.format(user.name)
```

#### Flask Extensions

* Flask is designed to be extended, a great variety of Flask extensions are available.