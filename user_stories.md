## User Stories – Smart Clinic Management System

This document presents user stories for Admins, Doctors, and Patients using a standardized template format.

---

### Admin User Stories

As an Admin, I want to securely manage doctor accounts and monitor system usage, so that I can maintain control and visibility over the platform._

**Acceptance Criteria:**
1. Admin must be able to log into the portal using a valid username and password.
2. Admin must be able to securely log out of the portal to end their session and protect system access.
3. Admin can add a new doctor by providing required information such as name, specialization, email, and availability.
4. Admin can delete a doctor's profile from the system, and associated data should be handled according to data retention policies.
5. Admin has access to a script or MySQL stored procedure via the CLI that returns the number of appointments grouped by month.
6. The stored procedure must return results with month names, appointment counts, and optionally percentage growth compared to the previous month.
7. An error message should be displayed if login fails due to incorrect credentials.
8. Deletion of doctors must include a confirmation step to avoid accidental removal.
9. Admin can run the MySQL stored procedure securely with read-only access for reporting purposes.

**Priority:** High  
**Story Points:** 8  
**Notes:**
- Login and logout must follow security best practices (e.g., session timeout, hashed passwords).
- Adding and deleting doctors should update the UI immediately and reflect changes in real-time.
- The stored procedure might use `GROUP BY MONTH(appointment_date)` and `COUNT(*)` for aggregating data.
- Consider audit logging for admin actions such as delete or stored procedure executions.

---

### Doctor User Stories

As a Doctor, I want to manage my appointments, profile, and availability through the portal, so that I can stay organized and provide accurate information to my patients._

**Acceptance Criteria:**
1. Doctors must be able to securely log into the portal using their credentials.
2. Doctors must be able to log out of the portal to protect access to their personal and professional data.
3. After logging in, doctors can view a calendar of all their upcoming appointments, organized by date and time.
4. Doctors can mark specific days or time slots as unavailable, preventing patients from booking during those periods.
5. The system must update availability in real time across the booking interface.
6. Doctors can update their profile with fields such as name, specialization, phone number, and clinic hours.
7. Profile updates are immediately reflected to patients in the doctor search and booking modules.
8. Doctors can access a list of upcoming appointments and view patient details (name, reason for visit, and contact info) for each.
9. Only authenticated doctors should be able to view or modify their own data.
10. Unauthorized access to appointment or patient data must be prevented.

**Priority:** High  
**Story Points:** 8  
**Notes:**
- Appointment calendar should support daily, weekly, and monthly views.
- Unavailability markings should prevent conflicts with already scheduled appointments.
- Changes to the profile should trigger a confirmation message.
- Patient details must be limited to relevant appointment information, respecting privacy.


---

### Patient User Stories

As a Patient, I want to explore doctors and manage my appointments through the portal, so that I can book and prepare for consultations easily and securely._

**Acceptance Criteria:**
1. Patients can view a public list of available doctors without needing to log in or register.
2. Patients can sign up using a valid email and password to create an account for booking appointments.
3. Patients must be able to log in to the portal using their registered credentials.
4. Patients can securely log out of the portal to end their session and protect account access.
5. After logging in, patients can select an available doctor and book an hour-long appointment.
6. Appointments should be confirmed and stored in the system with time, date, and doctor details.
7. Patients can access a section in the portal that displays their upcoming appointments.
8. The appointment list must show relevant details (doctor, time, date, location) for preparation.
9. Login must validate credentials and show appropriate error messages for failures.
10. Unauthenticated users should not be able to access booking or personal appointment pages.

**Priority:** High  
**Story Points:** 8  
**Notes:**
- Doctor list (public) should include filters like specialization and availability.
- Email verification during sign-up is recommended for security.
- Appointments should have duration validation (e.g., fixed to 60 minutes).
- Sessions should expire after inactivity for account safety.
