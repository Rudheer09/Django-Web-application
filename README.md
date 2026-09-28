# 📚 Django Library Management Web Application

A simple **Library Management Web Application** built using **Django** and **SQLite**.

The application allows users to view books stored in a database and add new books through a web form. It demonstrates the integration of **Django Models, Forms, Views, URLs, Templates, ORM, Migrations, and Django Admin**.

---

## 🚀 Features

- 📖 Display all books in the library
- ➕ Add new books using a web form
- 🗄️ Store book information in an SQLite database
- ✅ Track whether a book is available or issued
- 🔢 Display the total number of books
- 🔐 CSRF protection for forms
- 🛠️ Manage books through Django Admin
- 🧩 Uses Django Models, Forms, Views, URLs, Templates, ORM, and Migrations
- 🎨 Simple and clean beginner-friendly user interface

---

## 🛠️ Technologies Used

- **Python**
- **Django 6.1.1**
- **SQLite**
- **HTML**
- **CSS**
- **Django Templates**
- **Django ORM**

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
    ├── static/
    │   └── books/
    │       └── style.css
    │
    ├── __init__.py
    ├── admin.py
    ├── apps.py
    ├── forms.py
    ├── models.py
    ├── tests.py
    ├── urls.py
    └── views.py
