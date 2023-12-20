## Pre-Reqs

- Python >= 3.11
- [OPTIONAL] VSCode to use built-in tasks
- Access to GCP Project enabled for BigQuery

## Setup

- update .env with appropriate values
    - note project ID not project name (manifests as 404 error)
    - `. .env` to update values in use in terminal
- get credentials
    - if no valid credential, then error message says default credentials not found
    - must be application default credential
    - `gcloud auth application-default login`
- `dbt debug` should now succeed and list settings/versions
