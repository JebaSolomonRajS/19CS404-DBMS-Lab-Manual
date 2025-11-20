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
<img width="1536" height="1024" alt="ERD of FlexiFit Gym System" src="https://github.com/user-attachments/assets/42740383-02fa-4263-95ca-b8433b862cd6" />


### Entities and Attributes
| **Entity**                | **Attributes (PK, FK)**                                                                        | **Notes**                                          |
| ------------------------- | ---------------------------------------------------------------------------------------------- | -------------------------------------------------- |
| Member                    | Member_ID (PK), Name, Membership_Type, Start_Date, Contact_Number, Email, Address              | Stores details of gym members                      |
| Program                   | Program_ID (PK), Program_Name, Duration, Fee                                                   | Programs offered by the gym                        |
| Trainer                   | Trainer_ID (PK), Name, Specialty, Experience_Years, Contact_Number                             | Trainers assigned to programs                      |
| Personal_Training_Session | Session_ID (PK), Member_ID (FK), Trainer_ID (FK), Session_Date, Session_Time, Duration, Status | Records sessions booked by members with trainers   |
| Attendance                | Attendance_ID (PK), Member_ID (FK), Program_ID (FK), Date, Status                              | Tracks member attendance in programs               |
| Payment                   | Payment_ID (PK), Member_ID (FK), Amount, Payment_Date, Payment_Type                            | Tracks payment details for memberships or sessions |
| Membership                | Membership_ID (PK), Member_ID (FK), Start_Date, End_Date, Type, Fee                            | Optional: detailed membership tracking             |


### Relationships and Constraints

| **Relationship**                                     | **Cardinality** | **Participation**    | **Notes**                                                                           |
| ---------------------------------------------------- | --------------- | -------------------- | ----------------------------------------------------------------------------------- |
| Joins (Member–Program)                               | N:M             | Mandatory for Member | Many members can join many programs                                                 |
| Conducts (Trainer–Program)                           | 1:N             | Mandatory            | Each program can have multiple trainers; each trainer can conduct multiple programs |
| Books (Member–Personal_Training_Session)             | 1:N             | Mandatory            | Each personal training session is booked by one member                              |
| Conducts_Session (Trainer–Personal_Training_Session) | 1:N             | Mandatory            | Each session is conducted by one trainer                                            |
| Records_Attendance (Member–Attendance)               | 1:N             | Mandatory            | Each attendance is linked to one member                                             |
| Tracks (Attendance–Payment)                          | 1:1 or 1:N      | Optional             | Payments can be linked to attended sessions                                         |
| Membership_Payment (Member–Payment)                  | 1:N             | Optional             | Tracks payments for membership separately                                           |


A member can join multiple programs (Yoga, Zumba, Weight Training).

A trainer can conduct multiple programs, but each program can have multiple trainers.

Payments are made either for membership or for individual sessions.

Attendance is recorded per session or per program for each member.

Membership details can be tracked separately if required.
### Assumptions
A member can join multiple programs (Yoga, Zumba, Weight Training).

A trainer can conduct multiple programs, but each program can have multiple trainers.

Payments are made either for membership or for individual sessions.

Attendance is recorded per session or per program for each member.

Membership details can be tracked separately if required.
### Assumptions
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
<img width="1536" height="1024" alt="City Library System ER Diagram" src="https://github.com/user-attachments/assets/23d8c28f-c1f2-4128-8b31-1435cc41ffdf" />


### Entities and Attributes

| **Entity**         | **Attributes (PK, FK)**                                                          | **Notes**                                                  |
| ------------------ | -------------------------------------------------------------------------------- | ---------------------------------------------------------- |
| Member             | Member_ID (PK), Name, Contact_Number, Email, Address, Membership_Type            | Stores library member details                              |
| Book               | Book_ID (PK), Title, Author, Category, Copies_Available                          | Details of books in the library                            |
| Loan               | Loan_ID (PK), Member_ID (FK), Book_ID (FK), Loan_Date, Return_Date, Status, Fine | Tracks book lending and overdue fines                      |
| Event              | Event_ID (PK), Event_Name, Event_Date, Room_ID (FK), Organizer                   | Library cultural events                                    |
| Speaker            | Speaker_ID (PK), Name, Biography                                                 | Speakers or authors for events                             |
| Room               | Room_ID (PK), Room_Name, Capacity, Room_Type                                     | Rooms for events or study sessions                         |
| Event_Registration | Registration_ID (PK), Member_ID (FK), Event_ID (FK), Registration_Date           | Tracks which members registered for which events           |
| Event_Speaker      | EventSpeaker_ID (PK), Event_ID (FK), Speaker_ID (FK)                             | Junction table for many-to-many Event–Speaker relationship |

### Relationships and Constraints
| **Relationship**                                      | **Cardinality** | **Participation** | **Notes**                                                                  |
| ----------------------------------------------------- | --------------- | ----------------- | -------------------------------------------------------------------------- |
| Borrows (Member–Loan)                                 | 1:N             | Mandatory         | A member can borrow multiple books; each loan is linked to one member      |
| Booked (Book–Loan)                                    | 1:N             | Mandatory         | Each loan is linked to one book; a book can be borrowed multiple times     |
| Registers (Member–Event_Registration)                 | N:M             | Optional          | Members can register for multiple events                                   |
| Held_In (Event–Room)                                  | 1:N             | Mandatory         | Each event occurs in one room; a room can host multiple events             |
| Presented_By (Event–Event_Speaker)                    | N:M             | Mandatory         | Events can have multiple speakers; speakers can present at multiple events |
| Tracks_Registration (Event_Registration–Member/Event) | 1:N             | Mandatory         | Each registration links a member to an event                               |


### Assumptions
Each book copy is treated as a single entity in Loan; availability is tracked per copy.

Overdue fines are calculated per book per day late.

Rooms are shared for events and study, but cannot double-book at the same time.

Event speakers can be authors, experts, or library staff.

Members can register for multiple events, and each event can have multiple participants
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
<img width="1248" height="832" alt="Gemini_Generated_Image_ikc464ikc464ikc4" src="https://github.com/user-attachments/assets/41384c45-8ee5-4e97-830c-1c2cbf1de76c" />


### Entities and Attributes

| Entity       | Attributes (PK, FK)                                                           | Notes                                                             |
| ------------ | ----------------------------------------------------------------------------- | ----------------------------------------------------------------- |
| Customer     | CustomerID (PK), Name, Phone, Email                                           | Stores customer details; can reserve tables or walk in            |
| Reservation  | ReservationID (PK), CustomerID (FK), TableID (FK), Date, Time, NumberOfGuests | Links customer to a table and their visit                         |
| Table        | TableID (PK), TableNumber, Capacity                                           | Restaurant seating arrangement                                    |
| Order        | OrderID (PK), ReservationID (FK), OrderTime                                   | Linked to a reservation; multiple orders per reservation possible |
| Dish         | DishID (PK), Name, Category, Price                                            | Category: Starter/Main/Dessert                                    |
| OrderDetails | OrderDetailID (PK), OrderID (FK), DishID (FK), Quantity                       | Resolves many-to-many between Orders and Dishes                   |
| Bill         | BillID (PK), ReservationID (FK), TotalAmount, ServiceCharge, Tax              | Generated per reservation                                         |
| Waiter       | WaiterID (PK), Name, Phone                                                    | Assigned to serve reservations                                    |

### Relationships and Constraints

| Relationship                    | Cardinality | Participation                                | Notes                                                                        |
| ------------------------------- | ----------- | -------------------------------------------- | ---------------------------------------------------------------------------- |
| Customer — Reservation          | 1:N         | Total for Reservation, Optional for Customer | One customer can have multiple reservations                                  |
| Reservation — Table             | N:1         | Total for Reservation, Total for Table       | Each reservation assigned a table                                            |
| Reservation — Order             | 1:N         | Total for Reservation, Optional for Order    | Multiple orders per reservation                                              |
| Order — Dish (via OrderDetails) | M:N         | Total participation                          | Each order can have multiple dishes; each dish can appear in multiple orders |
| Reservation — Bill              | 1:1         | Total                                        | One bill per reservation                                                     |
| Reservation — Waiter            | N:1         | Total for Reservation                        | Waiter serves multiple reservations                                          |

### Assumptions
A reservation always requires a table; walk-ins can be assigned a table dynamically.

Each dish belongs to only one category (starter/main/dessert).

A waiter can serve multiple tables/reservations, but each reservation is served by one waiter.

Bills include service charges and tax automatically calculated.

Customers may place multiple orders during one reservation.
---

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
