# Data Processing

## Main Workflow
**File:** `main.nf`
The main workflow handles channel processing and parallel execution.

## Deeplex Excel Report Workflow
**File:** `deeplex.nf`
For processing Deeplex Myc-TB output files (Excel format)
1.  **Conversion**:
    *   Script: `xlsx_json_converter.py`
    *   Function: Parses Excel sheets ('Drug resistance variants', 'Uncharacterised variants', 'Phylo_Syn variants') to extract variant and lineage data.
    *   Mapping: Maps drugs to SNOMED CT and variants, lineage to LOINC.
2.  **Clinical Data Merge**:
    *   Script: `merge_clinical_deeplex.py`
    *   Function: Aggregates observations to DiagnosticReport.
    *   **Resistance Classification**: Classifies samples (e.g., MDR-TB, XDR-TB) based on detected drug resistance profiles.

## Workflow Parameter 
`nextflow.config` defines all input files, directories, versioning, and specific tool parameters, relative to the base directory ($baseDir).