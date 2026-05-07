# Installation

## Prerequisites
To run this pipeline, you need the following prerequisites:

*   [Nextflow](https://www.nextflow.io/)
*   [Python](https://www.python.org/)

## Setup
1.  Clone the repository for local installation:
    ```bash
    git clone https://github.com/oucru-id/tb-to-fhir-deeplex.git
    cd tb-to-fhir-deeplex
    ```
2.  Install Nextflow:
    ```bash
    curl -s https://get.nextflow.io | bash
    ```
3.  Testing the Nextflow install:
    ```bash
    nextflow -v
    ```
4.  Get Access Token to FHIR Server:
    ```bash
    python3 scripts/get_access_token.py
    ```
5.  Basic Run:
    ```bash
    nextflow run main.nf
    ```
6.  Run and Upload to FHIR Server:
   Notes: need to get access token first before running the pipeline
    ```bash
    nextflow run main.nf \
      --fhir_server_url "https://<BASE_URL>/fhir"
    ```
