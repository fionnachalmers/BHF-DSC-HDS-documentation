---
layout: default
title: Methodology
nav_order: 2
parent: Key Patient Characteristics
grand_parent: Curated Assets
permalink: /docs/curated_assets/kpcs/methodology
---

# Code


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
* GDPPR is derived from a JOURNALS (coded data) and PATIENTS (demographic) table whereby the latter contains the most up-to-date view of a patient’s demographics. Thus, demographics in GDPPR are not record specific. Using the latest batch of the extract will include the characteristic only as at its most recent recording but accessing all batches allows a person’s full history to be captured. 

**No data cleaning is ever applied to the multisource table.**

https://www.nature.com/articles/s41597-024-02958-1

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


** Data Resctictions**

Available as function arguments:

* Filter out data sources from the multisource table that are not used in the HDS selection algorithm.

* Record date must be ≥ 1900-01-01 

* Record date must be ≤ most recent archived_on date (the max archived_on date for each data source is considered)










