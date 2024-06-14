---
layout: default
title: Key Patient Characteristics
parent: Curated Assets
nav_order: 1
has_children: true
permalink: /docs/curated_assets/kpcs
---

# Key Patient Characterisitcs

## Motivation

* Desire to have common demographics table that everyone can use.

* NHS Data Wranglers curated assets: curr301_patient_skinny_unassembled & curr302_patient_skinny_record. These tables are no longer maintained.

* BHF DSC HDS common functions: key_patient_characteristics_harmonise & key_patient_characteristics_select. These functions were run by every project in every pipeline.

* Monthly curated assets that can be reused by multiple projects as part of a project pipeline or for exploratory data analysis.

* New terminology: multisource tables, individual tables, demographics table.

* Provide a multisource table for projects to apply their own bespoke selection algorithm.

* Provide an individual table that applies the HDS selection algorithm + new algorithm features.

* Provide functions, examples and insight to bespoke algorithms.

## Characteristics of Interest

| Demographic Data       | Multisource Tables | Individual Tables | Demographics Table |
|------------------------|---------------------|-------------------|--------------------|
| Date of Birth          | ✔                   | ✔                 | ✔                  |
| Sex + Mappings         | ✔                   | ✔                 | ✔                  |
| Ethnicity + Mappings   | ✔                   | ✔                 | ✔                  |
| LSOA                   | ✔                   | ✔                 | ✔                  |
|   - Region             |                     |                   | ✔                  |
|   - IMD Quintile       |                     |                   | ✔                  |
|   - IMD Decile         |                     |                   | ✔                  |
| Death                  |                     |                   | ✔                  |
|   - Date of Death      |                     |                   | ✔                  |
| In GDPPR               |                     |                   | ✔                  |




---
