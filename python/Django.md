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

## Understanding Django Views, Templates, and URL Patterns

>**Creating a View:**
>
>1. Create a view function by defining it in the `views.py` file:>
>
>   ```python
>   from django.http import HttpResponse
>
>   def hello(request):
>       return HttpResponse("Hello, Django!")
>   ```
> - To create a view, you define a Python function in the `views.py` file within your Django app. This function takes a `request` parameter and should return an HTTP response.

**Connect the view to a URL pattern by defining it in the `urls.py` file:**

>```python
>from django.urls import path
>from . import views
>
>urlpatterns = [
>    path('hello/', views.hello, name='hello'),
>]
>```
> - In this step, you are connecting the hello view function to a URL pattern /hello/ by defining it in the urls.py file. This allows you to access the hello view when you visit the /hello/ URL in your Django application.
