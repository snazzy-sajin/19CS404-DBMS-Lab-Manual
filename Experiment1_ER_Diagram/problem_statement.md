# ER Diagram Workshop – Submission Template

## Objective
To understand and apply ER modeling concepts by creating ER diagrams for real-world applications.

## Purpose
Gain hands-on experience in designing ER diagrams that represent database structure including entities, relationships, attributes, and constraints.

---

# Scenario A: City Fitness Club Management

**Business Context:**  
FlexiFit Gym wants a database to manage its members, trainers, and fitness programs.

**Requirements:**  
- Members register with name, membership type, and start date.  
- Each member can join multiple programs (Yoga, Zumba, Weight Training).  
- Trainers assigned to programs; a program may have multiple trainers.  
- Members may book personal training sessions with trainers.  
- Attendance recorded for each session.  
- Payments tracked for memberships and sessions.

### ER Diagram:
<img width="1195" height="552" alt="image" src="https://github.com/user-attachments/assets/20c00231-2ea8-4906-bac3-38722d0975cd" />

### Entities and Attributes


| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
|   Members     |    M_ID (PK), M_Name, M_Gender, M_StartDate, MembershipType                | Membership type was mentioned in requirements but missing in diagram → add it.      |
|Program|  P_ID (PK), P_Name                  |     Represents fitness programs (Yoga, Zumba, etc.).  |
|  Trainer      |         T_ID (PK), T_Name, T_Specialization           |  Trainers may specialize in certain areas.     |


### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|   Takes           |      M:N      |   Partial for both            |  A member can join many programs; each program has many members.     |
| Assigned             |    M:N        |      Total on Program side         |   A program must have at least one trainer; a trainer can be assigned to many programs.    |
|              |            |               |       |

### Assumptions
 A membership type (e.g., Monthly, Annual, Premium) determines the base subscription fees.

Each program (Yoga, Zumba, Weight Training) must be assigned at least one trainer.

Members can join multiple programs simultaneously.


---

# Scenario B: City Library Event & Book Lending System

**Business Context:**  
The Central Library wants to manage book lending and cultural events.

**Requirements:**  
- Members borrow books, with loan and return dates tracked.  
- Each book has title, author, and category.  
- Library organizes events; members can register.  
- Each event has one or more speakers/authors.  
- Rooms are booked for events and study.  
- Overdue fines apply for late returns.

### ER Diagram:
<img width="975" height="606" alt="Screenshot 2025-09-04 112925" src="https://github.com/user-attachments/assets/d270d63a-1d4d-441a-883f-a65eec1a45a1" />

### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
|ROOM        |    Room_ID (PK), Room_Name, Capacity, Room_Type                | Stores details of rooms available for events or bookings.      |
|    EVENT    |         Event_ID (PK), Event_Name, Event_Date, Description           |    Events hosted in rooms, associated with speakers.   |


### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|        hosts      |   1:N         |   Total on Event side            | Each event must be hosted in one room; a room can host multiple events.      |
|   registers           |     M:N       |         Partial      |   A member can register for many events; an event can have many registered members.    |
|              |            |               |       |

### Assumptions
Each event is assigned to exactly one room, but a room may host many events across dates.

Speakers may be linked to multiple events.

Members can borrow multiple books, but a book can only be loaned to one member at a time.

---

# Scenario C: Restaurant Table Reservation & Ordering

**Business Context:**  
A popular restaurant wants to manage reservations, orders, and billing.

**Requirements:**  
- Customers can reserve tables or walk in.  
- Each reservation includes date, time, and number of guests.  
- Customers place food orders linked to reservations.  
- Each order contains multiple dishes; dishes belong to categories (starter, main, dessert).  
- Bills generated per reservation, including food and service charges.  
- Waiters assigned to serve reservations.

### ER Diagram:

<img width="879" height="889" alt="Screenshot 2025-09-04 113556" src="https://github.com/user-attachments/assets/18ec9096-01d2-43d8-bfc8-68d198263c2d" />

### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
| CUSTOMER       |  Customer_ID (PK), Name, Contact_Info                  | Customers make reservations and place orders.      |
|   TABLE     |      Table_ID (PK), Table_Number, Capacity, Location              |  Represents physical tables in the restaurant.     |


### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|   makes           |   1:N         |    Partial           |    A customer may make many reservations.   |
|       hosts       |      1:N      |       Total on Reservation        | Each reservation must be for one table; a table can host many reservations over time.      |
|              |            |               |       |

### Assumptions
Each reservation must be linked to a specific table and waiter.

A reservation may include multiple orders during the dining session.

Orders consist of one or more dishes; handled through Order_Detail.

---

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
