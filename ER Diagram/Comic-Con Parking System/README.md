# 🚗 Comic-Con Parking System

## 📌 Overview

This project models a **multi-zone parking management system** for a large-scale event like Comic-Con India. The system is designed to efficiently track vehicle entries, parking allocation, reserved categories, session timings, and payments across multiple days.

It supports different vehicle types, special access categories (VIP, staff, exhibitors, etc.), and structured parking zones with multiple levels.

---

## 🎯 Objectives

The system is designed to answer:

* What vehicles entered the parking facility?
* What type of vehicle entered?
* Which parking spot was assigned?
* Which zone and level does the spot belong to?
* Was the spot reserved (VIP, staff, EV, etc.)?
* When did the vehicle enter and exit?
* What ticket was issued?
* Can vehicles visit multiple times?
* Can parking spots be reused?
* How is availability tracked?
* How are charges calculated?
* How are payments recorded?
* Which vehicles are currently parked?

---

## 🧱 Core Entities

### 🚘 Vehicles

Stores all vehicles entering the venue.

* Linked to vehicle type and access category
* Supports multiple visits

### 🏷️ Vehicle Categories

Defines types of vehicles:

* Bike, Car, SUV, EV, Cab

### 👤 Access Categories

Defines special permissions:

* VIP, Staff, Exhibitor, Cosplayer, General

### 🗺️ Parking Zones

Represents physical parking structure:

* Divided into zones and levels

### ⭐ Spot Categories

Defines reserved parking types:

* VIP, Staff, EV Charging, etc.

### 🅿️ Parking Spots

Individual parking units:

* Assigned based on vehicle type and availability
* Tracks current status (Available/Occupied)

### 🎟️ Parking Tickets

Generated when a vehicle enters:

* One ticket per entry

### ⏱️ Parking Sessions

Tracks each visit:

* Entry time, exit time
* Assigned spot
* Active or completed status
* Total parking fee

### 💰 Pricing Rules

Defines pricing logic:

* Based on vehicle category
* Supports flexible pricing models

### 💳 Payments

Stores payment details:

* Linked to parking sessions
* Tracks payment status

---

## 🔗 Relationships Summary

* One vehicle category → many vehicles
* One access category → many vehicles
* One zone → many parking spots
* One spot category → many parking spots
* One vehicle → many parking sessions
* One parking spot → many sessions over time
* One ticket → one parking session
* One session → one payment
* One vehicle category → pricing rules

---

## ⚙️ Key Features

### ✅ Multi-Visit Support

Vehicles can enter and exit multiple times across event days.

### ✅ Smart Spot Allocation

Parking spots are assigned based on:

* Vehicle type
* Availability
* Reserved category

### ✅ Reserved Parking

Supports special categories:

* VIP, Staff, Exhibitors, Cosplayers, EV charging

### ✅ Real-Time Availability

* Spot status (Available/Occupied)
* Active sessions indicate currently parked vehicles

### ✅ Session Tracking

Each parking session records:

* Entry and exit timestamps
* Assigned parking spot
* Ticket reference

### ✅ Pricing & Billing

* Pricing rules based on vehicle type
* Automatic fee calculation
* Payment tracking with status

---

## 🚀 System Capabilities

* Track all vehicles inside the venue
* Identify currently parked vehicles (`ACTIVE` sessions)
* Manage multi-zone, multi-level parking
* Reuse parking spots efficiently
* Handle high-volume event traffic
* Maintain clean separation of entities (normalized design)

---

## 🧠 Design Highlights

* Separation of **tickets and sessions** for flexibility
* Use of **categories for scalability**
* Support for **real-world constraints** (EV, VIP, etc.)
* Clean **one-to-many relationships** for reuse
* Extensible pricing system

---

## 🏁 Conclusion

This ERD represents a **scalable, real-world parking system** suitable for large events. It ensures efficient tracking of vehicles, optimized parking allocation, and accurate billing while maintaining flexibility for future enhancements.

<p align="center">
<img src="./Comic-Con Parking System/Comic-Con Parking System.png" width="800">
</p>
