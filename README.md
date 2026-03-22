# kube-airflow-deploy
**Project Overview**
kube-airflow-deploy is a centralized repository for managing multiple, independent Apache Airflow deployments using Helm. Each   deployment is encapsulated within its own directory, allowing for distinct configurations, environment-specific overrides, and easy lifecycle management across various clusters.

**Key Features**
Multi-Instance Support: Organized folder structure where each directory represents a unique Airflow deployment.

**Cloud-Agnostic Design**: Primary support for Google Kubernetes Engine (GKE) with the flexibility to deploy to any standard Kubernetes environment.

**Helm-Driven**: Leverages Helm charts for consistent, repeatable, and version-controlled infrastructure as code.

**Modular Configuration**: Easily manage individual instance settings (e.g., executor types, resource limits, and IAM roles) without affecting other deployments.
