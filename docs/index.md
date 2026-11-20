# NUH SACT Research Metadata

This site is the **data dictionary and metadata reference** for the Systemic Anti-Cancer Therapy (SACT) research dataset from **Nottingham University Hospitals NHS Trust (NUH)**, one of the largest acute NHS trusts in England, serving a population of approximately 2.5 million across Nottinghamshire and surrounding counties.

The pages here describe the dataset's structure: its fields, data types, permitted values, and coding standards. The dataset is a pseudonymised research view; access to the data requires a formal data access request.

---

## Dataset

### [Systemic Anti-Cancer Therapy (SACT)](schema/index.md)

> **2009–present · Quarterly**

Patient-level records of systemic anti-cancer treatments (chemotherapy, targeted therapies, immunotherapy, and other drug-based cancer treatments) administered.

**What it contains:**

| Domain | Detail |
|---|---|
| Patient | Pseudonymised NHS number, year and month of birth, gender, Lower Layer Super Output Area (LLSOA) |
| Diagnosis | Primary ICD diagnosis, ICD-O morphology, SNOMED CT diagnosis code |
| Regimen | Treatment regimen acronym, intent (curative/palliative/adjuvant), adjunctive therapy type, co-morbidity adjustment, clinical trial flag |
| Cycle | Cycle number, start date, weight, WHO performance status |
| Drug administration | Drug name (BNF), dm+d code, dose, unit of measurement, route of administration (coded and SNOMED CT), administration date, administering organisation |
| Outcomes | Dose reduction, regimen completion (curative), reason not completed, non-curative benefit, toxicity |

**Coding standards:** ICD-10, ICD-O-3, SNOMED CT, NHS dm+d

---

## Geographic and Temporal Coverage

| Dataset | Geography | Start | End | Frequency |
|---|---|---|---|---|
| SACT | Nottinghamshire, England | January 2009 | Ongoing | Quarterly |
