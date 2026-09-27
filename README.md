# 📚 Django Library Management Web Application

A simple **Library Management Web Application** built using **Django** and **SQLite**.
The application allows users to view books in the library and add new books through a web form. Books are stored in a database using Django's ORM.

---

## 🚀 Features

* 📖 Display all books in the library
* ➕ Add new books using a web form
* 🗄️ Store book information in an SQLite database
* ✅ Track whether a book is available or issued
* 🔢 Display the total number of books
* 🔐 CSRF protection for forms
* 🛠️ Manage books through Django Admin
* 🧩 Uses Django Models, Forms, Views, URLs, Templates and Migrations

---

## 🛠️ Technologies Used

* **Python**
* **Django 6.1.1**
* **SQLite**
* **HTML**
* **Django Templates**
* **Django ORM**

---

## 📂 Project Structure

```text
project2_library/
│
├── manage.py
├── db.sqlite3
│
├── config/
│   ├── __init__.py
│   ├── settings.py
│   ├── urls.py
│   ├── asgi.py
│   └── wsgi.py
│
└── books/
    ├── migrations/
    │   ├── 0001_initial.py
    │   └── __init__.py
    │
    ├── templates/
    │   └── books/
    │       ├── book_list.html
    │       └── add_book.html
    │
    ├── admin.py
    ├── apps.py
    ├── forms.py
    ├── models.py
    ├── tests.py
    ├── urls.py
    └── views.py
```

---

## 🗄️ Database Model

The application contains a `Book` model with the following fields:

| Field            | Type         | Description                             |
| ---------------- | ------------ | --------------------------------------- |
| `title`          | CharField    | Name of the book                        |
| `author`         | CharField    | Author of the book                      |
| `year_published` | IntegerField | Year the book was published             |
| `is_available`   | BooleanField | Indicates whether the book is available |

Django automatically creates an `id` field as the primary key.

### Model

```python
class Book(models.Model):
    title = models.CharField(max_length=200)
    author = models.CharField(max_length=100)
    year_published = models.IntegerField()
    is_available = models.BooleanField(default=True)

    def __str__(self):
        return self.title
```

---

## 📝 Forms

The project uses Django's `ModelForm` to create the book-entry form.

```python
class BookForm(forms.ModelForm):
    class Meta:
        model = Book
        fields = [
            'title',
            'author',
            'year_published',
            'is_available'
        ]
```

Using `ModelForm` automatically creates form fields based on the `Book` model and performs validation before saving the data.

---

## 👁️ Views

The application contains two main views.

### 1. Book List

The `book_list` view retrieves all books from the database and displays them on the library page.

```python
def book_list(request):
    books = Book.objects.all()
    return render(
        request,
        'books/book_list.html',
        {'books': books}
    )
```

### 2. Add Book

The `add_book` view handles both displaying the form and processing submitted book data.

```python
def add_book(request):
    if request.method == 'POST':
        form = BookForm(request.POST)

        if form.is_valid():
            form.save()
            return redirect('book_list')
    else:
        form = BookForm()

    return render(
        request,
        'books/add_book.html',
        {'form': form}
    )
```

---

## 🔗 URL Routing

The project uses Django URL routing to connect URLs with views.

### Project URLs

```python
urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('books.urls')),
]
```

### Books URLs

| URL       | View         | Purpose                 |
| --------- | ------------ | ----------------------- |
| `/`       | `book_list`  | Display all books       |
| `/add/`   | `add_book`   | Add a new book          |
| `/admin/` | Django Admin | Manage database records |

---

## 🎨 Templates

### Book List

The library page displays:

* Book number
* Title
* Author
* Publication year
* Availability status
* Total number of books
* Link to add a new book

Example:

```text
My Book Library

Total books: 3

No. | Title | Author | Year | Status
---------------------------------------
1   | Book A | Author A | 2024 | Available
2   | Book B | Author B | 2023 | Issued
```

### Add Book

The `add_book.html` template provides a form where users can enter book information.

The form uses:

```django
{% csrf_token %}
```

to provide CSRF protection.

---

## 🔄 Database Migrations

Django migrations are used to create and update the database schema.

The initial migration creates the `Book` table with:

* `id`
* `title`
* `author`
* `year_published`
* `is_available`

Run migrations using:

```bash
python manage.py makemigrations
python manage.py migrate
```

---

## ⚙️ Installation and Setup

### 1. Clone the repository

```bash
git clone https://github.com/Rudheer09/Django-Web-application.git
```

### 2. Navigate to the project

```bash
cd Django-Web-application/project2_library
```

### 3. Create a virtual environment

```bash
python -m venv venv
```

### 4. Activate the virtual environment

#### Windows

```bash
venv\Scripts\activate
```

#### macOS/Linux

```bash
source venv/bin/activate
```

### 5. Install Django

```bash
pip install django
```

### 6. Apply migrations

```bash
python manage.py migrate
```

### 7. Start the development server

```bash
python manage.py runserver
```

Open the application in your browser:

```text
http://127.0.0.1:8000/
```

---

## 🔐 Django Admin

The project also supports Django's built-in admin interface.

Create an administrator account:

```bash
python manage.py createsuperuser
```

Then open:

```text
http://127.0.0.1:8000/admin/
```

The `Book` model is registered in `admin.py`, allowing administrators to view and manage books.

---

## 🔄 How the Application Works

The basic flow of the application is:

```text
User
  ↓
Browser
  ↓
Django URL
  ↓
View
  ↓
Model / ModelForm
  ↓
SQLite Database
  ↓
View
  ↓
HTML Template
  ↓
Browser
```

### Adding a Book

```text
User opens /add/
        ↓
Django displays BookForm
        ↓
User enters book details
        ↓
Form submitted using POST
        ↓
Django validates the form
        ↓
Book saved using Django ORM
        ↓
Redirect to /
        ↓
New book appears in library
```

---

## 📌 Django Concepts Demonstrated

This project demonstrates the following core Django concepts:

* **Project and App structure**
* **Django Models**
* **SQLite Database**
* **Django ORM**
* **ModelForm**
* **Views**
* **URL Routing**
* **Django Templates**
* **Template Tags**
* **Migrations**
* **Django Admin**
* **CSRF Protection**
* **HTTP GET and POST requests**
* **Redirects**

---

## 🎯 Learning Objectives

The main objective of this project is to understand how the major components of a Django web application work together.

After implementing this project, the following concepts can be demonstrated:

1. Creating a Django project and application
2. Designing a database model
3. Performing database operations using Django ORM
4. Creating forms using ModelForm
5. Handling GET and POST requests
6. Connecting URLs with views
7. Rendering dynamic data using templates
8. Creating and applying migrations
9. Registering models with Django Admin
10. Building a basic database-driven web application

---

## 🔮 Future Enhancements

The application can be extended with:

* 🔍 Search books by title or author
* ✏️ Edit existing books
* 🗑️ Delete books
* 📅 Track issue and return dates
* 👤 Add users and authentication
* 📚 Add categories and genres
* 📊 Add a dashboard with library statistics
* 📱 Improve responsive UI
* 🔎 Add filtering and sorting
* 👥 Implement student/member management

---

## 👨‍💻 Author

**Rudheer09**

GitHub:
https://github.com/Rudheer09

---

## 📄 License

This project is intended for **educational and academic purposes**.
