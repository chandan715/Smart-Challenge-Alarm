# Smart Challenge Alarm – Project Context

> Give this file to the AI at the start of every new chat.
> Update Section 9 (Current Progress) at the end of every work session.

---

## 1. Project Overview

I am developing a portfolio-level project called **Smart Challenge Alarm**.

**Problem:** People often dismiss alarms while sleepy and go back to sleep. Traditional alarms can be stopped with a single tap. I faced this problem myself.

**Solution:** A smart alarm application that requires users to complete selected challenges before dismissing the alarm.

### Workflow
1. User creates an alarm (e.g., 6:00 AM).
2. Alarm rings.
3. User attempts to stop it.
4. Application displays the selected challenges.
5. User completes all required challenges.
6. System verifies completion and dismisses the alarm.

---

## 2. Planned Features

**Core Features:**
- User registration and login
- Create, update, delete and manage alarms
- Alarm time and recurring days
- Multiple challenge types per alarm
- Difficulty (Easy, Medium, Hard)
- Math, memory, typing, missing-letter word challenges
- QR code scanning
- Alarm history
- Performance tracking and statistics

**Advanced Features (added gradually, later):**
- Physical activities (push-ups, squats, jumping jacks, dancing)
- Camera-based activity verification
- AI-based activity recognition
- Personalized challenge generation
- Smart difficulty adjustment

---

## 3. Technology Stack

- Backend: Python, Django, Django REST Framework
- Database: SQLite now, PostgreSQL later
- Frontend: HTML, CSS, JavaScript, later React.js
- Mobile: Flutter / native Android integration (later)
- API testing: Postman
- Version control: Git and GitHub
- Advanced backend: Celery, Redis
- Testing: Pytest
- Deployment: Docker, Nginx, Gunicorn, Linux
- CI/CD: GitHub Actions
- Documentation: Swagger / OpenAPI

**Introduce technologies only when required.**

---

## 4. My Current Knowledge

- I know Python fundamentals, OOP, Django basics and basic SQL.
- I have limited DRF knowledge.
- I am learning relationships (ForeignKey) and real-world backend development.
- My English is simple. Please use simple words, short explanations and practical examples.

I want to learn DRF and backend development **while building**, without finishing every tutorial first.

---

## 5. Software Engineering Approach

Phases:
1. Requirement analysis (SRS, user stories, use cases)
2. Database design (ER diagram, relationships, constraints, indexing)
3. Backend development (models, serializers, views, APIs, CRUD, auth, permissions, pagination, filtering)
4. Business logic (challenge generation, answer verification, alarm management)
5. Frontend (HTML, CSS, JavaScript, then React)
6. Testing (unit, integration, API)
7. Advanced backend (Celery, Redis, caching, logging, security, optimization)
8. Deployment (Linux, Docker, Nginx, Gunicorn, cloud, CI/CD)

---

## 6. Project Decisions

- Version 1 has one normal user role. No separate administrator role.
- Django Admin is used internally for development only.
- The system automatically generates challenges, verifies answers and tracks history.
- Reliable mobile alarm scheduling must eventually use native Android functionality.
- Start with a web prototype, add mobile integration later.

### Business Rules (final)

| ID | Rule |
|---|---|
| BR-01 | Challenges run in the order the user selected them. Order has no other meaning. |
| BR-02 | A wrong answer shows a NEW question. Repeats with no limit until correct. Every question, answer and result is saved. |
| BR-03 | No snooze. The alarm stops only after all challenges are completed. |
| BR-04 | Session status: RINGING -> IN_PROGRESS -> COMPLETED (or MISSED). Progress is saved if the app closes; the user continues where they stopped. |
| BR-05 | Alarm rings for a maximum of 15 minutes (keep it as a setting, not hard-coded). Then status becomes MISSED. MISSED counts in history and statistics. |

---

## 7. Database Design (decided)

**Concept:** Alarm = configuration. AlarmSession = one ringing event.

| Table | Columns |
|---|---|
| User | Django built-in (`settings.AUTH_USER_MODEL`). Not created by me. |
| Alarm | user (FK, CASCADE, related_name="alarms"), label, time, is_active, created_at (auto_now_add), updated_at (auto_now) |
| AlarmChallenge | alarm (FK), challenge_type (MATH, TYPING, MEMORY, MISSING_LETTER, QR), difficulty (EASY, MEDIUM, HARD), order, question_count. Unique together: (alarm, challenge_type) |
| AlarmSession | alarm (FK), scheduled_time, started_time (nullable), completed_time (nullable), status (RINGING, IN_PROGRESS, COMPLETED, MISSED), current_challenge_order |
| QuestionAttempt | session (FK), challenge_type, question_text, correct_answer, user_answer (nullable), is_correct, created_at |

**Relationships**
- One User has many Alarms
- One Alarm has many AlarmChallenges
- One Alarm has many AlarmSessions
- One AlarmSession has many QuestionAttempts

**Left for later:** `repeat_days` (to be added as a proper separate structure, not a text column).

**Rule I learned:** the ForeignKey goes on the "many" side.

---

## 8. My Learning Approach

I prefer **AI-assisted development, not vibe coding**.

For every feature:
1. Understand the requirement.
2. Learn the necessary concept.
3. Try implementing it myself.
4. Ask AI to review my code.
5. Understand every correction.
6. Test and debug.
7. Move to the next feature.

**What I expect from the AI:**
- Act as my senior backend developer and mentor.
- Continue from my current progress. Do not restart.
- Explain the why and how, with practical examples.
- Give assignments and review my code. Do not generate large amounts of code without explanation.
- Let me try first. Do not only give solutions.
- Do not skip database design or requirement analysis.
- Do not introduce advanced technologies early.
- Keep the project maintainable, scalable and good for a portfolio.

---

## 9. Current Progress (UPDATE THIS EVERY SESSION)

**Environment:** Windows, PowerShell, Python 3.11.

**Folder structure**
```
Smart-Challenge-Alarm/
├── backend/
│   ├── config/        (Django project)
│   ├── alarms/        (Django app)
│   └── manage.py
├── venv/
├── requirements.txt
├── SmartAlarm_SRS.md
├── PROJECT_CONTEXT.md
└── README.md
```

**Done**
- [x] SRS draft created
- [x] Business rules finalized (BR-01 to BR-05)
- [x] Django project `config` and app `alarms` created inside `backend/`
- [x] DRF installed and both apps added to `INSTALLED_APPS`
- [x] Git initialized
- [x] README.md created
- [x] Database tables and relationships designed
- [x] Alarm model code written

**In progress**
- [ ] Run `makemigrations` and `migrate` for Alarm
- [ ] Register Alarm in `admin.py`, create superuser, add one alarm in Django Admin

**Next**
1. Write the `AlarmChallenge` model myself (then AI reviews).
2. Write `AlarmSession` and `QuestionAttempt` models.
3. DRF serializers and views for Alarm CRUD.
4. Authentication (register and login).
5. Challenge generation and answer verification.

**Concepts learned so far**
- Why we use a virtual environment
- Django project vs app
- ForeignKey, `on_delete`, `related_name`, and "FK goes on the many side"
- A missing comma between strings in a list joins them silently (caused a `ModuleNotFoundError`)

**Open questions / problems**
- None right now.

---

## 10. Instruction for the AI (paste at the start of a new chat)

> Continue my Smart Challenge Alarm project using the context above.
> Do not restart. Act as my senior backend mentor. Use simple English.
> Start from "Current Progress" and give me the next assignment.