# CI/CD Pipeline
## Getting Started
When committing to `master` branch, [Github Actions](https://github.com/features/actions) triggers the below workflow:

1. Setup 
    * Checkout the repository.
    * Make an artifact and upload it.
1. Lint & Test
    * Download the artifact.
    * Install [Python](https://www.python.org/).
    * Install the dependencies.
    * Lint with [flake8](https://github.com/PyCQA/flake8).
    * Test with [pytest](https://docs.pytest.org/en/7.1.x/).
1. Build & Deploy
    * Download the artifact.
    * Start [minikube](https://minikube.sigs.k8s.io/docs/).
    * Build [Docker](https://www.docker.com/) image.
    * Install [Helm](https://helm.sh/).
    * Lint helm chart.
    * Deploy helm chart.
    * Ensure the readiness of created pods.

## Architecture Overview
![Architecture diagram](https://i.imgur.com/9VoVdDv.png)

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

## References
1. [Events that trigger workflows](https://docs.github.com/en/actions/using-workflows/events-that-trigger-workflows)
1. [Setup minikube as CI step in GitHub Actions](https://minikube.sigs.k8s.io/docs/tutorials/setup_minikube_in_github_actions/)
1. [Application deployment with Helm and GitHub actions to Kubernetes cluster](http://www.inanzzz.com/index.php/post/879p/application-deployment-with-helm-and-github-actions-to-kubernetes-cluster)
