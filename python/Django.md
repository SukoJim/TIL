# Django Basics
## Installing Django and Creating a Project

### Environment Setup
> 1. Set up a Virtual Environment (Optional)
> ```shell
> python -m venv myenv
> source myenv/bin/activate  # Or on Windows: myenv\Scripts\activate
> ```

> 2. Install Django
> ```shell
> pip install django
> ```

> 3. Check Django Version
> ```shell
> django-admin --version
> ```

### Basic Django Project Commands
> Create a Django Project
> ```shell
> django-admin startproject myproject
> ```
> 2. Navigate to the Project Directory
> ```shell
> cd myproject
> ```

> 3. Run the Development Server
> ```shell
> python manage.py runserver
> ```

## Understanding Django Models and ORM (Object-Relational Mapping)

### Defining Models
> 1. Create a Model Class: Define your data model in the models.py file.
> ```python
> from django.db import models
> 
> class Book(models.Model):
>     title = models.CharField(max_length=100)
>     author = models.CharField(max_length=50)
>     publication_date = models.DateField()
> 
>     def __str__(self):
>         return self.title
> ```

> 2. Track Model Changes
> ```shell
> python manage.py makemigrations
> ```
>
## Model data manipulation
### Data Generation
>```shell
>book = Book(title="Django for Beginners", author="William S. Vincent", publication_date="2023-01-01")
>book.save()
>```

### Data Retrieval
> 2. Fetch all books from the database:
> ```shell
> all_books = Book.objects.all()
> ```

### Data Filtering
> 3. Filter books written by "William S. Vincent":
> ```shell
> python_books = Book.objects.filter(author="William S. Vincent")
> ```

### Data Modification
> 4. Update data for a specific book (e.g., book with primary key 1):
> ```shell
> book = Book.objects.get(pk=1)
> book.title = "Django for Professionals"
> book.save()
> ```

### Data Deletion
> 5. Delete a specific book (e.g., book with primary key 1):
> ```shell
> book = Book.objects.get(pk=1)
> book.delete()
> ```

# Django Design Patterns

## 1. Model

### How it works
1. Create Python classes in the `models.py` file to define database tables.
2. Each class field is mapped to a database column.
3. Use the `migrate` command to create the database schema and store data.

>### Example
>```python
>from django.db import models
>
>class Post(models.Model):
>    title = models.CharField(max_length=200)
>    content = models.TextField()
>    pub_date = models.DateTimeField('date published')
>```
## 2. View

### How it works
1. Create Python functions or classes in the `views.py` file to define the business logic of web pages.
2. Handle requests, fetch data from the model, and pass it to the template.
3. Generate and return responses.

### Example
>```python
>from django.shortcuts import render
>from .models import Post
>
>def post_list(request):
>    posts = Post.objects.all()
>    return render(request, 'blog/post_list.html', {'posts': posts})
>```
## 3. Template

### How it works
1. Create HTML template files in the `templates` directory.
2. Use Django template language to display data dynamically within the template.
3. Render web pages dynamically using template tags and variables.

### Example
>```html
><!DOCTYPE html>
><html>
><head>
>    <title>Post List</title>
></head>
><body>
>    <h1>Blog Posts</h1>
>    <ul>
>        {% for post in posts %}
>            <li>{{ post.title }}</li>
>        {% endfor %}
>    </ul>
></body>
></html>
>```

## 4. URL Configuration
### How it works
1. Define URL patterns in the urls.py file to route requests to view functions or classes.
2. Map URL patterns using regular expressions.
3. Django processes requests by calling the appropriate view based on the URL pattern.

>```python
>from django.urls import path
>from . import views
>
>urlpatterns = [
>    path('posts/', views.post_list, name='post_list'),
>]
>```
