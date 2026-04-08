# 🏥 Clinic Management System - ER Design

This project represents a **database design (ERD)** for a modern clinic system.  
It focuses on managing patients, doctors, appointments, consultations, diagnostic tests, reports, and payments in a structured and scalable way.


## 📌 Overview

The system is designed to handle:

- Patient registration and history
- Doctor management with specializations
- Appointment scheduling
- Consultation (actual visits)
- Diagnostic test prescriptions
- Report generation
- Payment tracking


## 🧩 Core Entities

### 👤 Patients
Stores patient details such as name, contact, and demographics.

### 👨‍⚕️ Doctors
Stores doctor information including specialization and contact details.

### 🏷️ Specializations
Defines doctor specialties (e.g., Cardiology, Dermatology).

### 📅 Appointments
Represents scheduled meetings between patients and doctors.

### 🩺 Consultations
Represents actual visits (may or may not come from appointments).

### 🧪 Diagnostic Tests
Master list of available tests (e.g., Blood Test, X-ray).

### 📋 Prescriptions
Links consultations with diagnostic tests prescribed by doctors.

### 📄 Reports
Stores test results generated after diagnostics.

### 💳 Payments
Tracks all financial transactions related to appointments and consultations.


## 🔗 Relationships

- One patient can have many appointments and consultations  
- One doctor can attend many patients  
- One appointment may lead to a consultation (optional)  
- One consultation can generate multiple prescriptions  
- Each prescription corresponds to one diagnostic test  
- Each prescription generates a report  
- Payments can be linked to appointments or consultations  
- Multiple doctors can share the same specialization  


## ⚙️ Key Design Decisions

### 1. Appointment vs Consultation
- **Appointment** = scheduled visit  
- **Consultation** = actual visit  
- Not all appointments result in consultations (no-show/cancel)


### 2. Tests Linked to Consultation
- Tests are prescribed during consultation, not at booking stage


### 3. Reports Linked to Prescriptions
- Each report belongs to a specific test instance


### 4. Denormalization for Performance
- 'reports' includes 'patient_id' and 'doctor_id'
- 'payments' includes 'patient_id'
- This reduces complex joins for reporting and billing queries


### 5. Flexible Payment Handling
- Payments can be made:
  - During appointment booking
  - After consultation
  - For diagnostic tests


### 6. Follow-up Support
- 'consultations' includes 'follow_up_date' to track future visits


## 📊 Example Use Cases

- Find all appointments for a patient  
- Track consultation history of a patient  
- List all tests prescribed during a visit  
- Retrieve diagnostic reports  
- Generate billing reports for a patient  
- Analyze doctor workload  


## 🚀 Possible Enhancements

- Add user authentication (admin/staff roles)
- Add doctor availability scheduling
- Add departments (above specialization)
- Add audit logs for changes
- Add insurance handling


## 🧠 Conclusion

This ER design balances:
- **Normalization** (clean structure)
- **Practical optimization** (faster queries)
- Real-world workflow modeling
It is suitable for a **small to mid-scale clinic system** and can be extended further as needed.

<p align="center">
<img src="./Clinic Appointment/Clinic Appointment and Diagnostics Platform.png" width="800">
</p>
