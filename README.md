# StreamIT

A Netflix-style clone built with Django.
This repository contains the web app source, a database dump (streamit.sql), and project scaffolding. 
GitHub

Table of contents

About

Features

Tech stack

Prerequisites

Installation & quick start

Database

Running locally

Deployment

Project structure

Contribute

License

About

StreamIT is a small clone of Netflix — a streaming catalogue web app demonstrating typical streaming-site features (catalogue, categories, maybe user/auth). The repository contains several Django app folders and a SQL dump for populating the database. 
GitHub
+1

Features (example)

Browse movies / shows by category

Movie/show detail pages

Admin interface for content management (Django admin)

User authentication (if included)

Adjust this section to reflect the exact features implemented in your code.

Tech stack

Python (Django) — repository contains manage.py and Python code. 
GitHub

Database dump included (streamit.sql) for pre-populated data. 
GitHub

Prerequisites

Python 3.8+

pip

(Optional) PostgreSQL / MySQL if you want to import streamit.sql into an RDBMS; otherwise Django’s default SQLite works for local testing.

Virtual environment tool (recommended): venv or virtualenv

Installation & quick start (local)

Clone the repository

git clone https://github.com/Siddanth-pai/StreamIT.git
cd StreamIT


Create a virtual environment and activate it

python -m venv venv
# Mac / Linux
source venv/bin/activate
# Windows (Powershell)
venv\Scripts\Activate.ps1


Install dependencies
If there is a requirements.txt, install it:

pip install -r requirements.txt


If there is no requirements.txt, install Django (and other libs used in the project as needed):

pip install django
# install additional packages if your project uses them (e.g. pillow, djangorestframework)


Database / migrations

If you want to start fresh with Django’s DB:

python manage.py makemigrations
python manage.py migrate


If you prefer to import the included streamit.sql, inspect the SQL file and import into your chosen DB (Postgres/MySQL). See the Database
 section below.

Create a superuser (for admin access)

python manage.py createsuperuser


Run the development server

python manage.py runserver


Open http://127.0.0.1:8000/ in your browser.

Database

This repo includes a streamit.sql SQL dump (useful for pre-populating the database). The exact import steps depend on which RDBMS you choose:

PostgreSQL

Create database: createdb streamit_db

Import: psql streamit_db < streamit.sql

MySQL

Create DB and import using mysql -u username -p streamit_db < streamit.sql

SQLite
If streamit.sql is for another RDBMS, it may not be directly compatible. You can run Django migrations to create a fresh SQLite DB and then add sample data via fixtures or the admin.

Always inspect streamit.sql before importing to confirm compatibility and security.

Configuration & environment

If the project expects environment variables (e.g., SECRET_KEY, DEBUG, DATABASE_URL), create a .env file or export env variables before running.

Check settings.py (or settings module under the project folder) for expected configuration keys and adjust accordingly.

Running tests

If the repository contains tests:

python manage.py test


(If not present, add unit tests to cover views, models and forms.)

Project structure (high-level)
StreamIT/
├─ manage.py
├─ streamIT/         # main Django project package (settings, urls, wsgi)
├─ mysite/           # (possible additional app or deployment folder)
├─ streamitfinal/    # (possible additional app/final version)
├─ streamit.sql      # DB dump
├─ .gitignore
└─ README.md         # <-- add this file


(Adjust this tree to reflect the actual folders and app names in your repo.) 

Deployment

For production, set DEBUG = False and configure a production-ready DB (Postgres), static/media hosting (S3 or similar), and a WSGI server (Gunicorn + Nginx).

Use environment variables for sensitive data.

Consider containerizing with Docker for easier deployment.

Contribute

Fork the repo

Create a feature branch (git checkout -b feature/your-feature)

Commit your changes and push (git push origin feature/your-feature)

Open a pull request with a description of changes

Notes & TODOs

Update the Features section with exact implemented features from the code.

Add requirements.txt if missing (run pip freeze > requirements.txt in the venv after installing dependencies).

Add screenshots or a short demo GIF to showcase the UI.

Consider adding unit tests and CI (GitHub Actions) for automated checks.
