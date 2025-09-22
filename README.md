# Web-Assignment-8
# ClinicBookingSystem - Raw README

## Database Name
ClinicBookingSystem

## Tables and Relationships

1. Patients
- patient_id (PK)
- full_name
- date_of_birth
- gender (ENUM: Male, Female, Other)
- phone (UNIQUE)
- email (UNIQUE)

2. Doctors
- doctor_id (PK)
- full_name
- specialty
- phone (UNIQUE)
- email (UNIQUE)

3. Appointments
- appointment_id (PK)
- patient_id (FK → Patients)
- doctor_id (FK → Doctors)
- appointment_date
- status (ENUM: Scheduled, Completed, Cancelled)

4. Rooms
- room_id (PK)
- room_number (UNIQUE)
- room_type (ENUM: Consultation, Surgery, Recovery)

5. DoctorRoomAssignments
- doctor_id (FK → Doctors)
- room_id (FK → Rooms)
- assigned_on
- Composite PK: (doctor_id, room_id)

6. Prescriptions
- prescription_id (PK)
- appointment_id (FK → Appointments, UNIQUE)
- medication
- dosage
- instructions

## Relationships Summary
- Patients → Appointments: One-to-Many
- Doctors → Appointments: One-to-Many
- Doctors ↔ Rooms: Many-to-Many via DoctorRoomAssignments
- Appointments → Prescriptions: One-to-One

## Notes
- All foreign keys enforce referential integrity.
- ENUMs used for controlled value domains.
- Unique constraints on phone, email, room_number.
- Composite primary key used in DoctorRoomAssignments.
