# Smart Challenge Alarm
## Software Requirements Specification (SRS)

### 1. Project Introduction

Smart Challenge Alarm is a smart alarm application designed to help users wake up on time by completing different challenges before dismissing their alarms.

Unlike traditional alarm applications, Smart Challenge Alarm requires users to complete tasks such as mathematics, memory, typing, word puzzles, QR scanning and physical activities.

The main goal is to encourage users to get out of bed and become more active after waking up.

### 2. Problem Statement

Many people set alarms but dismiss them while still feeling sleepy and go back to sleep.

Traditional alarm applications allow users to turn off alarms with a single tap.

This application aims to address this problem by introducing interactive challenges that users must complete before dismissing their alarms.

### 3. Project Objectives

- Allow users to create and manage alarms.
- Provide multiple mathematics challenges.
- Provide memory-based challenges.
- Provide typing challenges.
- Provide missing-letter word challenges.
- Allow users to scan QR codes to dismiss alarms.
- Introduce physical activities such as push-ups, squats and dancing.
- Allow users to select challenge difficulty levels.
- Maintain alarm history.
- Track users' alarm completion performance.

## Business Rules

01- Challenge Order
The challenges run in the same order the user selected them when creating the alarm. The order has no other special meaning.

02- Wrong Answer Handling
- If the user gives a wrong answer, the system shows a NEW question (not the same question).
- This repeats with no limit until the user answers correctly.
- Every question shown, the user's answer, and whether it was correct are saved.

03- No Snooze
The system does not provide a snooze option. The alarm can be stopped only by completing all selected challenges.

04- Challenge Completion
- An alarm session has one status: RINGING, IN_PROGRESS, COMPLETED or MISSED.
- When the alarm starts, the status is RINGING.
- When the user starts the first challenge, the status becomes IN_PROGRESS.
- The status becomes COMPLETED only when ALL selected challenges are solved correctly.
- If the user closes the app in the middle, the alarm keeps ringing and the progress is saved. The user continues from where they stopped.

05- Timeout
- The alarm rings for a maximum of 15 minutes.
- If the challenges are not completed in 15 minutes, the status becomes MISSED.
- MISSED sessions are counted in the history and statistics.

## 4. User Roles

User:

A user can:

Register and log in.

Create, update and delete personal alarms.

Select alarm times.

Choose multiple challenge types.

Select challenge difficulty.

Complete challenges when alarms ring.

View personal alarm history.

Track waking-up performance.

System:

The application automatically:

Generates challenges.

Validates challenge answers.

Manages challenge completion.

Records alarm history.

Tracks user performance.

### 5. Functional Requirements

FR01: Users should be able to register and log in.

FR02: Users should be able to create, update and delete alarms.

FR03: Users should be able to enable and disable alarms.

FR04: Users should be able to select multiple challenge types.

FR05: The application should generate mathematics questions.

FR06: The application should generate memory challenges.

FR07: The application should provide typing challenges.

FR08: The application should provide missing-letter word challenges.

FR09: Users should be able to scan QR codes.

FR10: The application should support physical activity challenges.

FR11: The application should verify challenge completion.

FR12: The alarm should only be dismissed after the required challenges are completed.

FR13: Users should be able to view their alarm history.

FR14: Users should be able to configure recurring alarms.

FR15: Users should be able to select challenge difficulty levels.

### 6. Non-Functional Requirements

NFR01: The application should securely store user information.

NFR02: User passwords must be stored using secure password hashing.

NFR03: Users should only be able to access their own alarms and personal information.

NFR04: API responses should normally complete within 2 seconds under expected load.

NFR05: The application should handle invalid inputs and unexpected errors.

NFR06: The application should provide a responsive user interface.

NFR07: The application should maintain reliable alarm scheduling on supported mobile devices.

NFR08: The application should be maintainable and easy to extend with new challenge types.

NFR09: The application should support multiple users.

NFR10: The application should protect against unauthorized API access.

### 7. Technology Stack

**Backend:**
- Python
- Django
- Django REST Framework

**Frontend:**
- HTML
- CSS
- JavaScript
- React.js (future enhancement)

**Database:**
- PostgreSQL

**Mobile Development:**
- Flutter / Android integration (future enhancement)

**Development Tools:**
- VS Code
- Git
- GitHub
- Postman

**Additional Technologies (when required):**
- Redis
- Celery
- Docker
- Pytest

### 8. Future Enhancements

- AI-based activity recognition.
- Camera-based physical activity verification.
- Advanced QR code challenges.
- Personalized challenge generation.
- User performance analytics.
- Smart difficulty adjustment.