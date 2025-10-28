# Use Case Diagram - Airbnb Clone Backend

## Overview
This document contains the Use Case Diagram for the Airbnb Clone backend system, visualizing all key interactions between actors and the system.

## Use Case Diagram

### Diagram Description
The Use Case Diagram illustrates the interactions between three main actors (Guest, Host, Admin) and the Airbnb Clone system, covering all core functionalities from user registration to booking management and administrative tasks.

### Key Actors
1. **Guest** - Users who search for and book properties
2. **Host** - Users who list and manage their properties
3. **Admin** - System administrators who manage the platform

### Core Use Cases

#### Guest Use Cases
- **Account Management**: Register, Login, Update Profile
- **Property Discovery**: Search Properties, View Property Details, Save Favorites
- **Booking Management**: Make Booking, Cancel Booking, View Booking History
- **Reviews & Communication**: Write Reviews, Message Hosts
- **Payment**: Make Payments, View Payment History

#### Host Use Cases
- **Property Management**: List Property, Update Property, Manage Availability
- **Booking Management**: Accept/Decline Bookings, View Booking Calendar
- **Communication**: Respond to Messages, Respond to Reviews
- **Financial**: View Payouts, Manage Pricing

#### Admin Use Cases
- **User Management**: Manage Users, Moderate Content
- **Platform Management**: View Analytics, Manage System Settings
- **Financial Oversight**: View Financial Reports

## Mermaid Code for Diagram
```mermaid
graph TD
    subgraph Actors
        A1[Guest]
        A2[Host] 
        A3[Admin]
    end

    subgraph Authentication
        B1[Register]
        B2[Login]
        B3[Update Profile]
    end

    subgraph PropertyManagement
        C1[List Property]
        C2[Update Property]
        C3[Manage Availability]
        C4[Search Properties]
        C5[View Property Details]
        C6[Save Favorites]
    end

    subgraph BookingManagement
        D1[Make Booking]
        D2[Cancel Booking]
        D3[Accept/Decline Booking]
        D4[View Booking History]
        D5[View Booking Calendar]
    end

    subgraph PaymentSystem
        E1[Make Payment]
        E2[View Payment History]
        E3[View Payouts]
        E4[Manage Pricing]
    end

    subgraph ReviewsMessaging
        F1[Write Reviews]
        F2[Respond to Reviews]
        F3[Message Users]
        F4[Respond to Messages]
    end

    subgraph AdminFunctions
        G1[Manage Users]
        G2[Moderate Content]
        G3[View Analytics]
        G4[View Financial Reports]
        G5[Manage System Settings]
    end

    %% Guest Relationships
    A1 --> B1
    A1 --> B2
    A1 --> B3
    A1 --> C4
    A1 --> C5
    A1 --> C6
    A1 --> D1
    A1 --> D2
    A1 --> D4
    A1 --> E1
    A1 --> E2
    A1 --> F1
    A1 --> F3

    %% Host Relationships
    A2 --> B1
    A2 --> B2
    A2 --> B3
    A2 --> C1
    A2 --> C2
    A2 --> C3
    A2 --> D3
    A2 --> D5
    A2 --> E3
    A2 --> E4
    A2 --> F2
    A2 --> F4

    %% Admin Relationships
    A3 --> B2
    A3 --> G1
    A3 --> G2
    A3 --> G3
    A3 --> G4
    A3 --> G5

    %% System Boundaries
    subgraph System Boundary
        Authentication
        PropertyManagement
        BookingManagement
        PaymentSystem
        ReviewsMessaging
        AdminFunctions
    end
