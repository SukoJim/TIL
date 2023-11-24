# Flask Basics
## Installing Flask and Creating an App

### Environment Setup
> 1. Set up a Virtual Environment (Optional)
> ```shell
> python -m venv myenv
> source myenv/bin/activate  # Or on Windows: myenv\Scripts\activate
> ```

> 2. Install Flask
> ```shell
> pip install flask
> ```

### Basic Flask App Commands
> 1. Create a Flask App
> ```shell
> mkdir myapp
> cd myapp
> ```

> 2. Create a Virtual Environment (Optional)
> ```shell
> python -m venv venv
> source venv/bin/activate  # Or on Windows: venv\Scripts\activate
> ```

> 3. Install Flask
> ```shell
> pip install flask
> ```

> 4. Create a Python File (e.g., app.py)
> ```python
> from flask import Flask
> 
> app = Flask(__name__)
> 
> @app.route('/')
> def hello_world():
>     return 'Hello, World!'
> ```

> 5. Run the App
> ```shell
> flask run
> ```

## Understanding Flask Routes and Views

### Defining Routes
> 1. Define a Route
> ```python
> @app.route('/about')
> def about():
>     return 'About Us'
> ```

> 2. Route with Variable
> ```python
> @app.route('/user/<username>')
> def show_user(username):
>     return f'User: {username}'
> ```

### Request and Response
> 3. Accessing Query Parameters
> ```python
> from flask import request
> 
> @app.route('/greet')
> def greet():
>     name = request.args.get('name', 'Guest')
>     return f'Hello, {name}!'
> ```

## Working with Templates in Flask

### Template Setup
> 1. Create a Templates Folder
> ```shell
> mkdir templates
> ```

> 2. Create HTML Template (e.g., index.html)
> ```html
> <!DOCTYPE html>
> <html>
> <head>
>     <title>My Flask App</title>
> </head>
> <body>
>     <h1>{{ title }}</h1>
>     <p>{{ content }}</p>
> </body>
> </html>
> ```

### Rendering Templates
> 3. Render Template in View
> ```python
> from flask import render_template
> 
> @app.route('/home')
> def home():
>     return render_template('index.html', title='Welcome', content='This is my Flask app.')
> ```

## Flask Model (No Built-in ORM)

### Data Handling
> 1. Use External Database Libraries (e.g., SQLAlchemy) for ORM

### Data Generation
>```python
>from myapp import db
>from myapp.models import Book
>
>book = Book(title="Flask for Beginners", author="John Doe", publication_date="2023-01-01")
>db.session.add(book)
>db.session.commit()
>```

### Data Retrieval
> 2. Fetch all books from the database:
> ```python
> all_books = Book.query.all()
> ```

### Data Filtering
> 3. Filter books written by "John Doe":
> ```python
> flask_books = Book.query.filter_by(author="John Doe").all()
> ```

### Data Modification
> 4. Update data for a specific book (e.g., book with id 1):
> ```python
> book = Book.query.get(1)
> book.title = "Flask for Professionals"
> db.session.commit()
> ```

### Data Deletion
> 5. Delete a specific book (e.g., book with id 1):
> ```python
> book = Book.query.get(1)
> db.session.delete(book)
> db.session.commit()
> ```

# Flask Design Patterns

## 1. Route and View

### How it works
1. Define routes in the `app.py` file to handle different URL paths.
2. Create view functions or classes to handle requests and generate responses.
3. Use decorators to associate routes with view functions.

>### Example
>```python
>from flask import Flask, render_template
>app = Flask(__name__)
>
>@app.route('/')
>def home():
>    return render_template('index.html', title='Welcome', content='This is my Flask app.')
>```

## 2. Template

### How it works
1. Create HTML template files in the `templates` directory.
2. Use Jinja2 template engine to embed dynamic content within the template.
3. Render templates in view functions using `render_template` function.

### Example
>```html
><!DOCTYPE html>
><html>
><head>
>    <title>{{ title }}</title>
></head>
><body>
>    <h1>{{ title }}</h1>
>    <p>{{ content }}</p>
></body>
></html>
>```

## 3. Model (Using External Libraries)

### How it works
1. Use external database libraries like SQLAlchemy for handling models and ORM.
2. Define model classes to represent database tables.
3. Perform database operations using the model classes.

>```python
>from flask_sqlalchemy import SQLAlchemy
>db = SQLAlchemy()
>
>class Book(db.Model):
>    id = db.Column(db.Integer, primary_key=True)
>    title = db.Column(db.String(100))
>    author = db.Column(db.String(50))
>    publication_date = db.Column(db.Date)
>```

## 4. URL Configuration

### How it works
1. Define URL patterns in the `app.py` file to route requests to view functions or classes.
2. Map URL patterns using route decorators.
3. Flask processes requests by calling the appropriate view based on the URL pattern.

>```python
>from flask import Flask
>app = Flask(__name__)
>
>@app.route('/')
>def home():
>    return 'Hello, World!'
>```
