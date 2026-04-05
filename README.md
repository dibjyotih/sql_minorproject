# 🏥 Hospital Management & Patient Analytics System (SQL Project)

A database-driven system designed to efficiently manage hospital records and perform analytical queries to extract meaningful insights about patients, doctors, and treatments.

---

## 🚀 Features

-  Structured database design with multiple tables
-  Relationship mapping using foreign keys
-  Analytical queries for hospital insights
-  Track doctor performance
-  Revenue analysis
-  Disease frequency identification
-  Patient visit tracking

---



##  Database Schema

### 🔹 Tables

#### 1. Patients
- `patient_id` (Primary Key)
- `name`
- `age`
- `gender`

#### 2. Doctors
- `doctor_id` (Primary Key)
- `name`
- `specialization`

#### 3. Appointments
- `appointment_id` (Primary Key)
- `patient_id` (Foreign Key)
- `doctor_id` (Foreign Key)
- `date`

#### 4. Treatments
- `treatment_id` (Primary Key)
- `patient_id` (Foreign Key)
- `diagnosis`
- `cost`
- `treatment_date`

---

##  Setup Instructions

1. Create database:
   CREATE DATABASE hospital_db;
   USE hospital_db;


2. Create tables using provided SQL scripts

3. Insert sample data

---

## 📊 Key Queries

### 🔥 1. Most Consulted Doctors
SELECT d.name, COUNT(a.appointment_id) AS total_visits
FROM Doctors d
JOIN Appointments a ON d.doctor_id = a.doctor_id
GROUP BY d.name
ORDER BY total_visits DESC;

<img width="659" height="284" alt="image" src="https://github.com/user-attachments/assets/b5b16068-50c8-4dfb-8859-58e1638e83e2" />


---

### 💰 2. Monthly Revenue
SELECT DATE_FORMAT(treatment_date, '%Y-%m') AS month,
SUM(cost) AS total_revenue
FROM Treatments
GROUP BY month;

<img width="570" height="236" alt="image" src="https://github.com/user-attachments/assets/afc9ae47-6243-4b8a-a12d-3f958a3a8c28" />


---

### 🦠 3. Most Common Diseases
SELECT diagnosis, COUNT(*) AS frequency
FROM Treatments
GROUP BY diagnosis
ORDER BY frequency DESC;

<img width="613" height="288" alt="image" src="https://github.com/user-attachments/assets/00c2f017-706f-4ddd-ad04-cf49f5dce637" />

---

### 🔁 4. Patient Visit Frequency
SELECT p.name, COUNT(a.appointment_id) AS visits
FROM Patients p
JOIN Appointments a ON p.patient_id = a.patient_id
GROUP BY p.name;

<img width="555" height="294" alt="image" src="https://github.com/user-attachments/assets/ed8ef5a0-aa79-45fd-b774-db6f89d4e59b" />

---

### 👨‍⚕️ 5. Doctor Performance
SELECT d.name,
COUNT(a.appointment_id) AS total_patients,
SUM(t.cost) AS revenue_generated
FROM Doctors d
JOIN Appointments a ON d.doctor_id = a.doctor_id
JOIN Treatments t ON a.patient_id = t.patient_id
GROUP BY d.name
ORDER BY revenue_generated DESC;

<img width="940" height="278" alt="image" src="https://github.com/user-attachments/assets/b4ec3971-c6dd-4fe8-a09c-b708e9366fde" />


---

## 📌 Sample Insights

- Identify busiest doctors
- Track hospital revenue trends
- Analyze disease patterns
- Monitor patient engagement
- Evaluate doctor performance

---

## 🚀 Future Enhancements

- 💊 Add medicines and prescriptions table
- 🧾 Billing system integration
- 📊 Dashboard visualization (Power BI / Python)
- 🔐 User authentication system
- 🌐 Web-based interface

---

## 🎯 Use Case

Useful for:
- Hospitals and clinics
- Healthcare analytics
- Medical data management systems

---



