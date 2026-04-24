# FHIR Standards

## Profiles Used

| Resource | Profile URL |
| :--- | :--- |
| **DiagnosticReport**| `http://hl7.org/fhir/uv/genomics-reporting/StructureDefinition/genomics-report` |
| **Observation (Laboratory)**| `http://terminology.hl7.org/CodeSystem/observation-category` |
| **Observation (Genetics)**| `http://terminology.hl7.org/CodeSystem/v2-0074` |
| **Variant**| `http://hl7.org/fhir/uv/genomics-reporting/StructureDefinition/variant` |

## Standard Terminologies

### LOINC Codes (Sputum & Genomics)

| Code | Display Name | Usage |
| :--- | :--- | :--- |
| **69548-6** | Genetic variant assessment | Observation (Variant) |
| **89486-5** | Mycobacterial susceptibility panel | Observation (Panel) |
| **81247-9** | Master HL7 genetic variant reporting panel | DiagnosticReport |
| **79162-1** | Deeplex Myc-TB codon change | Variant Component |
| **48005-3** | Amino acid change (pHGVS) | Variant Component |
| **48018-6** | Gene studied [ID] | Variant Component |
| **53037-8** | Genetic variation clinical significance [Imp] | Variant Component (WHO Class) |
| **614-8** | Mycobacterial strain [Type] | Lineage Observation |

### LOINC Codes (Drug Susceptibility)
Used within the Susceptibility Panel Observation.

| Code | Display Name |
| :--- | :--- |
| **89489-9** | Rifampin [Susceptibility] by Genotype method |
| **89488-1** | Isoniazid [Susceptibility] by Genotype method |
| **92242-7** | Pyrazinamide [Susceptibility] by Genotype method |
| **89491-5** | Ethambutol [Susceptibility] by Genotype method |
| **96112-8** | Moxifloxacin [Susceptibility] by Genotype method |
| **20629-2** | levoFLOXacin [Susceptibility] |
| **96107-8** | Bedaquiline [Susceptibility] by Genotype method |
| **96111-0** | Linezolid [Susceptibility] by Genotype method |
| **96114-4** | Streptomycin [Susceptibility] by Genotype method |
| **89484-0** | Amikacin [Susceptibility] by Genotype method |

**WHO Classification**
| Code | Display Name | Usage |
| :--- | :--- | :--- |
| **LA26333-7** | http://loinc.org | Uncertain significance |
| **SP000478** | http://terminology.kemkes.go.id/sp | Assoc w R |
| **SP000479** | http://terminology.kemkes.go.id/sp | Assoc w R - Interim |
| **SP000481** | http://terminology.kemkes.go.id/sp | Not assoc w R |

### Clinical Conclusion Codes
Used in `DiagnosticReport.conclusionCode`.

| Diagnosis | Code | System |
| :--- | :--- | :--- |
| **Sensitive** | **TB-SO** | `https://terminology.kemkes.go.id/CodeSystem/episodeofcare-type` |
| **RR-TB** | **415345001** | `http://snomed.info/sct` |
| **HR-TB** | **414546009** | `http://snomed.info/sct` |
| **MDR-TB** | **423092005** | `http://snomed.info/sct` |
| **Pre-XDR-TB** | **OV000435** | `http://terminology.kemkes.go.id/CodeSystem/clinical-term` |
| **XDR-TB** | **710106005** | `http://snomed.info/sct` |
| **Streptomycin mono-resistant** | **415622003** | `http://snomed.info/sct` |
| **Ethionamide mono-resistant** | **414149006** | `http://snomed.info/sct` |
| **Pyrazinamide mono-resistant** | **415222009** | `http://snomed.info/sct` |
| **Ciprofloxacin mono-resistant** | **413852006** | `http://snomed.info/sct` |
| **Ethambutol mono-resistant** | **414146004** | `http://snomed.info/sct` |
| **Drug-resistant (Other)** | **413556004** | `http://snomed.info/sct` |