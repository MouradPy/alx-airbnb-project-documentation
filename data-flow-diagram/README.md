# Data Flow Diagram - Airbnb Clone Backend

## Overview
This document presents the Data Flow Diagram (DFD) for the Airbnb Clone backend system. It visualizes how data moves between users, system processes, and data stores.

---

## DFD Description

### Key Entities
1. **Guest** - interacts with the system to browse listings, make bookings, and send payments.  
2. **Host** - lists and manages properties, responds to bookings, and receives payments.  
3. **Admin** - oversees the platform, monitors users, and manages the system.

---

## Main Processes
1. **User Management**  
   - Handles registration, authentication, and user profile data.  

2. **Property Management**  
   - Handles creation, updating, and retrieval of property listings.  

3. **Booking Management**  
   - Processes booking requests, confirmations, and cancellations.  

4. **Payment Processing**  
   - Handles guest payments, host payouts, and transaction history.  

5. **Review & Messaging System**  
   - Enables user reviews and host–guest communication.  

---

## Data Stores
- **User Database** – stores user profiles and authentication data.  
- **Property Database** – stores property details and availability.  
- **Booking Database** – stores all booking records and histories.  
- **Payment Database** – stores transaction and payment data.  
- **Review Database** – stores reviews and message records.

---

## Mermaid DFD Code

```mermaid
graph TD

%% External Entities
Guest((Guest))
Host((Host))
Admin((Admin))

%% Processes
P1[User Management]
P2[Property Management]
P3[Booking Management]
P4[Payment Processing]
P5[Review & Messaging]

%% Data Stores
D1[(User Database)]
D2[(Property Database)]
D3[(Booking Database)]
D4[(Payment Database)]
D5[(Review Database)]

%% Guest Interactions
Guest --> P1
Guest --> P2
Guest --> P3
Guest --> P4
Guest --> P5

%% Host Interactions
Host --> P1
Host --> P2
Host --> P3
Host --> P4
Host --> P5

%% Admin Interactions
Admin --> P1
Admin --> P2
Admin --> P3
Admin --> P4
Admin --> P5

%% Processes to Data Stores
P1 --> D1
P2 --> D2
P3 --> D3
P4 --> D4
P5 --> D5

%% Data Stores back to Processes
D1 --> P1
D2 --> P2
D3 --> P3
D4 --> P4
D5 --> P5
