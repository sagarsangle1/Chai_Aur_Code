# 🏋️ Online Fitness Coaching Platform – Database Design

## 📌 Overview

This project defines the **ER (Entity-Relationship) design** for an online fitness coaching platform where trainers manage clients, sell fitness plans, schedule sessions, and track client progress.

The system supports:

* Trainer-client relationships
* Plan subscriptions
* Consultations & live sessions
* Progress tracking (check-ins, measurements, media)
* Payments and transactions

---

## 🧱 Database Schema

### 👤 Users

Stores all platform users (both trainers and clients).

* `user_id (PK)`
* `name`
* `email (unique)`
* `phone`
* `role` → CLIENT / TRAINER
* `created_at`

---

### 🧑‍🏫 Trainers

Extends users with trainer-specific details.

* `trainer_id (PK, FK → users.user_id)`
* `bio`
* `specialization`
* `experience_years`

---

### 🧑 Clients

Extends users with client-specific details.

* `client_id (PK, FK → users.user_id)`
* `age`
* `gender`
* `fitness_goal`
* `medical_conditions`

---

### 📦 Plans

Fitness programs created by trainers.

* `plan_id (PK)`
* `trainer_id (FK)`
* `name`
* `description`
* `price`
* `duration_days`
* `plan_type` → CONSULTATION / FULL_COACHING / WORKOUT_ONLY / DIET_ONLY
* `created_at`

---

### 🔁 Subscriptions

Tracks which client purchased which plan.

* `subscription_id (PK)`
* `client_id (FK)`
* `plan_id (FK)`
* `start_date`
* `end_date`
* `status` → ACTIVE / COMPLETED / CANCELLED
* `created_at`

---

### 💳 Payments

Stores payment transactions for subscriptions.

* `payment_id (PK)`
* `subscription_id (FK)`
* `amount`
* `payment_date`
* `payment_method`
* `status` → SUCCESS / FAILED / REFUNDED

---

### 📅 Sessions

Represents consultations and live workouts.

* `session_id (PK)`
* `trainer_id (FK)`
* `client_id (FK)`
* `subscription_id (FK, nullable)`
* `session_type` → CONSULTATION / LIVE_WORKOUT
* `scheduled_at`
* `duration` (in minutes)
* `status` → SCHEDULED / COMPLETED / CANCELLED
* `meeting_link`
* `created_at`

---

### 📊 Check-ins

Client progress updates (weekly or periodic).

* `checkin_id (PK)`
* `client_id (FK)`
* `subscription_id (FK)`
* `submitted_at`
* `weight`
* `notes`
* `adherence_score`
* `created_at`

---

### 📏 Body Measurements

Detailed physical metrics per check-in.

* `measurement_id (PK)`
* `checkin_id (FK)`
* `chest`
* `waist`
* `hips`
* `body_fat_percentage`

---

### 📸 Progress Media

Stores images/videos for progress tracking.

* `media_id (PK)`
* `checkin_id (FK)`
* `media_url`
* `type` → IMAGE / VIDEO

---

### 📝 Trainer Notes

Feedback provided by trainers on check-ins.

* `note_id (PK)`
* `checkin_id (FK)`
* `trainer_id (FK)`
* `note_text`
* `created_at`

---

### 🥗 Plan Content

Stores workout and diet content for plans.

* `content_id (PK)`
* `plan_id (FK)`
* `type` → WORKOUT / DIET
* `title`
* `description`

---

## 🔗 Relationships

```
users.user_id = trainers.trainer_id        (1:1)
users.user_id = clients.client_id          (1:1)

trainers.trainer_id < plans.trainer_id     (1:N)

clients.client_id < subscriptions.client_id   (1:N)
plans.plan_id < subscriptions.plan_id         (1:N)

subscriptions.subscription_id < payments.subscription_id   (1:N)

trainers.trainer_id < sessions.trainer_id   (1:N)
clients.client_id < sessions.client_id      (1:N)
subscriptions.subscription_id < sessions.subscription_id   (optional)

clients.client_id < checkins.client_id      (1:N)
subscriptions.subscription_id < checkins.subscription_id   (1:N)

checkins.checkin_id = body_measurements.checkin_id   (1:1)
checkins.checkin_id < progress_media.checkin_id      (1:N)
checkins.checkin_id < trainer_notes.checkin_id       (1:N)

trainers.trainer_id < trainer_notes.trainer_id       (1:N)

plans.plan_id < plan_content.plan_id                (1:N)
```

---

## 🧠 Key Design Decisions

### ✅ Single User Table

* Avoids duplication
* Supports role-based extension (trainer/client)

### ✅ Subscription-Based Model

* Tracks plan ownership over time
* Supports multiple purchases per client

### ✅ Separation of Concerns

* Sessions ≠ Check-ins
* Progress data stored separately

### ✅ Scalable Progress Tracking

* Measurements, media, and notes are modular

### ✅ Flexible Plan Content

* Supports both workout and diet in one structure

---

## 🚀 Features Supported

* Multiple trainers and clients
* One trainer → many plans
* One plan → many clients
* Multiple subscriptions per client
* Consultation-only users
* Session scheduling system
* Weekly progress tracking
* Trainer feedback system
* Payment tracking per subscription

---

## 🏁 Conclusion

This database design provides a **clean, normalized, and scalable structure** for an online fitness coaching platform. It efficiently models real-world scenarios like subscriptions, consultations, and progress tracking while maintaining flexibility for future enhancements.

---

## ER Diagram

The ER diagram is included in this repository as: 

<p align="center">
<img src="Fitness Influencer Coaching Platform.png" width="800">
</p>
