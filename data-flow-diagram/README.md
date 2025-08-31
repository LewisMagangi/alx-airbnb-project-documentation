# Data Flow Diagram - Airbnb Clone Backend

## Overview

This document describes the Data Flow Diagram (DFD) for the Airbnb Clone backend system. The DFD illustrates how data moves through the system, showing data inputs, processes, data stores, and outputs.

## DFD Components

### External Entities
1. **Guest User** - Users who browse without registration
2. **Registered User** - Authenticated users who can make bookings
3. **Host** - Property owners who list properties
4. **Admin** - System administrators
5. **Payment Gateway** - External payment processing system
6. **Email Service** - External email service provider
7. **SMS Service** - External SMS notification service

### Data Stores
1. **User Database** - Stores user profiles, authentication data
2. **Property Database** - Stores property listings, details, photos
3. **Booking Database** - Stores reservation information
4. **Payment Database** - Stores payment transactions, billing info
5. **Review Database** - Stores user reviews and ratings
6. **Notification Database** - Stores notification history and preferences
7. **Analytics Database** - Stores system analytics and reports

### Core Processes

#### Process 1: User Management
- **Input**: Registration data, login credentials, profile updates
- **Output**: User authentication tokens, profile information
- **Data Stores**: User Database
- **Description**: Handles user registration, authentication, and profile management

#### Process 2: Property Management
- **Input**: Property details, photos, pricing, availability
- **Output**: Property listings, search results
- **Data Stores**: Property Database, User Database
- **Description**: Manages property listing creation, updates, and search functionality

#### Process 3: Booking Management
- **Input**: Booking requests, date selections, guest information
- **Output**: Booking confirmations, availability updates
- **Data Stores**: Booking Database, Property Database, User Database
- **Description**: Handles reservation creation, modification, and cancellation

#### Process 4: Payment Processing
- **Input**: Payment information, booking details, refund requests
- **Output**: Payment confirmations, receipts, host payouts
- **Data Stores**: Payment Database, Booking Database
- **Description**: Processes payments, handles refunds, manages host payouts

#### Process 5: Review Management
- **Input**: Review submissions, ratings, moderation actions
- **Output**: Published reviews, rating aggregations
- **Data Stores**: Review Database, User Database, Booking Database
- **Description**: Manages user reviews and rating system

#### Process 6: Notification System
- **Input**: Trigger events, user preferences, message content
- **Output**: Email notifications, SMS alerts, push notifications
- **Data Stores**: Notification Database, User Database
- **Description**: Handles all system notifications and communications

#### Process 7: Analytics and Reporting
- **Input**: User activity, booking data, system metrics
- **Output**: Reports, dashboards, insights
- **Data Stores**: Analytics Database, all other databases
- **Description**: Generates analytics and business intelligence reports

## Data Flows

### User Registration and Authentication Flow
```
Guest User → [Registration Data] → Process 1 (User Management) → [User Profile] → User Database
Guest User → [Login Credentials] → Process 1 (User Management) → [Authentication Token] → Registered User
User Database → [User Profile] → Process 1 (User Management) → [Profile Data] → Registered User
```

### Property Listing Flow
```
Host → [Property Details] → Process 2 (Property Management) → [Property Record] → Property Database
Host → [Property Photos] → Process 2 (Property Management) → [Image Data] → Property Database
Process 2 (Property Management) → [Listing Confirmation] → Host
```

### Property Search Flow
```
Guest User/Registered User → [Search Criteria] → Process 2 (Property Management)
Property Database → [Property Data] → Process 2 (Property Management) → [Search Results] → User
```

### Booking Creation Flow
```
Registered User → [Booking Request] → Process 3 (Booking Management)
Property Database → [Availability Data] → Process 3 (Booking Management)
Process 3 (Booking Management) → [Payment Request] → Process 4 (Payment Processing)
Process 4 (Payment Processing) → [Payment Data] → Payment Gateway
Payment Gateway → [Payment Confirmation] → Process 4 (Payment Processing)
Process 4 (Payment Processing) → [Payment Status] → Process 3 (Booking Management)
Process 3 (Booking Management) → [Booking Record] → Booking Database
Process 3 (Booking Management) → [Booking Confirmation] → Registered User
Process 3 (Booking Management) → [Booking Notification] → Host
```

### Review Submission Flow
```
Registered User → [Review Data] → Process 5 (Review Management)
Booking Database → [Booking Verification] → Process 5 (Review Management)
Process 5 (Review Management) → [Review Record] → Review Database
Process 5 (Review Management) → [Review Notification] → Host
```

### Notification Flow
```
Process 1-7 → [Trigger Events] → Process 6 (Notification System)
User Database → [User Preferences] → Process 6 (Notification System)
Process 6 (Notification System) → [Email Data] → Email Service
Process 6 (Notification System) → [SMS Data] → SMS Service
Process 6 (Notification System) → [Notification Record] → Notification Database
```

### Analytics Flow
```
User Database → [User Metrics] → Process 7 (Analytics)
Property Database → [Property Metrics] → Process 7 (Analytics)
Booking Database → [Booking Metrics] → Process 7 (Analytics)
Payment Database → [Payment Metrics] → Process 7 (Analytics)
Process 7 (Analytics) → [Analytics Data] → Analytics Database
Process 7 (Analytics) → [Reports] → Admin
Process 7 (Analytics) → [Host Insights] → Host
```

## Data Dictionary

### User Data
- **UserID**: Unique identifier for users
- **Email**: User email address
- **Password**: Encrypted password
- **Profile**: User profile information (name, photo, verification status)
- **Preferences**: User notification and search preferences

### Property Data
- **PropertyID**: Unique identifier for properties
- **HostID**: Reference to property owner
- **Title**: Property title and description
- **Location**: Address and geographic coordinates
- **Amenities**: List of property features
- **Pricing**: Base price, fees, taxes
- **Availability**: Calendar and booking rules
- **Photos**: Property image URLs

### Booking Data
- **BookingID**: Unique identifier for bookings
- **PropertyID**: Reference to booked property
- **UserID**: Reference to guest user
- **Dates**: Check-in and check-out dates
- **Guests**: Number of guests
- **Status**: Booking status (pending, confirmed, cancelled, completed)
- **Total**: Total booking cost

### Payment Data
- **PaymentID**: Unique identifier for payments
- **BookingID**: Reference to associated booking
- **Amount**: Payment amount
- **Method**: Payment method used
- **Status**: Payment status
- **Timestamp**: Payment processing time

### Review Data
- **ReviewID**: Unique identifier for reviews
- **BookingID**: Reference to associated booking
- **Rating**: Numerical rating (1-5 stars)
- **Comment**: Written review text
- **Timestamp**: Review submission time

## DFD Levels

### Level 0 (Context Diagram)
Shows the entire system as a single process with external entities and major data flows.

### Level 1 (System Overview)
Breaks down the main system into 7 core processes with data stores and external entities.

### Level 2 (Detailed Processes)
Further decomposes each Level 1 process into sub-processes for detailed analysis.

## Instructions for Creating the DFD

To create this Data Flow Diagram in Draw.io:

1. **Start with External Entities**
   - Use rectangles for external entities
   - Place them around the perimeter of the diagram

2. **Add Data Stores**
   - Use open rectangles (missing one side) for data stores
   - Label clearly with meaningful names

3. **Add Processes**
   - Use circles or rounded rectangles for processes
   - Number processes (1.0, 2.0, etc.)
   - Use descriptive names

4. **Draw Data Flows**
   - Use arrows to show data movement
   - Label each arrow with specific data names
   - Ensure all processes have inputs and outputs

5. **Maintain DFD Rules**
   - External entities don't communicate directly
   - Data stores don't communicate directly
   - All data flows must be labeled
   - Processes must transform data

6. **Export and Save**
   - Export as high-resolution PNG
   - Save as "data-flow.png"

This Data Flow Diagram provides a comprehensive view of how data moves through the Airbnb Clone backend system, helping developers understand system architecture and data requirements.
