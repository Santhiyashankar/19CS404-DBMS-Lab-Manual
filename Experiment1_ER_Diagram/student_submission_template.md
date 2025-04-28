# ER Diagram Submission - Santhiya S 212223220098

## Scenario Chosen:
University 

## ER Diagram:
![image](https://github.com/user-attachments/assets/307beabc-5855-4bab-9193-d13d6fa275c8)


## Entities and Attributes:
1.Patient:
Attributes: Patient ID (PK), Name, DOB, Gender, Address, Phone, Insurance details.
2.Doctor:
Attributes: Doctor ID (PK), Name, Specialization, Email, Phone, Work schedule.
3.Appointment:
Attributes: Appointment ID (PK), Appointment date & time, Reason to visit, Additional notes.
4.Billing:
Attributes: Bill ID (PK), Date of payment, Payment status, Total amount.
5.Payment:
Attributes: Payment ID (PK), Transaction date, Payment method, Amount paid.
6.Medical Record:
Attributes: Medical record ID (PK), Diagnoses, Medications, Treatments, Test results.
7.Department:
Attributes: Dept ID (PK), Dept name, Dept head.

## Relationships and Constraints:
1.Patient books Appointment (1-to-many):
One patient can book multiple appointments.

2.Appointment generates Billing (1-to-1):
Every appointment generates exactly one billing record.

3.Billing associated with Payment (1-to-1 or 1-to-many):
Each billing can have one or multiple payment records (e.g., if split payments are allowed).

4.Doctor has Appointment (1-to-many):
One doctor can have multiple appointments.

5.Doctor belongs to Department (many-to-1):
Many doctors belong to one department.

6.Patient has Medical Record (1-to-many):
Each patient can have multiple medical records over time.

7.Doctor contributes to Medical Record (many-to-many implied via Medical Record):
A medical record is linked to both a doctor and a patient.

## Extension (Prerequisite / Billing):
Billing is triggered after Appointment:
Modeled through a "generates" relationship between Appointment and Billing.

Payment is linked to Billing:
Billing details (amount due, date, status) are tracked separately from actual payments, allowing for partial payments or overdue billing scenarios.

Constraints:
Appointment must exist before a bill can be created.
Bill must exist before payment can happen.
Patient must exist to create appointments and medical records.

## Design Choices:
Separation of Billing and Payment:
To allow flexibility in payment options (e.g., partial payments, refunds, payment plans).

Doctor and Department Separation:
Doctors can change departments; departments can have multiple doctors. This improves scalability for large hospitals.

Medical Record as a separate entity:
Medical records can be extensive and tied to multiple visits or doctors, so a separate entity helps manage growth and privacy better.

Appointment as a central event:
Appointment is the starting point for both billing and medical updates, making it the anchor for financial and clinical workflows.


