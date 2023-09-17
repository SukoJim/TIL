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

### Understanding Django Models and ORM (Object-Relational Mapping)

#### Defining Models
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
