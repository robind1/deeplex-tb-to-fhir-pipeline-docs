# Output Files
The primary output is a **HL7 FHIR Bundle** containing genomic observations merged with clinical data.
```{image} _static/Deeplex_bundle_v1.4.png
:alt: Deeplex FHIR Genomics Bundle
:width: 600px
:align: center
```

## FHIR Genomic Bundle
### 1. Variant Observation Resources
Each detected variant generates an observation (LOINC `69548-6`) containing:
*   **Genomic Coordinates**: 
    *   **Deeplex Myc-TB codon change**: (e.g., `cac445gac`) - LOINC `79162-1`.
    *   **pHGVS**: Amino acid change (e.g., `NC_000962.3:p.(H445D)`) - LOINC `48005-3`.
*   **Gene Information**: The affected gene (e.g., *rpoB*) - LOINC `48018-6`.
*   **DNA Change Type**: Sequence Ontology term (e.g., *missense_variant*) - LOINC `48019-4`.
*   **Clinical Significance**: WHO classification (e.g., *Assoc w R*) - LOINC `53037-8`.

### Example: Variant Observation Resource

```json
    {
      "fullUrl": "urn:uuid:sample1-obs-1",
      "resource": {
        "resourceType": "Observation",
        "id": "sample1-obs-1",
        "meta": {
          "profile": [
            "http://hl7.org/fhir/uv/genomics-reporting/StructureDefinition/variant"
          ],
          "tag": [
            {
              "system": "http://terminology.kemkes.go.id/sp",
              "code": "genomics",
              "display": "Genomics"
            }
          ]
        },
        "status": "final",
        "category": [
          {
            "coding": [
              {
                "system": "http://terminology.hl7.org/CodeSystem/observation-category",
                "code": "laboratory",
                "display": "Laboratory"
              }
            ]
          },
          {
            "coding": [
              {
                "system": "http://terminology.hl7.org/CodeSystem/v2-0074",
                "code": "GE",
                "display": "Genetics"
              }
            ]
          }
        ],
        "code": {
          "coding": [
            {
              "system": "http://loinc.org",
              "code": "69548-6",
              "display": "Genetic variant assessment"
            }
          ]
        },
        "subject": {
          "reference": "Patient/sample1-patient"
        },
        "specimen": {
          "reference": "Specimen/sample1-specimen"
        },
        "effectiveDateTime": "2026-04-23T07:38:04.270765+00:00",
        "performer": [
          {
            "reference": "Organization/1"
          }
        ],
        "valueCodeableConcept": {
          "coding": [
            {
              "system": "http://loinc.org",
              "code": "LA9633-4",
              "display": "Present"
            }
          ],
          "text": "Present"
        },
        "component": [
          {
            "code": {
              "coding": [
                {
                  "system": "http://loinc.org",
                  "code": "48018-6",
                  "display": "Gene studied [ID]"
                }
              ]
            },
            "valueCodeableConcept": {
              "coding": [
                {
                  "system": "https://www.ncbi.nlm.nih.gov/gene",
                  "code": "rpoB1",
                  "display": "rpoB1"
                }
              ],
              "text": "rpoB1"
            }
          },
          {
            "code": {
              "coding": [
                {
                  "system": "http://loinc.org",
                  "code": "79162-1",
                  "display": "Deeplex Myc-TB codon change"
                }
              ]
            },
            "valueCodeableConcept": {
              "coding": [
                {
                  "system": "https://www.deeplex.com/",
                  "code": "cac445gac",
                  "display": "cac445gac"
                }
              ],
              "text": "cac445gac"
            }
          },
          {
            "code": {
              "coding": [
                {
                  "system": "http://loinc.org",
                  "code": "48005-3",
                  "display": "Amino acid change (pHGVS)"
                }
              ]
            },
            "valueCodeableConcept": {
              "coding": [
                {
                  "system": "https://varnomen.hgvs.org",
                  "code": "NC_000962.3:p.(H445D)",
                  "display": "H445D"
                }
              ],
              "text": "H445D"
            }
          },
          {
            "code": {
              "coding": [
                {
                  "system": "http://loinc.org",
                  "code": "53037-8",
                  "display": "Genetic variation clinical significance [Imp]"
                }
              ]
            },
            "valueCodeableConcept": {
              "coding": [
                {
                  "system": "http://terminology.kemkes.go.id/sp",
                  "code": "SP000478",
                  "display": "Assoc w R"
                }
              ],
              "text": "Associated with resistance"
            }
          }
        ]
      },
      "request": {
        "method": "PUT",
        "url": "Observation/sample1-obs-1"
      }
    }
```

### 2. Drug Susceptibility Panel Observation
A single summary observation (LOINC `89486-5`) reporting susceptibility status for specific drugs:
*   **Components**: Value for each drug (e.g., Rifampicin, Isoniazid, Bedaquiline).
*   **Values**: `Resistant` (LOINC `LA6676-6`) or `Susceptible` (LOINC `LA24225-7`).

### Example: Drug Susceptibility Panel Resource

```json
    {
      "fullUrl": "urn:uuid:02058040-0799-4258-9517-3b1df746c031",
      "resource": {
        "resourceType": "Observation",
        "id": "ERR2706911-susceptibility-panel",
        "meta": {
          "profile": [
            "http://hl7.org/fhir/StructureDefinition/Observation"
          ]
        },
        "text": {
          "status": "generated",
          "div": "<div xmlns=\"http://www.w3.org/1999/xhtml\">Mycobacterial susceptibility panel for ERR2706911</div>"
        },
        "status": "final",
        "category": [
          {
            "coding": [
              {
                "system": "http://terminology.hl7.org/CodeSystem/observation-category",
                "code": "laboratory",
                "display": "Laboratory"
              }
            ]
          },
          {
            "coding": [
              {
                "system": "http://terminology.hl7.org/CodeSystem/v2-0074",
                "code": "GE",
                "display": "Genetics"
              }
            ]
          }
        ],
        "code": {
          "coding": [
            {
              "system": "http://loinc.org",
              "code": "89486-5",
              "display": "Mycobacterial susceptibility panel Qualitative by Genotype method"
            }
          ]
        },
        "subject": {
          "reference": "Patient/ERR2706911-patient"
        },
        "specimen": {
          "reference": "Specimen/ERR2706911-specimen"
        },
        "effectiveDateTime": "2026-01-12T05:45:05.277192+00:00",
        "performer": [
          {
            "reference": "Organization/1"
          }
        ],
        "component": [
          {
            "code": {
              "coding": [
                {
                  "system": "http://loinc.org",
                  "code": "89489-9",
                  "display": "rifAMPin [Susceptibility] by Genotype method"
                }
              ]
            },
            "valueCodeableConcept": {
              "coding": [
                {
                  "system": "http://loinc.org",
                  "code": "LA24225-7",
                  "display": "Susceptible"
                }
              ]
            }
          },
          {
            "code": {
              "coding": [
                {
                  "system": "http://loinc.org",
                  "code": "89488-1",
                  "display": "Isoniazid [Susceptibility] by Genotype method"
                }
              ]
            },
            "valueCodeableConcept": {
              "coding": [
                {
                  "system": "http://loinc.org",
                  "code": "LA6676-6",
                  "display": "Resistant"
                }
              ]
            }
          },
          {
            "code": {
              "coding": [
                {
                  "system": "http://loinc.org",
                  "code": "89491-5",
                  "display": "Ethambutol [Susceptibility] by Genotype method"
                }
              ]
            },
            "valueCodeableConcept": {
              "coding": [
                {
                  "system": "http://loinc.org",
                  "code": "LA24225-7",
                  "display": "Susceptible"
                }
              ]
            }
          },
          {
            "code": {
              "coding": [
                {
                  "system": "http://loinc.org",
                  "code": "92242-7",
                  "display": "Pyrazinamide [Susceptibility] by Genotype method"
                }
              ]
            },
            "valueCodeableConcept": {
              "coding": [
                {
                  "system": "http://loinc.org",
                  "code": "LA24225-7",
                  "display": "Susceptible"
                }
              ]
            }
          },
          {
            "code": {
              "coding": [
                {
                  "system": "http://loinc.org",
                  "code": "96112-8",
                  "display": "Moxifloxacin [Susceptibility] by Genotype method"
                }
              ]
            },
            "valueCodeableConcept": {
              "coding": [
                {
                  "system": "http://loinc.org",
                  "code": "LA24225-7",
                  "display": "Susceptible"
                }
              ]
            }
          },
          {
            "code": {
              "coding": [
                {
                  "system": "http://loinc.org",
                  "code": "20629-2",
                  "display": "levoFLOXacin [Susceptibility]"
                }
              ]
            },
            "valueCodeableConcept": {
              "coding": [
                {
                  "system": "http://loinc.org",
                  "code": "LA24225-7",
                  "display": "Susceptible"
                }
              ]
            }
          },
          {
            "code": {
              "coding": [
                {
                  "system": "http://loinc.org",
                  "code": "96107-8",
                  "display": "Bedaquiline [Susceptibility] by Genotype method"
                }
              ]
            },
            "valueCodeableConcept": {
              "coding": [
                {
                  "system": "http://loinc.org",
                  "code": "LA24225-7",
                  "display": "Susceptible"
                }
              ]
            }
          },
          {
            "code": {
              "coding": [
                {
                  "system": "http://loinc.org",
                  "code": "96109-4",
                  "display": "Delamanid [Susceptibility] by Genotype method"
                }
              ]
            },
            "valueCodeableConcept": {
              "coding": [
                {
                  "system": "http://loinc.org",
                  "code": "LA24225-7",
                  "display": "Susceptible"
                }
              ]
            }
          },
          {
            "code": {
              "coding": [
                {
                  "system": "http://loinc.org",
                  "code": "93850-6",
                  "display": "Pretomanid [Susceptibility]"
                }
              ]
            },
            "valueCodeableConcept": {
              "coding": [
                {
                  "system": "http://loinc.org",
                  "code": "LA24225-7",
                  "display": "Susceptible"
                }
              ]
            }
          },
          {
            "code": {
              "coding": [
                {
                  "system": "http://loinc.org",
                  "code": "96114-4",
                  "display": "Streptomycin [Susceptibility] by Genotype method"
                }
              ]
            },
            "valueCodeableConcept": {
              "coding": [
                {
                  "system": "http://loinc.org",
                  "code": "LA24225-7",
                  "display": "Susceptible"
                }
              ]
            }
          },
          {
            "code": {
              "coding": [
                {
                  "system": "http://loinc.org",
                  "code": "89484-0",
                  "display": "Amikacin [Susceptibility] by Genotype method"
                }
              ]
            },
            "valueCodeableConcept": {
              "coding": [
                {
                  "system": "http://loinc.org",
                  "code": "LA24225-7",
                  "display": "Susceptible"
                }
              ]
            }
          },
          {
            "code": {
              "coding": [
                {
                  "system": "http://loinc.org",
                  "code": "89482-4",
                  "display": "Kanamycin [Susceptibility] by Genotype method"
                }
              ]
            },
            "valueCodeableConcept": {
              "coding": [
                {
                  "system": "http://loinc.org",
                  "code": "LA24225-7",
                  "display": "Susceptible"
                }
              ]
            }
          },
          {
            "code": {
              "coding": [
                {
                  "system": "http://loinc.org",
                  "code": "89483-2",
                  "display": "Capreomycin [Susceptibility] by Genotype method"
                }
              ]
            },
            "valueCodeableConcept": {
              "coding": [
                {
                  "system": "http://loinc.org",
                  "code": "LA24225-7",
                  "display": "Susceptible"
                }
              ]
            }
          },
          {
            "code": {
              "coding": [
                {
                  "system": "http://loinc.org",
                  "code": "96108-6",
                  "display": "Clofazimine [Susceptibility] by Genotype method"
                }
              ]
            },
            "valueCodeableConcept": {
              "coding": [
                {
                  "system": "http://loinc.org",
                  "code": "LA24225-7",
                  "display": "Susceptible"
                }
              ]
            }
          },
          {
            "code": {
              "coding": [
                {
                  "system": "http://loinc.org",
                  "code": "96110-2",
                  "display": "Ethionamide [Susceptibility] by Genotype method"
                }
              ]
            },
            "valueCodeableConcept": {
              "coding": [
                {
                  "system": "http://loinc.org",
                  "code": "LA24225-7",
                  "display": "Susceptible"
                }
              ]
            }
          },
          {
            "code": {
              "coding": [
                {
                  "system": "http://loinc.org",
                  "code": "96111-0",
                  "display": "Linezolid [Susceptibility] by Genotype method"
                }
              ]
            },
            "valueCodeableConcept": {
              "coding": [
                {
                  "system": "http://loinc.org",
                  "code": "LA24225-7",
                  "display": "Susceptible"
                }
              ]
            }
          },
          {
            "code": {
              "coding": [
                {
                  "system": "http://loinc.org",
                  "code": "103959-3",
                  "display": "cycloSERINE [Susceptibility] by Genotype method"
                }
              ]
            },
            "valueCodeableConcept": {
              "coding": [
                {
                  "system": "http://loinc.org",
                  "code": "LA24225-7",
                  "display": "Susceptible"
                }
              ]
            }
          }
        ]
      },
      "request": {
        "method": "PUT",
        "url": "Observation/ERR2706911-susceptibility-panel"
      }
    }
```

### 3. Lineage Observation
Classifies the TB strain (LOINC `614-8`) using `http://tb-lineage.org` codes (e.g., Lineage 1, Lineage 2).

### Example: Lineage Observation Resource

```json
    {
      "fullUrl": "urn:uuid:ceedc1e1-aab3-4235-be9c-54470f0ab612",
      "resource": {
        "resourceType": "Observation",
        "id": "ERR2706911-lineage",
        "meta": {
          "profile": [
            "http://hl7.org/fhir/StructureDefinition/Observation"
          ],
          "tag": [
            {
              "system": "http://terminology.kemkes.go.id/sp",
              "code": "genomics",
              "display": "Genomics"
            }
          ]
        },
        "text": {
          "status": "generated",
          "div": "<div xmlns=\"http://www.w3.org/1999/xhtml\">Mycobacterial Lineage: lineage4.7 (Euro-American)</div>"
        },
        "status": "final",
        "category": [
          {
            "coding": [
              {
                "system": "http://terminology.hl7.org/CodeSystem/observation-category",
                "code": "laboratory",
                "display": "Laboratory"
              }
            ]
          },
          {
            "coding": [
              {
                "system": "http://terminology.hl7.org/CodeSystem/v2-0074",
                "code": "GE",
                "display": "Genetics"
              }
            ]
          }
        ],
        "code": {
          "coding": [
            {
              "system": "http://loinc.org",
              "code": "614-8",
              "display": "Mycobacterial strain [Type] in Isolate by Mycobacterial subtyping"
            }
          ]
        },
        "valueCodeableConcept": {
          "coding": [
            {
              "system": "http://tb-lineage.org",
              "code": "lineage4.7",
              "display": "TB Lineage lineage4.7"
            }
          ],
          "text": "Lineage lineage4.7"
        },
        "subject": {
          "reference": "Patient/ERR2706911-patient"
        },
        "specimen": {
          "reference": "Specimen/ERR2706911-specimen"
        },
        "effectiveDateTime": "2026-01-12T05:45:05.277209+00:00",
        "performer": [
          {
            "reference": "Organization/1"
          }
        ]
      },
      "request": {
        "method": "PUT",
        "url": "Observation/ERR2706911-lineage"
      }
    }
  ]
}
```

## Clinical Data Integration & Reporting

### Generated Resources
*   **DiagnosticReport**: 
    *   **Code**: LOINC `81247-9` (Master HL7 genetic variant reporting panel).
    *   **Conclusion**: Text summary of resistance and lineage.
    *   **Presentation**: Base64 encoded HTML report.

## Drug Resistance Classification
The `DiagnosticReport` conclusion is derived using the following SNOMED CT logic order:

| Classification | Definition | Logic |
| :--- | :--- | :--- |
| **Sensitive** | No resistance detected | No Associated with Resistance mutation |
| **XDR-TB** | Extensively drug-resistant | (MDR or RR) + Resistance to **Fluoroquinolones** + **Group A** drugs |
| **Pre-XDR-TB** | Pre-Extensively drug-resistant | (MDR or RR) + Resistance to **Fluoroquinolones** |
| **MDR-TB** | Multidrug-resistant TB | Resistance to **both** Isoniazid and Rifampicin |
| **RR-TB** | Rifampicin-resistant TB | Resistance to **Rifampicin** detected (without Isoniazid) |
| **HR-TB** | Isoniazid-resistant TB | Resistance to **Isoniazid** detected (without Rifampicin) |
| **Streptomycin mono-resistant** | Streptomycin-resistant TB | Resistance to **Streptomycin** only |
| **Ethionamide mono-resistant** | Ethionamide-resistant TB | Resistance to **Ethionamide** only |
| **Pyrazinamide mono-resistant** | Pyrazinamide-resistant TB | Resistance to **Pyrazinamide** only |
| **Ethambutol mono-resistant** | Ethambutol-resistant TB | Resistance to **Ethambutol** only |
| **Ciprofloxacin mono-resistant** | Ciprofloxacin-resistant TB | Resistance to **Ciprofloxacin** only (without other Fluoroquinolones) |
| **Drug-resistant** | Antibiotic resistant tuberculosis | Any other resistance combination not falling into above categories |

### Example: DiagnosticReport conclusion code

```json
 ],
        "conclusion": "HR-TB (Isoniazid-resistant tuberculosis). Detected resistance genes: katG. Detected drug resistance: isoniazid  by genotype method. TB Lineage lineage4.7 detected. Reference genome: NC_000962.3",
        "conclusionCode": [
          {
            "text": "HR-TB",
            "coding": [
              {
                "system": "http://snomed.info/sct",
                "code": "414546009",
                "display": "Isoniazid resistant tuberculosis"
              }
            ]
          },
          {
            "text": "Lineage lineage4.7"
          }
        ],
        "presentedForm": [
          {
            "contentType": "text/html",
            "language": "en-US",
            "title": "TB Genomic Analysis Report",
            "data": "PGRpdiB4bWxucz0iaHR0cDovL3d3dy5......"
          }
        ]
      },
      "request": {
        "method": "PUT",
        "url": "DiagnosticReport/ERR2706911-genomic-report"
      }
    }
```

## Output Directory Structure

```bash
results/        
├── fhir/
│   └── *.fhir.json              
├── fhir_merged/
│   └── *.merged.fhir.json
├── runningstat/
│   └── dag.html
│   └── execution.html
│   └── timeline.html
├── software_versions.yml
```