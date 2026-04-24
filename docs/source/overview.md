# Overview

[This pipeline](https://github.com/oucru-id/tb-to-fhir-deeplex) is a Nextflow-based pipeline designed for the analysis of TB genomic data from Deeplex Myc-TB. It processes Deeplex excel sheet to identify drug resistance mutations, TB lineages, and generates a [HL7](https://fhir.org/) FHIR-compliant genomics bundle (Observations, DiagnosticReport).

```{image} _static/Deeplex_workflow_v1.4.png
:alt: Pipeline Workflow
:width: 1000px
:align: center
```
