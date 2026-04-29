# Security Specification

## Data Invariants
1. Patients belong to a user (ownerId).
2. Prescriptions belong to a患者 (patientId) and a user (ownerId).
3. Invoices belong to a patient (patientId) and a user (ownerId).
4. All writes must validate schema and ownership.

## The "Dirty Dozen" Payloads (Examples)
1. Write patient with no ownerId.
2. Write patient with ownerId that doesn't match auth.uid.
3. Write invoice for a patient belonging to someone else.
4. Update invoice totalAmount to a negative value.
5. Create prescription with invalid medicine format.
6. Create patient with empty name.
7. Attempt to read other users' patients (List).
8. Attempt to read other users' patients (Get).
9. Attempt to delete other users' prescriptions.
10. Inject large string into ID field.
11. Update status to invalid value.
12. Modify createdAt/updatedAt directly.

## Test Runner (firestore.rules)
(To be implemented in `firestore.rules.test.ts` if needed, currently manual review of rules)
