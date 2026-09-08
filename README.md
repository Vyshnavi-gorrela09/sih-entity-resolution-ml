# SIH Entity Resolution ML

ML-based Entity Resolution and Confidence Scoring system developed for the Smart India Hackathon (SIH) prototype.

The system is designed for a unified government portal that integrates records from different sectors such as education and employment.

## Overview

Government systems may contain records of the same person in different portals with variations in:

- Name
- Date of birth
- Phone number
- Email address
- Address

For example, the same person may appear as:

- `Rahul Sharma`
- `Rahul K Sharma`
- `Rahul Kumar Sharma`

with differences in formatting, address, or other fields.

This project uses **Entity Resolution / Record Linkage** techniques to determine whether two records belong to the same person.

The system compares a primary user record with candidate records and produces:

- Field-level similarity scores
- Match confidence
- Final decision: `MATCH`, `REVIEW`, or `NOT_MATCH`

---

## Key Idea

The system gives stronger importance to **phone number and email address**, while name, date of birth, and address provide supporting evidence.

The model learns how different combinations of these features indicate whether two records belong to the same person.

### Features used

- `name_similarity`
- `dob_match`
- `dob_day_diff`
- `phone_match`
- `email_match`
- `address_similarity`
- `dob_unknown`

Text similarity is calculated using **RapidFuzz**.

---

## Machine Learning Model

The current implementation uses:

**Logistic Regression**

with:

- StandardScaler
- Class balancing
- Probability-based prediction

The model outputs a probability representing the likelihood that two records belong to the same person.

Example:

```text
Confidence = 0.96
Decision   = MATCH  