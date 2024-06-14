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

| Demographic Data | Data Sources Included                                               |
|------------------|---------------------------------------------------------------------|
| Date of Birth<sup>1</sup>   | GDPPR, HES APC, HES OP<sup>2</sup>, HES AE<sup>2</sup>, SSNAP<sup>2</sup>       |
| Sex              | GDPPR, HES APC, HES OP, HES AE, SSNAP                               |
| Ethnicity        | GDPPR SNOMED, GDPPR, HES APC, HES OP, HES AE, SSNAP                 |
| LSOA             | GDPPR All Versions<sup>3</sup>, HES APC, HES OP, HES AE, Vaccine Status  |


1. Date of Birth is only ever accurate to month and year and imputed with Day = 01
2. Imputation algorithm applied to derive Date of Birth from Age. Age represents completed years therefore, an upward adjustment of 0.5 years has been applied to approximate fractional ages.
3. GDPPR is derived from a JOURNALS (coded data) and PATIENTS (demographic) table whereby the latter contains the most up-to-date view of a patient’s demographics. Thus, demographics in GDPPR are not record specific. Using the latest batch of the extract will include only LSOA as at its most recent recording but accessing all batches allows a person’s full history to be captured. 


