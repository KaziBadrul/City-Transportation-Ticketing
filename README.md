# 📘 City Transportation Ticketing & Fleet Monitoring System

A database-driven system designed to manage city transportation workflows including ticketing, trip scheduling, fleet monitoring, maintenance tracking, and analytical reporting.

Course: RDBMS
DBMS: PostgreSQL
Semester Project
Team Members:

- Mohammad Ariqul Islam (220041219)

- Kazi Badrul Hasan (220041233)

- Mubashshir Hasnain Belal Turjo (220041249)

- Saadat Hasin Fattah (220041204)

## 📌 1. Project Overview

Modern urban transport systems deal with large volumes of data—vehicles, drivers, routes, schedules, ticket sales, maintenance, and incidents.
Many agencies still rely on spreadsheets and manual records, causing inefficiency and lack of real-time visibility.

CTTFMS provides a centralized, relational database system to handle:

Ticketing & seat availability

Trip creation & scheduling

Driver–vehicle assignment

Maintenance & fuel tracking

Operational reports & analytics

Audit logging for critical actions

PostgreSQL is used as the primary DBMS due to its strong relational integrity, advanced triggers, JSON support, and analytical SQL capabilities.

## 🧩 2. Core Features (Proposal Stage)

Manage vehicles, drivers, passengers, routes, and trips

Ticketing with automatic seat updates

Driver assignment with availability validation

Maintenance record tracking with JSON details

Audit logging using triggers

Analytical SQL for revenue, occupancy, and route performance

Role-based access structure

## 🗂️ 3. Entity–Relationship Diagram (ERD)

Proposal ERD includes 8 core entities:
Vehicle, Route, Trip, Driver, Passenger, Ticket, MaintenanceRecord, AuditLog

(Add ERD image here once completed:
/docs/ERD.png)

## 🧱 4. Initial Relational Schema
Vehicle

vehicle_id, registration_no, vehicle_type, capacity, status

Route

route_id, origin, destination, distance_km

Driver

driver_id, name, license_no, experience_years, availability_status

Trip

trip_id, vehicle_id, route_id, driver_id, trip_date, departure_time, arrival_time, total_seats, available_seats

Passenger

passenger_id, name, contact_no

Ticket

ticket_id, trip_id, passenger_id, seat_no, price, purchase_time, payment_status

MaintenanceRecord

record_id, vehicle_id, description, maintenance_date, cost, json_details

AuditLog

log_id, table_name, action_type, action_timestamp, record_id, user_role

## ⚙️ 5. Planned Stored Procedures & Functions
Stored Procedures

assign_driver_to_trip(driver_id, trip_id)

record_ticket_purchase(trip_id, passenger_id, seat_no)

generate_daily_trip_summary(date)

Stored Functions

calculate_trip_revenue(trip_id)

get_available_seats(trip_id)

next_maintenance_due(vehicle_id)

## 🚨 6. Planned Triggers

BEFORE INSERT on Ticket – prevent duplicate seat

AFTER INSERT on Ticket – update Trip.available_seats

AFTER UPDATE on Trip (multi-row) – summarize occupancy + audit log

BEFORE INSERT on MaintenanceRecord – validate maintenance interval

AFTER INSERT on core tables – insert into AuditLog

## 📊 7. Example SQL Queries (Final Project)

Most profitable route (nested subquery)

Driver/route/trip JOIN with occupancy

Window function ranking — revenue per vehicle

Rolling averages — passengers per route

CUBE / GROUPING SETS — revenue breakdown

JSON extraction — maintenance details

Optimized indexed queries

## 🔄 8. Multi-step Workflows Covered

1. Passenger Ticketing
Seat validation → ticket creation → seat update → audit log

2. Driver Assignment
Availability check → assignment → audit log

3. Vehicle Maintenance
Interval validation → JSON record → searchable logs

4. Trip Lifecycle
Trip scheduling → ticket sales → summary generation

## 🔐 9. Role-Based Access Model

Admin – Full CRUD, revenue views, maintenance approval
Staff – Ticketing, schedules
Maintenance Crew – Add/update maintenance
Passenger (future) – Browse & book tickets

Roles implemented using PostgreSQL role management.

## 🛠️ 10. Tech Stack

DBMS: PostgreSQL

Tools: pgAdmin 4 / DBeaver

Procedures: PL/pgSQL

Future Backend (optional): NExpressJS

Frontend: NextJS

## 📈 11. Why PostgreSQL?

Advanced triggers & PL/pgSQL

Powerful indexing (GIN, BRIN, B-tree)

Native JSON & hybrid storage

Partitioning for large tables

Excellent for analytical SQL

Production-grade reliability

