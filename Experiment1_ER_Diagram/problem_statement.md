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
 <img width="1195" height="552" alt="image" src="https://github.com/user-attachments/assets/8b28d752-93ff-4b23-ba87-5b21fa990a9c" />


### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
|  member   |      m_name, M_ID(PK), M_Age, M_Gender              |       |
|   trainer     |     T_Name, T_ID(PK), T_specialization               |       |
|   program     |     P_ID(PK), P_Name               |       |

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|    Training          |    program       |      Member & Trainer        |   Trainer trains the member according to the program   |

### Assumptions
- Trainer chooses the program thats right for the member
- member will pay the fee required for the program

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
<img width="975" height="606" alt="image" src="https://github.com/user-attachments/assets/f5de0caf-e14a-4faa-93c3-8ebfb86b4cc3" />


### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
|    Room    |  Room_ID(PK),Room_name, Room_No                  |       |
|  Event      |       Event_ID(PK), Event_Speaker,             |       |
|  Book      |        Book_ID(PK), Book_Name, Book_Price            |       |
|  Member      |       Member_ID(PK), Member_Name             |       |
|   Speaker     |        Speaker_ID(PK), Speaker_info            |       |

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|      Lending        |  Members lend the book from the library          |     Member, book, speaker          |       |
|      Buying        |  Members buy the book from the library          |    Member, Book, Speaker           |       |
|       Reading       |   Speaker reading the book         |           Speaker & Book    |       |

### Assumptions
- Speaker lends book to member
- Member buy the book from library

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
<img width="879" height="889" alt="image" src="https://github.com/user-attachments/assets/8a1e6458-4655-446c-85cd-6bea4dd54deb" />


### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
| Table       |   Table_ID(PK), Table_No, Table_capacity                 |       |
|  Waiter      |   Waiter_ID(PK), Waiter_info, Waiter_contact                 |       |
|   Dish     |    Dish_ID(PK), price, Category                |       |

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|      ordering        |       customer orders food to the table     |   waiter, customer, order, dish            |       |
|      Billing        |   customer Buys the dish after ordering         |   customer, cashier, bill            |       |
|              |            |               |       |

### Assumptions
- Customer order the food(DISH) from the waiter.
- Bill generated for the customer for thier respective dish

---

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
