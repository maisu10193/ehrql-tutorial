# ehrQL tutorial – OpenSAFELY

## What this is
I completed the OpenSAFELY ehrQL tutorial in GitHub Codespaces (Nov 2026).
I built the QOF diabetes register and checked ACE inhibitor/ARB treatment for patients with proteinuria following instructions on the website.
- dataset_definition.py: QOF diabetes register
- medication.py: test ACE inhibitor/ARB treatment dataset

## What I learned and how it compares with my GMCR work
I learned ehrQL to do the same kinds of extractions I did in SQL on GMCR.

Different language, same ideas: reusable functions (is_alive_on, age_on), ready-made codelists, and extracting GP events and medications.

| GMCR (SQL) | ehrQL |
|---|---|
|Table with one row per patient (Patient_Link) |Patient frame (`patients`) |
| Table with many rows per patient (GP_Events) | Event frame (`clinical_events`) |
| Versioned code sets (`--> CODESET diabetes:1`) | Codelists from OpenCodelists (`codelist_from_csv`) |
| `WHERE code IN (SELECT ... FROM #CodeSet)` | `.where(...snomedct_code.is_in(codelist))` |
| Use reusable query to calculate age from different sources | Built-in `patients.age_on(date)` |


My GMCR SQL work is public in the gm-sde repo under my work account maiparkes58 
Example project 047 https://github.com/UoM-Data-Science-Platforms/gm-sde/tree/master/projects/047%20-%20Lai

## Setup note
The codespace didn’t build at first. The error log showed ehrQL needs Python 3.14, so I changed the codespace setup to use a Python 3.14 image, and then it worked.




## About the original template

This repo is a template for [the ehrQL tutorial][1].
It is part of the OpenSAFELY platform's technical documentation.

## About the OpenSAFELY platform

The OpenSAFELY platform is a secure analytics framework for electronic health records research in the NHS.

Instead of requesting access for slices of patient data and transporting them elsewhere for analysis,
the platform supports developing analytics against dummy data
and then running against the real data *within the same infrastructure that the real data is stored*.
Read more at [OpenSAFELY.org](https://opensafely.org).

[1]: https://docs.opensafely.org/ehrql/tutorial/
