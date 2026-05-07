# Overview

[This pipeline](https://github.com/oucru-id/tb-to-fhir-deeplex) is a Nextflow-based pipeline designed for the analysis of TB genomic data from Deeplex Myc-TB. It processes Deeplex excel sheet to identify drug resistance mutations, TB lineages, and generates a [HL7](https://fhir.org/) FHIR-compliant genomics bundle (Observations, DiagnosticReport).

```{image} _static/Deeplex_workflow_v1.4.png
:alt: Pipeline Workflow
:width: 1000px
:align: center
```

### Directory structure
```
tb-to-fhir-deeplex
├── main.nf                          # Main workflow
├── nextflow.config                  # Configuration
├── workflows/
│   ├── deeplex.nf                   # Deeplex processing
│   ├── upload_fhir.nf               # FHIR uploader
│   └── utils.nf                     # Utility functions
├── scripts/
│   ├── xlsx_json_converter.py       # Deeplex to FHIR converter
│   ├── merge_clinical_deeplex.py    # DiagnosticReport data merge
│   └── get_versions.py              # Version collection
│   └── upload_fhir.py               # FHIR uploader
│   └── get_access_token.py          # Standalone script to get the access token to FHIR server
└── data/
│   ├── Deeplex/
│   └── input_sso.json                 # SSO info to generate token
│   └── access_token.json              # Access token generated
│   └── sampletopatientid_mapping.csv  # Mapping patient UUID with Deeplex's sample ID 
```
