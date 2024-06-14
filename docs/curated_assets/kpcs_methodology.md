---
layout: default
title: Methodology
nav_order: 2
parent: Key Patient Characteristics
grand_parent: Curated Assets
permalink: /docs/curated_assets/kpcs/methodology
---

# Code

Stable
{: .label .label-green }

[View code on GitHub](Code Repo for KPCs){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 }

[Code Repo for KPCs]: [https://just-the-docs.com](https://github.com/fionnachalmers)

# Methodology

## Multisource Tables

The multisource tables consolidate a characteristic from multiple data sources. The data sources included so far are below. We will add data sources to this resource when the need arises - sources included so far have been project led. 

| Data Source    | DOB | Sex | Ethnicity | LSOA | Record Date                  |
|----------------|-----|-----|-----------|------|------------------------------|
| GDPPR - all archived versions          | ✔   | ✔   | ✔         | ✔    | reporting_period_end_date    |
| GDPPR - snomed codes   |     |     | ✔         |      | record_date (date if missing)|
| HES-APC        | ✔   | ✔   | ✔         | ✔    | epistart                     |
| HES OP         | ✔   | ✔   | ✔         | ✔    | apptdate                     |
| HES AE         | ✔   | ✔   | ✔         | ✔    | arrivaldate                  |
| SSNAP          | ✔   | ✔   |           | ✔    | s1firstarrivaldatetime       |
| Vaccine status | ✔   |     |           | ✔    | recorded_date                |



* Date of Birth is only ever accurate to month and year and imputed with Day = 01
* For HES OP, HES AE and SSNAP, an imputation algorithm is applied to derive Date of Birth from Age. Age represents completed years therefore, an upward adjustment of 0.5 years has been applied to approximate fractional ages.

> {: .new}
> > GDPPR is derived from a JOURNALS (coded data) and PATIENTS (demographic) table whereby the latter contains the most up-to-date view of a patient’s demographics. Thus, demographics in GDPPR are not record specific. Using the latest batch of the extract will include the characteristic only as at its most recent recording but accessing all batches allows a person’s full history to be captured. 

{: .highlight }
**No data cleaning is ever applied to the multisource table.**

https://www.nature.com/articles/s41597-024-02958-1

### Example

We source date of birth from the following sources:

**GDPPR**

| NHS_NUMBER_DEID | YEAR_OF_BIRTH | REPORTING_PERIOD_END_DATE |
|-----------------|---------------|---------------------------|
| A               | 1975-09       | 2020-05-18                |
| A               | 1975-09       | 2021-01-03                |
| A               | 1975-09       | 2023-08-09                |
| B               | 1980-10       | 2022-10-02                |
| B               | 1980-10       | 2024-05-09                |

**HES APC**

| PERSON_ID_DEID | MYDOB  | EPISTART    |
|----------------|--------|-------------|
| A              | 1975-09| 1800-01-01  |
| A              | 1975-09| 1998-04-14  |
| A              | 1975-09| 2024-02-20  |
| B              | 1980-10| 1801-01-01  |
| B              | 1980-10| 2023-12-13  |

**HES AE**

| PERSON_ID_DEID | ARRIVALAGE_CALC | ARRIVALDATE |
|----------------|------------------|-------------|
| B              | 23               | 2003-10-11  |
| B              | 34               | 2015-01-02  |
| B              | 42               | 2023-09-09  |

**HES OP**

| PERSON_ID_DEID | APPTAGE_CALC | APPTDATE   |
|----------------|--------------|------------|
| A              | 34           | 2010-09-01 |
| A              | 24           | 2004-11-02 |

**SSNAP**

| PERSON_ID_DEID | S1AGEONARRIVAL | S1FIRSTARRIVALDATETIME |
|----------------|----------------|------------------------|
| A              | 47             | 2023-06-01             |
| A              | 47             | 2023-06-12             |
| A              | 47             | 2023-09-03             |
| A              | 48             | 2023-12-03             |

They are then harmonised and concatenated into the table hds_curated_assets_date_of_birth_multisource_YYYY_MM_DD:


| PERSON_ID | DATE_OF_BIRTH | RECORD_DATE | DATA_SOURCE |
|-----------|----------------|-------------|-------------|
| A         | 1975-09-01     | 2020-05-18  | GDPPR       |
| A         | 1975-09-01     | 2021-01-03  | GDPPR       |
| A         | 1975-09-01     | 2023-08-09  | GDPPR       |
| B         | 1980-10-01     | 2022-10-02  | GDPPR       |
| B         | 1980-10-01     | 2024-05-09  | GDPPR       |
| A         | 1975-09-01     | 1800-01-01  | HES APC     |
| A         | 1975-09-01     | 1995-04-14  | HES APC     |
| A         | 1975-09-01     | 2024-02-20  | HES APC     |
| B         | 1985-10-01     |             | HES APC     |
| B         | 1980-10-01     | 2023-12-13  | HES APC     |
| B         | 1981-04-11     | 2003-10-11  | HES AE      |
| B         | 1980-07-02     | 2015-01-02  | HES AE      |
| B         | 1981-03-09     | 2023-09-09  | HES AE      |
| A         | 1977-03-01     | 2010-09-01  | HES OP      |
| B         | 1982-05-02     | 2004-11-02  | HES OP      |
| A         | 1975-12-01     | 2023-06-01  | SSNAP       |
| A         | 1975-12-12     | 2023-06-12  | SSNAP       |
| A         | 1976-03-03     | 2023-09-03  | SSNAP       |
| A         | 1976-06-01     | 2023-12-01  | SSNAP       |



### Mapping

Codes have been mapped to their descriptions for Sex and Ethnicity, by data source.

For example:

| sex_code | sex_description                                                                         | sex |
|----------|-----------------------------------------------------------------------------------------|-----|
| 0        | Not known (not recorded)                                                                | NULL |
| 1        | Male                                                                                    | M   |
| 2        | Female                                                                                  | F   |
| 9        | Not specified (indeterminate, i.e. unable to be classified as either male or female)   | I   |


| ethnicity_raw_code | ethnicity_raw_description                                  | ethnicity_18_code | ethnicity_18_group           | ethnicity_5_group       |
|--------------------|------------------------------------------------------------|-------------------|------------------------------|-------------------------|
| 93941000000        | Greek Cypriot – ethnic finding 2001 census (finding)       | C                 | Any other White background   | White                   |
| C                  | Any other White background                                 | C                 | Any other White background   | White                   |
| 7                  | Chinese                                                    | R                 | Chinese                      | Asian or Asian British  |
| ...                | ...                                                        | ...               | ...                          | ...                     |


## Individual Tables

We apply data cleaning, data restrictions and finally a selection algorithm to produce a one-record-per-person table.

**Data Cleaning**


* Characteristic of interest must be valid i.e. Not Null/NA or blank. Codes that were mapped to Not Given/Stated/Known or Unknown are considered invalid. 

* Record date must be valid i.e. Not Null/NA or blank. 

* Additionally for Date of Birth: Date of Birth must be ≤ Record Date


**Data Resctictions**

Available as function arguments:

* Filter out data sources from the multisource table that are not used in the HDS selection algorithm.

* Record date must be ≥ 1900-01-01 

* Record date must be ≤ most recent archived_on date (the max archived_on date for each data source is considered)


