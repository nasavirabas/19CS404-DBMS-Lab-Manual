## ER Diagram Submission 
## Name - Sabarivasan V
## Register No - 212222060206

## Scenario Chosen:
 Hospital Management System - ER Diagram

## ER Diagram:
![Screenshot 2025-04-30 060300](https://github.com/user-attachments/assets/796865d6-081d-4f4b-9139-1ebfeb7712c0)

## Entities and Attributes:

1. PATIENT
   
Attributes:
PATIENT_ID (Primary Key),
NAME,
GENDER,
EMAIL_ID,
PHONE_NO

2. APPOINTMENT

Attributes:
APPOINT_ID (Primary Key),
TIMING

3. DOCTOR
   
Attributes:
DOCTOR_ID (Primary Key),
NAME,
EMAIL_ID,
EXPERIENCE,
SALARY

4. DEPARTMENT

Attributes:
DEPT_ID (Primary Key),
NAME,
LOCATION

## Relationships and Constraints:


1. BOOK (between PATIENT and APPOINTMENT)

Cardinality: One PATIENT can book many APPOINTMENTs; one APPOINTMENT is booked by one PATIENT.

Participation: Total on PATIENT side (each appointment must be booked by a patient)


2. ASSIGN (between APPOINTMENT and DOCTOR)

Cardinality: One APPOINTMENT is assigned to one DOCTOR; one DOCTOR can have many APPOINTMENTs.

Participation: Total on both sides (every appointment must have a doctor, and every doctor is assigned at least one appointment)


3. SPECIALIZATION (between DOCTOR and DEPARTMENT)

Cardinality: One DOCTOR belongs to one DEPARTMENT; one DEPARTMENT can have many DOCTORs.

Participation: Total on DOCTOR side

## Extension (Prerequisite / Billing):

Billing is not shown in this diagram. However, it could be modeled by:
Creating a new BILLING entity with attributes such as BILL_ID, AMOUNT, METHOD, etc.
Connecting it with the APPOINTMENT entity via a relationship like PAY.

Prerequisite logic (e.g., doctor qualification before assignment) is indirectly represented via the EXPERIENCE and SPECIALIZATION attributes but isn't enforced explicitly in this diagram.

## Design Choices:

1. Clear Entity Separation: Each real-world object (patient, doctor, appointment, department) is modeled as a separate entity.

2. Attributes Directly Tied: All relevant information is directly tied to its entity for simplicity.

3. Logical Relationships: BOOK, ASSIGN, and SPECIALIZATION relationships logically represent interactions between entities.

4. Normalization: Redundancy is avoided by separating DOCTOR and DEPARTMENT.

5. Proper Use of Primary Keys: Unique identifiers (IDs) are used for easy relational mapping in databases.

## Result:

The ER diagram successfully models a hospital system where patients book appointments with doctors, and doctors belong to departments.
It clearly represents entities, relationships, and constraints required for efficient appointment and doctor management..
