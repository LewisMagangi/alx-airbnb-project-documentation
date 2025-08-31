# Airbnb Clone Backend - Use Case Diagram

## Overview

This document describes the use case diagram for the Airbnb Clone backend system. The diagram visualizes the interactions between different actors and the system's core functionalities.

## Use Case Diagram Description

### Actors

#### Primary Actors
1. **Guest User** - Unregistered users browsing the platform
2. **Registered User** - Authenticated users who can make bookings
3. **Host** - Property owners who list and manage properties
4. **Admin** - System administrators managing the platform

#### Secondary Actors (External Systems)
5. **Payment Gateway** - External payment processing system (Stripe, PayPal)
6. **Email Service** - External email service provider
7. **SMS Service** - External SMS notification service
8. **Map Service** - External mapping and location service

### Use Cases by Actor

#### Guest User Use Cases
- Browse Properties
- Search Properties
- View Property Details
- Filter Search Results
- View Reviews and Ratings
- Register Account
- Contact Support

#### Registered User Use Cases
- User Login/Logout
- Manage Profile
- Make Booking
- Cancel Booking
- View Booking History
- Leave Reviews
- Manage Favorites
- Update Payment Methods
- Receive Notifications
- Communication with Host

#### Host Use Cases
- Host Registration
- List Property
- Manage Property Listings
- Update Property Information
- Manage Availability Calendar
- Set Pricing
- Respond to Bookings
- Manage Booking Requests
- Communicate with Guests
- View Host Analytics
- Manage Property Photos
- Set House Rules
- View Earnings

#### Admin Use Cases
- Manage Users
- Moderate Content
- Manage Property Listings
- Handle Disputes
- Generate Reports
- Manage System Settings
- Monitor Platform Activity
- Handle Customer Support
- Manage Reviews
- Oversee Payments

#### Payment Gateway Use Cases
- Process Payments
- Handle Refunds
- Validate Payment Methods
- Send Payment Confirmations
- Process Host Payouts

#### Email Service Use Cases
- Send Booking Confirmations
- Send Password Reset Emails
- Send Promotional Emails
- Send Notification Emails

#### SMS Service Use Cases
- Send Booking Alerts
- Send Verification Codes
- Send Emergency Notifications

#### Map Service Use Cases
- Provide Location Data
- Show Property Locations
- Calculate Distances
- Provide Directions

### Key Use Case Relationships

#### Include Relationships
- Make Booking **includes** Process Payment
- Register Account **includes** Send Verification Email
- List Property **includes** Validate Property Information
- Cancel Booking **includes** Process Refund
- Leave Review **includes** Validate Booking History

#### Extend Relationships
- Browse Properties **extends** Filter Search Results
- Make Booking **extends** Apply Discount Code
- Manage Profile **extends** Upload Profile Picture
- List Property **extends** Add Property Photos
- View Property Details **extends** Check Availability

### System Boundary

All use cases are contained within the "Airbnb Clone Backend System" boundary, with external actors (Payment Gateway, Email Service, SMS Service, Map Service) interacting with the system from outside the boundary.

### Diagram Elements

#### Actors (Stick Figures)
- Guest User
- Registered User
- Host
- Admin
- Payment Gateway (with <<system>> stereotype)
- Email Service (with <<system>> stereotype)
- SMS Service (with <<system>> stereotype)
- Map Service (with <<system>> stereotype)

#### Use Cases (Ovals)
All use cases listed above should be represented as ovals within the system boundary.

#### Relationships (Lines)
- Solid lines connecting actors to their use cases
- Dashed lines with <<include>> for mandatory relationships
- Dashed lines with <<extend>> for optional relationships

### Usage Scenarios

#### Scenario 1: Guest Books a Property
1. Guest User browses properties
2. Guest User searches with filters
3. Guest User views property details
4. Guest User registers account (becomes Registered User)
5. Registered User makes booking
6. System processes payment via Payment Gateway
7. System sends confirmation via Email Service

#### Scenario 2: Host Lists a Property
1. Host registers account
2. Host logs in
3. Host lists new property
4. System validates property information
5. Host uploads property photos
6. Host sets pricing and availability
7. Admin reviews and approves listing

#### Scenario 3: Booking Management
1. Registered User views booking history
2. Registered User cancels booking
3. System processes refund via Payment Gateway
4. System sends cancellation confirmation via Email Service
5. Host receives notification via SMS Service

## Instructions for Creating the Diagram

To create this use case diagram in Draw.io:

1. **Start with System Boundary**
   - Draw a large rectangle labeled "Airbnb Clone Backend System"

2. **Add Actors**
   - Place actor stick figures outside the system boundary
   - Label each actor clearly
   - Use <<system>> stereotype for external system actors

3. **Add Use Cases**
   - Place oval shapes inside the system boundary
   - Label each use case with clear, action-oriented names
   - Group related use cases together

4. **Add Relationships**
   - Draw solid lines from actors to their use cases
   - Add <<include>> relationships with dashed arrows
   - Add <<extend>> relationships with dashed arrows
   - Ensure all relationships are clearly labeled

5. **Format and Export**
   - Use consistent colors and fonts
   - Ensure all text is readable
   - Export as PNG with high resolution
   - Save as "use-case-diagram.png"

This use case diagram provides a comprehensive view of all system interactions and serves as a foundation for developing user stories and system requirements.
