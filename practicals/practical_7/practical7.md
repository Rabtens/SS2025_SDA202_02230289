# Car Rental System - Sequence Diagram Documentation

## Overview

This sequence diagram illustrates the complete workflow of a car rental system, showing the interactions between different system components when processing a car rental request from initiation to billing completion.

## System Components

### Actors and Classes

- **Desk Officer**: The human operator who initiates the rental process
- **Billing System**: Handles all financial transactions and billing operations
- **FromRentCar**: The main rental processing interface
- **RentCarController**: Core business logic controller for rental operations
- **Car**: Represents the vehicle entity in the system
- **Customer**: The person renting the vehicle
- **Rental Record**: Maintains rental transaction history
- **BillingInterface**: Interface for billing system integration

## Process Flow

### 1. Rental Initiation (Steps 1-5)

1. **Enter Details**: Desk Officer inputs rental request details into the Billing System
2. **Check Availability**: System performs availability verification
3. **Rent Car**: Initial rental request is processed
4. **Find Car**: System locates an available vehicle matching requirements
5. **Set Status**: Car status is updated to "rented"

### 2. Record Creation (Steps 6-8)

1. **Message1**: Communication between Car and Customer entities
2. **Create Record**: New rental record is generated in the system
3. **Bill Customer**: Initial billing process is triggered

### 3. Billing Process (Steps 9-13)

1. **Bill Customer**: Detailed billing calculation and processing
2. **Display Completion Message**: Success confirmation is shown
3. **Set Status**: Car status is updated to "Available" (upon rental completion)
4. **Cancel**: Option to cancel the rental if needed
5. **Display Error Message**: Error handling for failed transactions

## Key Features

### Status Management

- Cars maintain real-time status tracking ("rented" → "available")
- Automatic status updates throughout the rental lifecycle

### Billing Integration

- Seamless integration between rental operations and billing system
- Real-time customer billing with completion confirmations
- Error handling for billing failures

### Record Keeping

- Comprehensive rental record creation and maintenance
- Customer and vehicle association tracking
- Transaction history preservation

## Error Handling

The system includes robust error handling mechanisms:

- **Availability Checking**: Prevents double-booking of vehicles
- **Billing Validation**: Ensures successful payment processing
- **Status Verification**: Confirms proper vehicle status transitions
- **Error Messaging**: Clear error communication for failed operations

## Workflow Summary

1. Desk officer initiates rental with customer details
2. System checks car availability and reserves vehicle
3. Car status is updated to "rented"
4. Rental record is created linking customer and vehicle
5. Customer billing is processed
6. Completion confirmation is displayed
7. Upon rental end, car status returns to "available"

This system ensures efficient car rental operations with proper tracking, billing, and error management throughout the entire rental lifecycle.