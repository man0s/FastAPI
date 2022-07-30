# CI/CD Pipeline [![CI/CD Pipeline](https://github.com/man0s/FastAPI/actions/workflows/pipeline.yml/badge.svg)](https://github.com/man0s/FastAPI/actions/workflows/pipeline.yml)
## Table of Contents
- [Getting Started](#getting-started)
- [Architecture Overview](#architecture-overview)
- [Repository Structure](#repository-structure)
- [Improvements](#improvements)
- [References](#references)

## Getting Started
When committing to `master` branch, [Github Actions](https://github.com/features/actions) triggers the below workflow:

1. **Setup**
    * Checkout the repository.
    * Make an artifact and upload it.
1. **Lint & Test**
    * Download the artifact.
    * Install [Python](https://www.python.org/).
    * Install the dependencies.
    * Lint with [flake8](https://github.com/PyCQA/flake8).
    * Test with [pytest](https://docs.pytest.org/en/7.1.x/).
1. **Build & Deploy**
    * Download the artifact.
    * Start [minikube](https://minikube.sigs.k8s.io/docs/).
    * Build [Docker](https://www.docker.com/) image.
    * Install [Helm](https://helm.sh/).
    * Lint helm chart.
    * Deploy helm chart.
    * Ensure the readiness of created pods.
## Architecture Overview
![Architecture diagram](https://i.imgur.com/2rfzdrk.png)

## Repository Structure
    .
    ├── .github
    │   └── workflows
    |       └── pipeline.yaml   # Github Actions pipeline 
    ├── helm                    # Helm chart directory
    │   ├── templates
    │       ├── deployment.yaml
    │       └── service.yaml
    │   ├── .helmignore
    │   ├── Chart.yaml
    │   └── values.yaml
    ├── src                     # Source files
    ├── tests                   # Automated tests
    ├── Dockerfile
    ├── requirements.md
    └── README.md


## Improvements
There are a lot more things that we can add in the pipeline:
* Environmental variables and secrets that are interpolated on the runner machine that runs the workflow.
* Vulnerability scanning of the Docker image (e.g. snyk).
* Testing of the service endpoint after the Kubernetes deployment.
* Execute the pipeline in higher environments after success.

## References
1. [Events that trigger workflows](https://docs.github.com/en/actions/using-workflows/events-that-trigger-workflows)
1. [Setup minikube as CI step in GitHub Actions](https://minikube.sigs.k8s.io/docs/tutorials/setup_minikube_in_github_actions/)
1. [Application deployment with Helm and GitHub actions to Kubernetes cluster](http://www.inanzzz.com/index.php/post/879p/application-deployment-with-helm-and-github-actions-to-kubernetes-cluster)
