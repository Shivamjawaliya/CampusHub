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

## 🚀 How to Run on Another System

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

- `new_course` (CharField): New course enrollment status

### 5. **Courses Model** (`coourses/models.py`)
- `department_id` (CharField): Associated department
- `course_name` (CharField): Name of the course
- `course_code` (CharField): Unique course code
- `course_instructor` (CharField): Instructor name
- `course_complete` (CharField): Course completion status

### 6. **Assignment Model** (`assignment/models.py`)
- `department_id` (CharField): Department for the assignment
- `course_name` (CharField): Associated course
- `title` (CharField): Assignment title
- `decs` (CharField): Assignment description
- `status` (CharField): Assignment status
- `url` (CharField): Assignment URL/link

### 7. **Assignment Model (v2)** (`assignment1/models.py`)
- `department_id` (CharField): Department for the assignment
- `course_name` (CharField): Associated course
- `title` (CharField): Assignment title
- `desc` (TextField): Assignment description
- `status` (BooleanField): Active/Inactive status
- `file_pdf` (FileField): PDF file upload

### 8. **Assignments Submitted Model** (`assignmentsubmited/models.py`)
- `course_name` (CharField): Course name
- `username` (CharField): Student username
- `title` (CharField): Assignment title
- `pdf_file` (FileField): Submitted PDF file
- `submitted_at` (DateTimeField): Auto-generated submission timestamp

### 9. **Grades Model** (`grades/models.py`)
- `student_id` (CharField): Student identifier
- `course_name` (CharField): Course name
- `title` (CharField): Assignment title
- `grades` (CharField): Grade received

### 10. **Request Course Model** (`requestcourse/models.py`)
- `course_name` (CharField): Requested course name
- `course_code` (CharField): Course code
- `student_email` (CharField): Student email
- `course_teacher` (CharField): Course instructor
- `primary` (CharField): Primary key field
- **Unique Constraint**: Combination of `course_code` and `student_email` must be unique

### 11. **New Course Enrolled Model** (`newcourseenroled/models.py`)
- `course_name` (CharField): Enrolled course name
- `course_code` (CharField): Course code
- `course_instructor` (CharField): Instructor name
- `course_complete` (CharField): Completion status
- `student_id` (CharField): Student identifier
- `primary` (CharField): Primary key field

---

## 🏗️ Project Structure

```
CampusHub-main/
│
├── assignment/              # Assignment management app
│   ├── models.py           # Assignment model (v1)
│   ├── views.py
│   ├── admin.py
│   └── migrations/
│
├── assignment1/            # Enhanced assignment app
│   ├── models.py           # Assignment model (v2) with file uploads
│   ├── forms.py            # Assignment form
│   ├── views.py            # Assignment creation and viewing
│   ├── urls.py
│   └── templates/
│
├── assignmentsubmited/      # Assignment submission tracking
│   ├── models.py           # Submitted assignments model
│   └── views.py
│
├── coourses/               # Course management
│   ├── models.py           # Course model
│   └── views.py
│
├── department/             # Department management
│   ├── models.py           # Department model
│   └── views.py
│
├── grades/                 # Grade management
│   ├── models.py           # Grades model
│   └── views.py
│
├── login/                  # Student login
│   ├── models.py           # Login credentials model
│   └── views.py
│
├── loginstudent/           # Additional student login app
│   └── models.py
│
├── stafflogin/             # Staff login
│   ├── models.py           # Staff login model
│   └── views.py
│
├── studentdetails/         # Student information
│   ├── models.py           # Student details model
│   └── views.py
│
├── requestcourse/          # Course enrollment requests
│   ├── models.py           # Course request model
│   └── views.py
│
├── newcourseenroled/       # Enrolled courses
│   ├── models.py           # Enrollment model
│   └── views.py
│
├── templates/              # HTML templates
│   ├── base.html          # Base template
│   ├── home.html          # Home page
│   ├── studentlogin_page.html
│   ├── stafflogin_page.html
│   ├── studentprofile.html
│   ├── course.html
│   ├── submitassingment.html
│   └── ...
│
├── static/                 # Static files
│   └── index.css          # Main stylesheet
│
├── media/                  # Media uploads
│   ├── assignments/       # Assignment PDFs
│   └── uploads/pdfs/     # Uploaded PDF files
│
├── db.sqlite3             # SQLite database (excluded from git)
├── manage.py              # Django management script
└── projectone/            # Main project settings (excluded from git)
```

---

## 🚀 Installation & Setup

### Prerequisites

- Python 3.7 or higher
- pip (Python package manager)
- Django 3.0 or higher

### Step 1: Clone the Repository

```bash
git clone <repository-url>
cd CampusHub-main
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

### Step 3: Install Dependencies

```bash
pip install django
```

**Note**: If you have a `requirements.txt` file, install all dependencies:
```bash
pip install -r requirements.txt
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

The application will be available at `http://127.0.0.1:8000/`

---

## 📋 Database Operations

### Accessing Django Admin

Navigate to `http://127.0.0.1:8000/admin/` and login with your superuser credentials to manage all database models through the Django admin interface.

### Database Models Management

All models are registered in their respective `admin.py` files. You can:
- View all records
- Add new records
- Edit existing records
- Delete records

### Common Database Queries

The project uses Django ORM for database operations. Example queries:

```python
# Get all courses
from coourses.models import coourses
courses = coourses.objects.all()

# Get assignments for a specific course
from assignment.models import assignment
assignments = assignment.objects.filter(course_name="Python Programming")

# Get student submissions
from assignmentsubmited.models import assignmentsubmited
submissions = assignmentsubmited.objects.filter(course_name="Python Programming")

# Get grades for a student
from grades.models import grades
student_grades = grades.objects.filter(student_id="STU001")
```

---

## 🔧 Configuration

### Settings Location

The Django settings are configured in `projectone/settings.py` (excluded from git for security). Ensure the following are configured:

- `DATABASES`: SQLite database configuration
- `INSTALLED_APPS`: All Django apps listed
- `MEDIA_ROOT` and `MEDIA_URL`: For file uploads
- `STATIC_URL` and `STATIC_ROOT`: For static files

### File Upload Configuration

The project supports PDF file uploads for assignments:
- Upload directory: `media/assignments/` and `media/uploads/pdfs/`
- Maximum file size: Configured in Django settings

---

## 🎯 Key Functionalities

### For Students

1. **Registration & Login**: Register and login with credentials
2. **Course Viewing**: Browse available courses
3. **Course Requests**: Request enrollment in new courses
4. **Assignment Submission**: Submit assignments with PDF files
5. **Grade Viewing**: View grades for submitted assignments
6. **Profile Management**: View and update student profile

### For Staff

1. **Staff Login**: Login with staff credentials
2. **Course Management**: Create and manage courses
3. **Assignment Creation**: Upload assignments with PDF files
4. **Grade Management**: Record and manage student grades
5. **Course Request Handling**: Approve or reject course enrollment requests
6. **Department Management**: Manage departments and courses

---

## 📁 Media Files

The project handles file uploads in the `media/` directory:
- **Assignment PDFs**: `media/assignments/`
- **Uploaded PDFs**: `media/uploads/pdfs/`

**Note**: Ensure proper file permissions are set for the media directory.

---

## 🔒 Security Considerations

1. **Database**: The `db.sqlite3` file is excluded from git (see `.gitignore`)
2. **Settings**: The `projectone/` directory is excluded from git
3. **Passwords**: Currently stored as plain text - consider implementing password hashing
4. **File Uploads**: Implement file validation and size limits

---

## 🛠️ Development

### Running Migrations

```bash
# Create new migrations after model changes
python manage.py makemigrations

# Apply migrations
python manage.py migrate
```

### Creating New Models

1. Define model in `models.py`
2. Create migration: `python manage.py makemigrations <app_name>`
3. Apply migration: `python manage.py migrate`
4. Register in `admin.py` for admin access

---

## 📝 Notes

- This project uses SQLite database for simplicity
- For production, consider migrating to PostgreSQL or MySQL
- Implement proper authentication (Django's built-in auth system recommended)
- Add password hashing for security
- Consider implementing REST API for mobile app integration

---

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

---

## 📄 License

This project is open source and available for educational purposes.

---

## 👨‍💻 Author

CampusHub Development Team

---

## 📞 Support

For issues and questions, please open an issue in the repository.

---

**Last Updated**: 2024

