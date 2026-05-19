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
4.  Create and activate a virtual environment:
    ```bash
    python3 -m venv venv
    source venv/bin/activate
    ```
5.  Get Access Token to FHIR Server:
    Notes: need to fill input_sso.json first
    ```bash
    python3 scripts/get_access_token.py
    ```
7.  Basic Run:
    ```bash
    nextflow run main.nf
    ```
8.  Search for Patient UUID:
    Notes: need to get an access token first
    ```bash
    python scripts/get_patient_by_nik.py --nik 1234567890 --fhir_base_url "https://<BASE_URL>/fhir"
    ```
10.  Run and Upload to FHIR Server:
   Notes: need to get an access token and mapping patient UUID first before running the pipeline
    ```bash
    nextflow run main.nf \
      --fhir_server_url "https://<BASE_URL>/fhir"
    ```

## Setup (Docker)
1.  Pull Docker image:
    ```bash
    docker pull robind1/tb-to-fhir-deeplex:v1.4.1
    ```
2.  Get Access Token to FHIR Server:
    Notes: need to fill input_sso.json first
    ```bash
    docker run --rm \
      -v /your/host/data:/pipeline/data \
      robind1/tb-to-fhir-deeplex:v1.4.1 \
      get-token --sso /pipeline/data/input_sso.json --out /pipeline/data/access_token.json
    ```
6.  Basic Run:
    ```bash
    docker run --rm \
      -v /your/host/data:/pipeline/data \
      -v /your/host/results:/pipeline/results \
      robind1/tb-to-fhir-deeplex:v1.4.1 \
      run main.nf
    ```
7.  Search for Patient UUID:
    Notes: need to get an access token first
    ```bash
    docker run --rm \
      -v /your/host/data:/pipeline/data \
      robind1/tb-to-fhir-deeplex:v1.4.1 \
      get-patient \
      --nik 1234567890 \
      --fhir_base_url "https://<BASE_URL>/fhir"
    ```
9.  Run and Upload to FHIR Server:
   Notes: need to get an access token and mapping patient UUID first before running the pipeline
    ```bash
    docker run --rm \
      -v /your/host/data:/pipeline/data \
      -v /your/host/results:/pipeline/results \
      robind1/tb-to-fhir-deeplex:v1.4.1 \
      run main.nf --fhir_server_url "https://<BASE_URL>/fhir"
    ```
