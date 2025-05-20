

---

# Page 1: Helm Basics & Installation

## Installation Commands

```bash
# Using script (Linux/macOS)
curl https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 | bash

# Using Homebrew (macOS)
brew install helm

# Using Chocolatey (Windows)
choco install kubernetes-helm

# Using Scoop (Windows)
scoop install helm

# Verify installation
helm version
```

## Repository Management

```bash
# Add a repository
helm repo add [NAME] [URL]
helm repo add stable https://charts.helm.sh/stable

# Update repositories
helm repo update

# List repositories
helm repo list

# Show repository details
helm repo index

# Remove a repository
helm repo remove [NAME]
helm repo remove stable
```

## Basic Chart Operations

```bash
# Search for charts in repository
helm search repo [KEYWORD]
helm search repo nginx

# Search in Artifact Hub
helm search hub [KEYWORD]
helm search hub wordpress

# Show chart information
helm show chart [CHART]
helm show chart bitnami/nginx

# Show chart values
helm show values [CHART]
helm show values bitnami/nginx

# Show all chart information
helm show all [CHART]
helm show all bitnami/nginx
```

## Help Commands

```bash
# General help
helm help

# Command-specific help
helm [COMMAND] --help
helm install --help
```

---

