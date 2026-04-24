# Version

### Pipeline Version
1.4.0

### Software Dependencies
Specific versions used in your run are automatically captured in the `software_versions.yml`.

### Platform Information
[Deeplex Myc-TB](https://www.deeplex.com/deeplex-myc-tb-tuberculosis-drug-resistance-diagnostic-kit/)

### [v1.4.0]
- Removed VCF processing, lineage analysis, and sample report generation.
- Fixed UPLOAD_FHIR process to FHIR transaction bundles.
- Removed VCF-related parameters (vcf_dir, reference, repetitive_regions, lineage_barcode, clinical_metadata).
- Add custom LOINC code for specific Deeplex codon change (replacing gHGVS).

## References
1.  Di Tommaso, P., et al. (2017). *Nextflow enables reproducible computational workflows*. [Nature Biotechnology](https://www.nature.com/articles/nbt.3820).
2.  Genomics Reporting Implementation Guide v3.0.0. [Variant Reporting](https://hl7.org/fhir/uv/genomics-reporting/index.html)
