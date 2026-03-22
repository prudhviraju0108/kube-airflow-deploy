# kube-airflow-deploy

Helm-based multi-instance Apache Airflow deployment management on Kubernetes.

## 📋 Table of Contents

- [Overview](#overview)
- [Key Features](#key-features)
- [Prerequisites](#prerequisites)
- [Quick Start](#quick-start)
- [Directory Structure](#directory-structure)
- [Configuration](#configuration)
- [Deployment](#deployment)
- [Contributing](#contributing)

## Overview

**kube-airflow-deploy** is a centralized repository for managing multiple, independent Apache Airflow deployments using Helm. Each deployment is encapsulated within its own directory, allowing for distinct configurations, environment-specific overrides, and easy lifecycle management across various Kubernetes clusters.

Whether you're deploying to Google Kubernetes Engine (GKE), Amazon EKS, or any other Kubernetes environment, this project provides a clean, modular approach to managing Airflow at scale.

## Key Features

- **🚀 Multi-Instance Support**: Organized folder structure where each directory represents a unique Airflow deployment
- **☁️ Cloud-Agnostic Design**: Primary support for Google Kubernetes Engine (GKE) with flexibility to deploy to any standard Kubernetes environment
- **📦 Helm-Driven**: Leverages Helm charts for consistent, repeatable, and version-controlled infrastructure as code
- **⚙️ Modular Configuration**: Easily manage individual instance settings (executor types, resource limits, IAM roles) without affecting other deployments
- **🔄 Environment Overrides**: Support for development, staging, and production configurations

## Prerequisites

Before you begin, ensure you have the following installed:

- Kubernetes 1.20+ cluster
- Helm 3.0+
- kubectl configured to access your cluster
- Git (for cloning the repository)

## Quick Start

1. Clone this repository:
```bash
git clone https://github.com/prudhviraju0108/kube-airflow-deploy.git
cd kube-airflow-deploy
```

2. Navigate to your desired Airflow instance:
```bash
cd airflow-instance-1
```

3. Install the Helm chart:
```bash
helm install airflow . -f values.yaml
```

## Directory Structure

```
kube-airflow-deploy/
├── airflow-instance-1/
│   ├── values.yaml
│   ├── values-dev.yaml
│   └── values-prod.yaml
├── airflow-instance-2/
│   ├── values.yaml
│   └── ...
└── README.md
```

Each instance directory contains:
- `values.yaml`: Default Helm values
- `values-{environment}.yaml`: Environment-specific overrides

## Configuration

Customize each Airflow deployment by modifying the appropriate `values.yaml` file:

```yaml
# Example: Configure executor type
executor: KubernetesExecutor

# Example: Set resource limits
resources:
  limits:
    cpu: 2
    memory: 4Gi
  requests:
    cpu: 1
    memory: 2Gi
```

Refer to the [Apache Airflow Helm Chart Documentation](https://airflow.apache.org/docs/helm-chart/stable/) for all available options.

## Deployment

### Deploy to specific environment:

```bash
# Deploy to development
helm install airflow . -f values.yaml -f values-dev.yaml

# Deploy to production
helm install airflow . -f values.yaml -f values-prod.yaml
```

### Update an existing deployment:

```bash
helm upgrade airflow . -f values.yaml -f values-prod.yaml
```

### View deployment status:

```bash
kubectl get pods -l app=airflow
helm status airflow
```

## Contributing

Contributions are welcome! Please feel free to submit a pull request with improvements or bug fixes.

---

**Last Updated**: 2026-03-22