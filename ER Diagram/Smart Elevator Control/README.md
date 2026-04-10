
# 🛗 LiftGrid Systems – Smart Elevator Control Platform (ERD)

## 📌 Overview

This project models a **smart elevator control system** used in large-scale infrastructure such as corporate towers, malls, airports, hospitals, and residential complexes.

The system is designed to manage:

* Multiple buildings
* Multiple elevators per building
* Real-time floor requests
* Ride allocation and execution
* Elevator status monitoring
* Maintenance tracking
* Usage analytics

The ER diagram ensures a **scalable, normalized, and production-ready backend design**.

---

## 🏗️ Core Architecture

The system is divided into three major layers:

### 1. Static Structure

* Buildings
* Floors
* Elevators
* Shafts
* Zones

### 2. Operational Data

* Floor Requests
* Ride Assignments
* Ride Logs

### 3. Monitoring & Tracking

* Elevator Status Logs
* Maintenance Logs

---

## 🧱 Entities Description

### 🏢 Buildings

Stores information about all buildings connected to the platform.

### 🏬 Floors

Each building contains multiple floors. Floors are uniquely identified within a building.

### 🧩 Zones

Used to group elevators into logical zones (e.g., low-rise, high-rise).

### 🛗 Shafts

Represents physical elevator shafts in a building.

### 🚀 Elevators

Each elevator:

* Belongs to a building
* Is assigned to exactly one shaft (**1:1 constraint**)
* Has capacity and operational status

---

## 🔗 Mapping Tables

### 🔄 Elevator-Floor Mapping

Defines which floors an elevator can serve (Many-to-Many).

### 🗺️ Elevator-Zone Mapping

Allows grouping elevators into zones for optimized routing.

---

## 📍 Request & Ride Flow

### 🧾 Floor Requests

Generated when a user requests an elevator from a floor.

Includes:

* Source floor
* Destination floor
* Direction (UP/DOWN)
* Status tracking

---

### 🔗 Ride Assignments

Maps each request to exactly one elevator.

Ensures:

* One request → one elevator

---

### 📊 Ride Logs

Stores completed ride details for analytics:

* Start & end floors
* Time tracking
* Duration

---

## 📡 Real-Time Monitoring

### ⚙️ Elevator Status Logs

Tracks real-time and historical status:

* Idle
* Moving
* Maintenance
* Offline

Also records current floor and timestamps.

---

## 🛠️ Maintenance Tracking

### 🔧 Maintenance Logs

Tracks all maintenance activities:

* Scheduled or breakdown
* Start and end time
* Technician details
* Status progression

Ensures history is preserved and not overwritten.

---

## 🔗 Relationships Summary

* One building → many floors, shafts, elevators, zones
* One shaft → one elevator (**1:1 enforced**)
* Elevators ↔ Floors (**M:N via mapping**)
* Elevators ↔ Zones (**M:N via mapping**)
* Floor requests → assigned to one elevator
* Elevators → handle multiple rides
* Elevators → have multiple status logs
* Elevators → have multiple maintenance records

---

## 📊 Supported Queries

This ERD supports:

* Total buildings in the system
* Elevators per building
* Floors per building
* Elevator-to-floor coverage
* Requests generated from floors
* Elevator assigned to each request
* Pending vs completed requests
* Ride count per elevator
* Most used elevator
* Real-time elevator status
* Maintenance history per elevator
* Ride analytics for performance monitoring

---

## 🎯 Key Design Decisions

* ✅ **Separation of request vs ride** (intent vs execution)
* ✅ **No dynamic data inside elevator entity**
* ✅ **Use of mapping tables for scalability**
* ✅ **Status & maintenance stored as logs (history preserved)**
* ✅ **Zone-based grouping for enterprise-level systems**

---

## 🏆 Conclusion

This ER design is:

* ✔ Fully normalized
* ✔ Scalable for large infrastructure
* ✔ Suitable for real-time systems
* ✔ Analytics-ready
* ✔ Industry-standard

It accurately models a **multi-building intelligent elevator control system** capable of handling high traffic, operational monitoring, and long-term analytics.

<p align="center">
<img src="./Smart Elevator Control/Smart Elevator Control.png" width="1000">
</p>
