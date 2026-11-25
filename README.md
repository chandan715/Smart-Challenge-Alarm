# Smart Challenge Alarm

A smart alarm application that makes you **solve challenges before the alarm can be stopped**, so you cannot dismiss it half asleep and go back to bed.

> **Status:** In development (Version 1, web prototype). Built as a learning and portfolio project.

---

## Table of Contents

1. [Problem](#problem)
2. [Solution](#solution)
3. [Features](#features)
4. [Business Rules](#business-rules)
5. [Tech Stack](#tech-stack)
6. [Project Structure](#project-structure)
7. [Database Design](#database-design)
8. [Getting Started](#getting-started)
9. [Roadmap](#roadmap)
10. [Documentation](#documentation)

---

## Problem

Traditional alarms can be stopped with a single tap. Sleepy users often dismiss the alarm and fall asleep again.

## Solution

When the alarm rings, the user must complete the selected challenges (math, typing, memory, and more). Only after all challenges are solved does the system verify the result and dismiss the alarm.

**Workflow**

1. The user creates an alarm (for example, 6:00 AM).
2. The alarm rings.
3. The user tries to stop it.
4. The application shows the selected challenges.
5. The user completes all required challenges.
6. The system verifies completion and dismisses the alarm.

---

## Features

### Core (Version 1)

- [ ] User registration and login
- [ ] Create, update, delete and manage alarms
- [ ] Select alarm time and recurring days
- [ ] Select multiple challenge types
- [ ] Select difficulty (Easy, Medium, Hard)
- [ ] Math challenges (multiple questions)
- [ ] Memory challenges
- [ ] Typing challenges
- [ ] Missing-letter word challenges
- [ ] QR code scanning
- [ ] Alarm history
- [ ] Performance tracking and statistics

### Advanced (Planned, added gradually)

- Physical activities (push-ups, squats, jumping jacks)
- Camera-based activity verification
- AI-based activity recognition
- Personalized challenge generation
- Smart difficulty adjustment

---

## Business Rules

| ID | Rule |
|---|---|
| BR-01 | Challenges run in the order the user selected them. |
| BR-02 | A wrong answer shows a **new** question. This repeats with no limit until the user answers correctly. Every question, answer and result is saved. |
| BR-03 | There is **no snooze**. The alarm stops only after all challenges are completed. |
| BR-04 | An alarm session has a status: `RINGING` → `IN_PROGRESS` → `COMPLETED` (or `MISSED`). Progress is saved, so the user can continue if the app closes. |
| BR-05 | The alarm rings for a maximum of 15 minutes (configurable later). If not completed, the session becomes `MISSED`. |

---

## Tech Stack

**Current**

- Python, Django, Django REST Framework
- SQLite (development database)
- Git and GitHub

**Planned (introduced only when needed)**

- PostgreSQL
- HTML, CSS, JavaScript, then React.js
- Flutter or native Android integration (reliable mobile alarm scheduling)
- Pytest, Postman, Swagger / OpenAPI
- Celery and Redis
- Docker, Nginx, Gunicorn, Linux
- GitHub Actions (CI/CD)

---

## Project Structure

```
Smart-Challenge-Alarm/
├── backend/
│   ├── config/          # Django project (settings, main URLs)
│   ├── alarms/          # Alarm app (models, views, APIs)
│   └── manage.py
├── requirements.txt
├── SmartAlarm_SRS.md    # Software Requirements Specification
├── .gitignore
└── README.md
```

---

## Database Design

| Table | Purpose |
|---|---|
| `User` | Django built-in user (username, email, password) |
| `Alarm` | Alarm configuration (owner, label, time, active) |
| `AlarmChallenge` | Challenge types and difficulty chosen for an alarm, with order |
| `AlarmSession` | One ringing event (status, start time, completion time, progress) |
| `QuestionAttempt` | Every question shown, the user's answer, and whether it was correct |

**Relationships**

- One User has many Alarms
- One Alarm has many AlarmChallenges
- One Alarm has many AlarmSessions
- One AlarmSession has many QuestionAttempts

An ER diagram will be added to this repository.

---

## Getting Started

### Prerequisites

- Python 3.11 or later
- Git

### Setup (Windows PowerShell)

```powershell
# 1. Clone the repository
git clone https://github.com/chandan715/Smart-Challenge-Alarm
cd Smart-Challenge-Alarm

# 2. Create and activate a virtual environment
python -m venv venv
venv\Scripts\activate

# 3. Install dependencies
pip install -r requirements.txt

# 4. Create database tables
cd backend
python manage.py migrate

# 5. Create an admin user (for development)
python manage.py createsuperuser

# 6. Run the server
python manage.py runserver
```

Open `http://127.0.0.1:8000/` in your browser. Django Admin is at `http://127.0.0.1:8000/admin/`.

### Mac / Linux

Activate the virtual environment with `source venv/bin/activate` instead of step 2's activation command. All other steps are the same.

---

## Roadmap

- [x] Project idea and SRS draft
- [x] Business rules
- [x] Django project setup
- [x] Database design (tables and relationships)
- [ ] `Alarm` model and Django Admin
- [ ] `AlarmChallenge`, `AlarmSession`, `QuestionAttempt` models
- [ ] Authentication (register and login APIs)
- [ ] Alarm CRUD APIs with DRF
- [ ] Challenge generation and answer verification
- [ ] Alarm history and statistics APIs
- [ ] Testing with Pytest
- [ ] Web frontend
- [ ] Docker and deployment
- [ ] Mobile integration

---

## Documentation

- [Software Requirements Specification](SmartAlarm_SRS.md)

---

## Author

Built by **Chandan Nayak** as a portfolio project to learn real-world backend development.