# Training Management System

A full-stack web application for managing training events, nominees, and feedback collection. Built with Django REST Framework (backend) and React (frontend).

## � Quick Navigation to Setup Guides

⚡ **New to this project?** Start here:

- **[SETUP_COMMANDS.md](SETUP_COMMANDS.md)** ⭐ - **Master guide with all commands to run the project (5-min quick start)**
- **[GITHUB_SETUP.md](GITHUB_SETUP.md)** - Complete Git & GitHub commands reference
- **[backend/requirements.txt](backend/requirements.txt)** - Python dependencies with installation commands
- **[frontend/NPM_COMMANDS.md](frontend/NPM_COMMANDS.md)** - NPM commands and package management

## �📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Complete Setup Commands](#complete-setup-commands)
- [Configuration](#configuration)
- [Running the Application](#running-the-application)
- [All Available Commands](#all-available-commands)
- [API Endpoints](#api-endpoints)
- [Project Structure](#project-structure)
- [Database Models](#database-models)
- [Email Configuration](#email-configuration)
- [Git Configuration](#git-configuration)
- [Troubleshooting](#troubleshooting)

## 🎯 Overview

This Training Management System allows organizations to:

- Create and manage training events
- Nominate employees for training programs
- Send automated email invitations with Accept/Reject options
- Track nominee responses and attendance status
- Collect post-training feedback with ratings and comments

## ✨ Features

- **Admin Dashboard**: Overview of all events, nominees, and their statuses
- **Event Management**: Create, read, update, delete training events
- **Nominee Management**: Add nominees individually or in bulk to events
- **Email Notifications**: Automated invitations and status updates
- **Response Tracking**: Accept/Reject invitation responses from nominees
- **Feedback Collection**: Post-event feedback with ratings (1-5) and comments
- **Session Authentication**: Admin login/logout with session management
- **CORS Support**: Seamless frontend-backend communication

## 🛠️ Tech Stack

### Backend

- **Framework**: Django 4.2
- **API**: Django REST Framework 3.14.0
- **Database**: MySQL 8.x
- **Other Libraries**:
  - django-cors-headers 4.3.1
  - mysqlclient 2.2.1
  - python-dotenv

### Frontend

- **Library**: React 18.2.0
- **Build Tool**: Vite 5.1.3
- **Routing**: React Router DOM 6.22.1
- **HTTP Client**: Axios 1.6.7
- **Styling**: Bootstrap 5.3.3

## 📦 Prerequisites

- **Python 3.8+**
- **Node.js 14+** and npm
- **MySQL 8.0+**
- **Git**

## 📋 Complete Setup Commands

### Quick Start (Windows)

```bash
# 1. Navigate to project directory
cd d:\D\Desktop\Traning_program

# 2. Create and activate virtual environment for backend
cd backend
python -m venv venv
venv\Scripts\activate

# 3. Install backend dependencies
pip install -r requirements.txt

# 4. Create MySQL database
mysql -u root -p
# Then execute:
# CREATE DATABASE training_db;
# EXIT;

# 5. Run migrations
python manage.py makemigrations
python manage.py migrate

# 6. Create superuser
python manage.py createsuperuser

# 7. Start backend server (in this terminal)
python manage.py runserver

# 8. In a NEW terminal, navigate to frontend
cd frontend
npm install

# 9. Start frontend development server
npm run dev
```

### Quick Start (macOS/Linux)

```bash
# 1. Navigate to project directory
cd /path/to/Traning_program

# 2. Create and activate virtual environment
cd backend
python3 -m venv venv
source venv/bin/activate

# 3. Install backend dependencies
pip install -r requirements.txt

# 4. Create MySQL database
mysql -u root -p
# Then execute:
# CREATE DATABASE training_db;
# EXIT;

# 5. Run migrations
python manage.py makemigrations
python manage.py migrate

# 6. Create superuser
python manage.py createsuperuser

# 7. Start backend server
python manage.py runserver

# 8. In a NEW terminal
cd frontend
npm install

# 9. Start frontend
npm run dev
```

## 📦 Prerequisites

## 📥 Installation

### 1. Clone the Repository

```bash
cd d:\D\Desktop\Traning_program
```

### 2. Backend Setup

#### Create Virtual Environment

```bash
cd backend
python -m venv venv
venv\Scripts\activate  # On Windows
# source venv/bin/activate  # On macOS/Linux
```

#### Install Dependencies

The project includes a `requirements.txt` file with all backend dependencies:

```
django==4.2
djangorestframework==3.14.0
django-cors-headers==4.3.1
mysqlclient==2.2.1
```

Install them using:

```bash
pip install -r requirements.txt
```

**Or install individually:**

```bash
pip install django==4.2
pip install djangorestframework==3.14.0
pip install django-cors-headers==4.3.1
pip install mysqlclient==2.2.1
```

**To add new packages and update requirements.txt:**

```bash
# Install new package
pip install <package-name>

# Update requirements.txt
pip freeze > requirements.txt
```

#### Apply Database Migrations

```bash
python manage.py makemigrations
python manage.py migrate
```

#### Create Superuser (Admin)

```bash
python manage.py createsuperuser
# Follow prompts to create admin user
```

### 3. Frontend Setup

Frontend dependencies from `package.json`:

```json
{
  "dependencies": {
    "axios": "^1.6.7",
    "bootstrap": "^5.3.3",
    "react": "^18.2.0",
    "react-dom": "^18.2.0",
    "react-router-dom": "^6.22.1"
  },
  "devDependencies": {
    "@types/react": "^18.2.55",
    "@types/react-dom": "^18.2.19",
    "@vitejs/plugin-react": "^4.2.1",
    "vite": "^5.1.3"
  }
}
```

Install them using:

```bash
cd ../frontend
npm install
```

**Or install specific packages:**

```bash
npm install react@18.2.0
npm install --save-dev vite@5.1.3
```

## ⚙️ Configuration

### Backend Configuration

1. **Create `.env` file** in the `backend/` directory (if needed):

```env
SECRET_KEY=your-secret-key-here
DEBUG=True
ALLOWED_HOSTS=localhost,127.0.0.1
BACKEND_URL=http://localhost:8000
DEFAULT_FROM_EMAIL=your-email@gmail.com
EMAIL_BACKEND=django.core.mail.backends.smtp.EmailBackend
EMAIL_HOST=smtp.gmail.com
EMAIL_PORT=587
EMAIL_USE_TLS=True
EMAIL_HOST_USER=your-email@gmail.com
EMAIL_HOST_PASSWORD=your-app-password
```

2. **Database Configuration** (in `config/settings.py`):

```python
DATABASES = {
    "default": {
        "ENGINE": "django.db.backends.mysql",
        "NAME": "training_db",  # Create this database in MySQL
        "USER": "root",
        "PASSWORD": "your-password",
        "HOST": "localhost",
        "PORT": "3306",
    }
}
```

### Create MySQL Database

```bash
mysql -u root -p
CREATE DATABASE training_db;
EXIT;
```

## 🚀 Running the Application

### Start Backend Server

```bash
cd backend
python manage.py runserver
# Backend runs on http://localhost:8000
```

### Start Frontend Development Server

In a new terminal:

```bash
cd frontend
npm run dev
# Frontend runs on http://localhost:5173
```

### Access the Application

Open your browser and navigate to:

```
http://localhost:5173
```

## 📝 All Available Commands

### Backend Commands

#### Dependency Management

```bash
# Install dependencies from requirements.txt
pip install -r requirements.txt

# Install a specific package
pip install <package-name>

# Upgrade a package
pip install --upgrade <package-name>

# Generate requirements.txt from installed packages
pip freeze > requirements.txt

# Install dependencies with upgrade
pip install --upgrade -r requirements.txt
```

#### Database & Migrations

```bash
# Create new migrations based on model changes
python manage.py makemigrations

# Apply migrations to database
python manage.py migrate

# Run migrations without prompting
python manage.py migrate --noinput

# Rollback to specific migration
python manage.py migrate <app-name> <migration-number>

# View migration status
python manage.py showmigrations

# Create initial migration for an app
python manage.py makemigrations <app-name>

# Backup database (MySQL)
mysqldump -u root -p training_db > backup.sql

# Restore database
mysql -u root -p training_db < backup.sql
```

#### User & Admin Management

```bash
# Create superuser (admin)
python manage.py createsuperuser

# Create regular user
python manage.py shell
# Then: from django.contrib.auth.models import User; User.objects.create_user(username='user', password='pass')

# Change user password
python manage.py changepassword <username>

# Change superuser password
python manage.py shell
# Then: from django.contrib.auth.models import User; u = User.objects.get(username='admin'); u.set_password('new_password'); u.save()
```

#### Development Server

```bash
# Start development server (default port 8000)
python manage.py runserver

# Start on a specific port
python manage.py runserver 8001

# Start on specific IP and port
python manage.py runserver 0.0.0.0:8000

# Enable auto-reload with extra file monitoring
python manage.py runserver --reload
```

#### Static Files & Media

```bash
# Collect static files (for production)
python manage.py collectstatic

# Collect without asking for confirmation
python manage.py collectstatic --noinput

# Clear static files
python manage.py collectstatic --clear
```

#### Django Shell

```bash
# Open Django interactive shell
python manage.py shell

# Example commands in shell:
# from api.models import Event, Nominee, Feedback
# events = Event.objects.all()
# print(events)
```

#### Testing

```bash
# Run all tests
python manage.py test

# Run tests for specific app
python manage.py test api

# Run with verbosity
python manage.py test --verbosity=2

# Run specific test class
python manage.py test api.tests.EventTests
```

#### Cleanup & Maintenance

```bash
# Clear all data tables (dangerous!)
python manage.py flush

# Check project for problems
python manage.py check

# Optimize database
python manage.py dbshell
# Then: OPTIMIZE TABLE <table-name>;

# Remove empty directories
python manage.py findstatic --list
```

#### Virtual Environment

```bash
# Create virtual environment
python -m venv venv

# Activate (Windows)
venv\Scripts\activate

# Activate (macOS/Linux)
source venv/bin/activate

# Deactivate
deactivate

# Delete virtual environment
rmdir /s venv  # Windows
rm -rf venv    # macOS/Linux
```

### Frontend Commands

#### Development

```bash
# Start development server (port 5173)
npm run dev

# Start on custom port
npm run dev -- --port 3000

# Start with host binding
npm run dev -- --host
```

#### Building

```bash
# Build for production
npm run build

# Preview production build
npm run preview

# Build with specific environment
npm run build -- --mode production
```

#### Dependencies

```bash
# Install all dependencies
npm install

# Install specific package
npm install <package-name>

# Install as dev dependency
npm install --save-dev <package-name>

# Upgrade package
npm update <package-name>

# Remove package
npm uninstall <package-name>

# Show installed packages
npm list

# Check for outdated packages
npm outdated

# Update all packages
npm update
```

#### Cleanup

```bash
# Clear npm cache
npm cache clean --force

# Remove node_modules and reinstall
npm ci

# Update package-lock.json
npm install --package-lock-only
```

### MySQL Commands

#### Database Management

```bash
# Connect to MySQL
mysql -u root -p

# List all databases
SHOW DATABASES;

# Create database
CREATE DATABASE training_db;

# Use database
USE training_db;

# Show all tables
SHOW TABLES;

# Describe table structure
DESCRIBE <table-name>;

# Drop database (careful!)
DROP DATABASE training_db;

# Backup database
mysqldump -u root -p training_db > backup.sql

# Restore database
mysql -u root -p training_db < backup.sql
```

#### Common Database Queries

```bash
# In MySQL shell:
# Show all events
SELECT * FROM api_event;

# Show all nominees
SELECT * FROM api_nominee;

# Show all feedback
SELECT * FROM api_feedback;

# Count nominations by status
SELECT status, COUNT(*) FROM api_nominee GROUP BY status;

# Count feedback per event
SELECT event_id, COUNT(*) FROM api_feedback GROUP BY event_id;
```

### Git Commands

```bash
# Initialize git repository
git init

# Add files to staging
git add .

# Commit changes
git commit -m "Your message"

# Push to remote
git push origin main

# Pull from remote
git pull origin main

# Check status
git status

# View commit history
git log

# Create new branch
git checkout -b <branch-name>

# Switch branch
git checkout <branch-name>

# List all branches
git branch -a
```

### Access the Application

Open your browser and navigate to:

```
http://localhost:5173
```

## 🔌 API Endpoints

### Authentication

- **POST** `/api/login/` - Admin login
- **POST** `/api/logout/` - Admin logout
- **GET** `/api/check-auth/` - Check authentication status

### Events

- **GET** `/api/events/` - List all events
- **POST** `/api/events/` - Create new event
- **GET** `/api/events/<id>/` - Get event details
- **PUT** `/api/events/<id>/` - Update event
- **DELETE** `/api/events/<id>/` - Delete event

### Nominees

- **GET** `/api/events/<event_id>/nominees/` - List nominees for event
- **POST** `/api/events/<event_id>/nominees/` - Add nominees
- **GET** `/api/nominee/<id>/` - Get nominee details
- **PUT** `/api/nominee/<id>/` - Update nominee
- **GET** `/api/nominee/<id>/accept/` - Accept invitation
- **GET** `/api/nominee/<id>/reject/` - Reject invitation

### Feedback

- **POST** `/api/feedback/` - Submit feedback
- **GET** `/api/feedback/` - List all feedback
- **GET** `/api/events/<event_id>/feedback/` - Feedback for specific event

## 📁 Project Structure

```
Traning_program/
├── .gitignore                  # Root level git ignore rules
├── README.md                   # Project documentation
├── backend/
│   ├── .gitignore             # Backend specific git ignore rules
│   ├── manage.py
│   ├── requirements.txt        # Python dependencies
│   ├── api/
│   │   ├── __init__.py
│   │   ├── models.py           # Event, Nominee, Feedback models
│   │   ├── views.py            # API endpoints
│   │   ├── serializers.py       # DRF serializers
│   │   ├── urls.py             # API routing
│   │   ├── utils.py            # Email utility functions
│   │   ├── admin.py            # Django admin configuration
│   │   ├── apps.py             # App configuration
│   │   └── migrations/          # Database migrations
│   │       ├── __init__.py
│   │       ├── 0001_initial.py
│   │       └── __pycache__/
│   └── config/
│       ├── __init__.py
│       ├── settings.py         # Django settings
│       ├── urls.py             # Main URL routing
│       ├── wsgi.py             # WSGI configuration
│       └── __pycache__/
├── frontend/
│   ├── .gitignore             # Frontend specific git ignore rules
│   ├── package.json           # Node dependencies
│   ├── package-lock.json      # Locked versions
│   ├── vite.config.js         # Vite configuration
│   ├── index.html
│   ├── dist/                  # Built files (generated)
│   ├── node_modules/          # Dependencies (generated)
│   ├── src/
│   │   ├── main.jsx           # React entry point
│   │   ├── App.jsx            # Main app component
│   │   ├── index.css
│   │   ├── api/
│   │   │   └── axios.js       # Axios API configuration
│   │   └── components/
│   │       ├── Login.jsx
│   │       ├── Dashboard.jsx
│   │       ├── EventForm.jsx
│   │       ├── EventList.jsx
│   │       ├── NomineeForm.jsx
│   │       ├── NomineeList.jsx
│   │       ├── NomineeResponse.jsx
│   │       ├── FeedbackForm.jsx
│   │       └── Navbar.jsx
│   └── public/                # Static assets
└── [project-root files]
```

### Files to Commit to Git ✅

- `.gitignore` files
- `README.md`
- Source code (`.py`, `.jsx`, `.js`)
- Configuration files (`settings.py`, `vite.config.js`)
- Metadata (`package.json`, `requirements.txt`)

### Files NOT Committed (via .gitignore) ❌

- `venv/`, `node_modules/` (dependencies directories)
- `.env` files (credentials)
- `*.log` files
- `db.sqlite3` (database)
- `dist/` (build output)
- IDE files (`.vscode/`, `.idea/`)
- `__pycache__/` (Python cache)

## 📊 Database Models

### Event

```python
- title: CharField(max_length=255)
- description: TextField
- date: DateField
- time: TimeField
- venue: CharField(max_length=255)
- created_at: DateTimeField (auto_now_add=True)
```

### Nominee

```python
- event: ForeignKey(Event)
- name: CharField(max_length=255)
- email: EmailField
- employee_id: CharField(max_length=50)
- department: CharField(max_length=255)
- status: CharField (Pending, Accepted, Rejected, Attended)
```

### Feedback

```python
- nominee: OneToOneField(Nominee)
- rating: IntegerField (1-5)
- comments: TextField
- suggestions: TextField
- submitted_at: DateTimeField (auto_now_add=True)
```

## 📧 Email Configuration

The system sends automated emails for:

1. **Invitation Emails**: Sent when nominees are added (includes Accept/Reject links)
2. **Admin Notifications**: Notifies admin when nominee accepts/rejects
3. **Feedback Confirmations**: Confirms feedback submission

### Gmail SMTP Setup

1. Enable 2-factor authentication on your Gmail account
2. Create an [App Password](https://myaccount.google.com/apppasswords)
3. Use the app password in EMAIL_HOST_PASSWORD

## � Git Configuration

### .gitignore Files

This project includes `.gitignore` files at three levels to properly exclude files from version control:

#### Root .gitignore (`.gitignore`)

Ignores files for the entire project:

- Python cache files (`__pycache__/`, `*.pyc`)
- Virtual environments (`venv/`, `env/`)
- Node modules (`node_modules/`)
- Environment variables (`.env`, `.env.local`)
- IDE files (`.vscode/`, `.idea/`)
- OS files (`.DS_Store`, `Thumbs.db`)
- Build directories (`dist/`, `build/`)
- Database files (`*.log`, `db.sqlite3`)
- Testing files (`.pytest_cache/`, `.coverage`)

#### Backend .gitignore (`backend/.gitignore`)

Backend-specific exclusions:

- Django logs (`*.log`)
- SQLite database (`db.sqlite3`)
- Local settings (`local_settings.py`)
- Python bytecode files
- Virtual environment
- IDE configuration files
- MySQL dumps (optional)
- Django migrations (optional - uncomment if desired)

#### Frontend .gitignore (`frontend/.gitignore`)

Frontend-specific exclusions:

- Node modules (`node_modules/`)
- Package lock files (`package-lock.json`, `yarn.lock`)
- Build output (`dist/`, `dist-ssr/`)
- Environment files (`.env`, `.env.local`)
- IDE files
- OS files
- Test coverage

### Setting Up Git

```bash
# Initialize repository
git init

# Configure user (if not already configured)
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"

# Add all files (respects .gitignore)
git add .

# Create initial commit
git commit -m "Initial commit: Training Management System"

# View ignored files (to verify)
git status --ignored
```

### What Gets Ignored

The `.gitignore` files ensure these are NOT tracked:

| File/Folder          | Reason                     |
| -------------------- | -------------------------- |
| `venv/`, `env/`      | Local virtual environments |
| `node_modules/`      | NPM dependencies           |
| `.env`, `.env.local` | Sensitive credentials      |
| `*.log`              | Django/application logs    |
| `db.sqlite3`         | Local development database |
| `dist/`, `build/`    | Build output               |
| `.vscode/`, `.idea/` | IDE configuration          |
| `__pycache__/`       | Python cache               |
| `.DS_Store`          | macOS system files         |
| `Thumbs.db`          | Windows system files       |

### Recommended Git Workflow

```bash
# Before pushing
git status                # Check what will be committed
git diff                  # Review changes
git add .                 # Stage changes (ignores files from .gitignore)
git commit -m "Description"  # Commit
git log --oneline        # View commit history

# For branches
git checkout -b feature/new-feature  # Create feature branch
git push origin feature/new-feature  # Push to remote
# Create Pull Request on GitHub

# Keep main clean
git checkout main
git pull origin main
git merge feature/new-feature
git push origin main
```

## �🐛 Troubleshooting

### MySQL Connection Error

```
Error: No module named 'MySQLdb'
```

**Solution**: Install mysqlclient

```bash
pip install mysqlclient
```

### CORS Error

**Solution**: Ensure `corsheaders` is installed and configured in settings.py

### Email Not Sending

- Check SMTP credentials in `.env`
- Verify email account allows less secure apps (if not using app password)
- Check Django email backend configuration

### Port Already in Use

- Backend: Change in manage.py or use `python manage.py runserver 8001`
- Frontend: Change in vite.config.js or use `npm run dev -- --port 3000`

### Database Migration Error

```bash
python manage.py migrate --run-syncdb
```

## 📝 Development Notes

- **Time Zone**: Set to Asia/Kolkata (IST)
- **Debug Mode**: Enabled in development; disable for production
- **Authentication**: Session-based (not JWT)
- **CORS**: Allow all origins in development (restrict in production)

## 🔐 Security Recommendations

1. Change `SECRET_KEY` in production
2. Set `DEBUG=False` in production
3. Restrict `ALLOWED_HOSTS`
4. Use environment variables for sensitive data
5. Configure HTTPS
6. Use strong database passwords
7. Implement rate limiting on API endpoints

## � Additional Documentation & Guides

### Quick Setup (NEW!)

- **[SETUP_COMMANDS.md](SETUP_COMMANDS.md)** ⭐ - Complete guide with all commands needed to run the project
  - Quick start (5 minutes)
  - Full step-by-step setup
  - All backend, frontend, and database commands
  - GitHub workflow
  - Troubleshooting table

### Detailed Guides

- **[GITHUB_SETUP.md](GITHUB_SETUP.md)** - Git and GitHub reference
  - Initial GitHub setup
  - 50+ Git commands
  - Feature branch workflow
  - Merge conflict resolution
  - SSH configuration
  - Commit message best practices

- **[backend/requirements.txt](backend/requirements.txt)** - Python dependencies
  - Package descriptions and documentation links
  - Installation commands
  - Dependency management commands
  - Optional packages for extensions

- **[frontend/NPM_COMMANDS.md](frontend/NPM_COMMANDS.md)** - NPM and Node reference
  - Package dependency table
  - Development server commands
  - Build and deployment commands
  - 50+ npm commands
  - Troubleshooting npm issues
  - Adding common packages

### Configuration Files

- **[.gitignore](.gitignore)** - Root level version control exclusions
- **[backend/.gitignore](backend/.gitignore)** - Django-specific exclusions
- **[frontend/.gitignore](frontend/.gitignore)** - Node/React exclusions

## �📄 License

This project is created for training purposes.

## 👨‍💻 Support

For issues or questions, please check the troubleshooting section or review the code comments in respective files.

---

**Last Updated**: February 2026
