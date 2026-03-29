# MobileAppProject2018
# Clinic Appointment & Queue Management System

## Overview

The Clinic Appointment & Queue Management System is a mobile application designed to simplify appointment booking and improve patient queue handling in clinics. The system helps minimize waiting time, prevent scheduling conflicts, and maintain an organized workflow through real-time queue updates and role-based access control.

## Objectives

- Provide an efficient platform for booking and managing appointments
- Reduce patient waiting time through queue optimization
- Implement role-based access control (RBAC)
- Demonstrate real-world application development using structured data models and logic

## Authentication and Authorization

### Authentication

The system supports basic user authentication:

- User registration (Sign Up)
- Login using email and password
- Logout functionality

### Authorization

The application uses role-based access control (RBAC) to manage permissions.

#### Patient

- Book appointments
- View appointments
- Update appointments
- Cancel appointments
- View queue position
- View estimated waiting time
- Check in upon arrival
- Receive turn alerts

#### Doctor

- View daily appointments
- Manage and control the patient queue
- Monitor checked-in patients

## Key Features

### Appointment Booking and Validation

- Patients can create, update, and cancel appointments
- Prevents double booking through time slot validation
- Only available time slots can be selected

### Queue Management

- Each appointment is automatically assigned a queue position
- The queue updates dynamically when:
  - A new appointment is added
  - An appointment is canceled
  - A patient is skipped or completed
- Ensures fair and structured patient flow

### Smart Waiting Time Estimation

The system calculates estimated waiting time using the formula:

`Estimated Waiting Time = Position x Average Consultation Time`

This helps patients plan their visit more effectively.

### Patient Check-in System

- Patients confirm arrival using a check-in feature
- Non-checked-in patients can be skipped by the doctor
- Improves clinic efficiency and reduces delays

### Turn Notification Alert

- Patients receive alerts when their turn is near
- Example: notification when queue position is less than or equal to 2

### Doctor Queue Management

Doctors can manage the queue using the following actions:

- Call Next Patient
  - Moves the queue forward by serving the first patient
- Skip Patient
  - Skips patients who are not checked in
  - Moves them to the end of the queue
- Mark as Completed
  - Removes the patient from the queue after consultation

All actions trigger automatic queue reordering and waiting time recalculation.

## Data Models

### User

- `id`
- `name`
- `email`
- `password`
- `role` (`Patient` or `Doctor`)

### Appointment

- `id`
- `patient_id`
- `doctor_id`
- `date`
- `status` (`Pending`, `Confirmed`, `Completed`, `Cancelled`)

### Queue

- `id`
- `appointment_id`
- `position`

## CRUD Operations

### Appointments

- Create: Book appointment
- Read: View appointments
- Update: Modify appointment
- Delete: Cancel appointment

### Queue

- Update: Adjust queue positions
- Reorder: Automatically shift positions after changes

## API Endpoints

- `POST /appointments` - Create appointment
- `GET /appointments` - Retrieve appointments
- `PUT /queue/:id` - Update queue position

## System Workflow

1. User registers and logs in
2. Patient books an appointment
3. The system validates time slot availability
4. The appointment is added to the queue with a position
5. The patient checks in upon arrival
6. The doctor manages the queue by calling, skipping, or completing patients
7. The queue updates dynamically
8. Waiting time is recalculated
9. The patient receives an alert when their turn is near

## Testing Strategy

### Unit Testing

- Queue ordering logic
- Waiting time calculation

### Widget Testing

- Appointment booking form
- Check-in functionality

### Integration Testing

- End-to-end workflow:
  - Booking
  - Queue assignment
  - Check-in
  - Queue update
  - Notification

## Future Enhancements

- Admin role for system management
- Push notifications
- Multi-doctor support
- Advanced analytics dashboard

## Conclusion

This project provides a practical solution for improving appointment scheduling and queue handling in clinical environments. By combining appointment management, queue optimization, waiting time estimation, and role-based access control, the system supports a smoother experience for both patients and doctors.
