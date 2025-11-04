# CampusHub - Campus Management System

## 📚 Introduction

**CampusHub** is a comprehensive Django-based web application designed to manage campus operations, student-staff interactions, course management, assignments, and grading systems. This project serves as a complete database-driven solution for educational institutions to streamline their academic processes.

### Key Features

- **User Authentication**: Separate login systems for students and staff members
- **Course Management**: Create, view, and manage courses with department associations
- **Assignment System**: Upload assignments, submit assignments, and track submission status
- **Grade Management**: Record and manage student grades for assignments
- **Department Management**: Organize courses and students by departments
- **Course Enrollment**: Students can request courses and enroll in new courses
- **Student Profiles**: Comprehensive student dashboard with profile information

The project uses Django ORM with SQLite database and includes 11 database models covering departments, courses, assignments, student/staff authentication, grades, and course enrollment.

---

## 🚀 How to Run

### Prerequisites

- Python 3.7 or higher
- pip (Python package manager)

### Step 1: Clone or Download the Project

```bash
# If using Git
git clone <repository-url>
cd CampusHub-main

# Or extract the project folder if downloaded as ZIP
```

### Step 2: Create Virtual Environment (Recommended)

```bash
# Create virtual environment
python3 -m venv venv

# Activate virtual environment
# On macOS/Linux:
source venv/bin/activate

# On Windows:
venv\Scripts\activate
```

### Step 3: Install Django

```bash
pip install django
```

### Step 4: Database Setup

```bash
# Create database migrations
python manage.py makemigrations

# Apply migrations to create database tables
python manage.py migrate

# Create superuser (optional, for admin access)
python manage.py createsuperuser
```

### Step 5: Run the Development Server

```bash
python manage.py runserver
```

### Step 6: Access the Application

- Open your browser and navigate to: `http://127.0.0.1:8000/`
- For admin panel: `http://127.0.0.1:8000/admin/` (use superuser credentials)

### Troubleshooting

- **If migrations fail**: Ensure all Django apps are properly installed and check `projectone/settings.py` for `INSTALLED_APPS`
- **If port 8000 is busy**: Use `python manage.py runserver 8080` to run on a different port
- **If static files don't load**: Run `python manage.py collectstatic` (if configured)

---

**Note**: The `projectone/` directory containing Django settings is excluded from git. You may need to create or configure the settings file if it's missing.

