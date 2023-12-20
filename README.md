A candidate template for a standalone dbt-core/dbt-bigquery based repository.

# Pre-Reqs

- Python >= 3.11
- [OPTIONAL] VSCode to use built-in tasks
- Access to GCP Project enabled for BigQuery

# Setup

- update .env with appropriate values
    - note project ID not project name (manifests as 404 error)
    - `. .env` to update values in use in terminal
- get credentials
    - if no valid credential, then error message says default credentials not found
    - must be application default credential
    - `gcloud auth application-default login`
- `dbt debug` should now succeed and list settings/versions

# Assumptions

This repo is setup based on assumptions of specific ways of working that I have found to work well.
I'll try and describe them here.

The aim is to apply tried and tested practices that I generally refer to as "engineering" to analytics, so that trust and value can develop.
The following set of principles help explain the choices in this repo structure.

## Data-as-a-Product

Whilst this repo can be used for ad-hoc exploration, it's intended to support a shared set of data that consumers can influence and then build on with confidence.

## You Build It You Run It

A team is responsible for actively developing the data product this repository describes. That team is responsible for operating the product, resolving issues, and maintaining appropriate stability and robustness to build trust with consumers.

## Trunk-Based Development

There is a `main` branch, which is the current version of the data product. This is the only long-lived branch, and will persist from creation of the repository until it is decommissioned. Engineers will branch from `main` to implemnent a change, then a Pull Request process with appropriate approvals will control the merge of that change back to `main` as the next iteration of the data product.

## Always Up-To-Date

There are several supply chains providing dependencies for this repo. When development interactively (ignoring your machine), the relevant sources are:

- Python packages via PyPI
- dbt packages

Both of these sources are set by default to update automatically to the latest available versions. A VSCode task is included to automatically update your local environment, and the CI system will update to latest on each run.

I believe this setup minimises the vulnerability risk users of this template are exposed to by default.