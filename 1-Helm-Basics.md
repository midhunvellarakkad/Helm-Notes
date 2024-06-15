

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

# Page 2: Chart Installation & Release Management

## Installing Charts

```bash
# Basic install with generated name
helm install [CHART]
helm install bitnami/nginx

# Install with specific release name
helm install [RELEASE_NAME] [CHART]
helm install my-nginx bitnami/nginx

# Install with custom values file
helm install [RELEASE_NAME] [CHART] -f [VALUES_FILE]
helm install my-nginx bitnami/nginx -f custom-values.yaml

# Install specific chart version
helm install [RELEASE_NAME] [CHART] --version [VERSION]
helm install my-nginx bitnami/nginx --version 9.5.0

# Install with overridden values
helm install [RELEASE_NAME] [CHART] --set key1=value1,key2=value2
helm install my-nginx bitnami/nginx --set service.type=NodePort,replicaCount=2

# Install in specific namespace
helm install [RELEASE_NAME] [CHART] --namespace [NAMESPACE]
helm install my-nginx bitnami/nginx --namespace web-apps

# Dry run (simulate installation)
helm install [RELEASE_NAME] [CHART] --dry-run
helm install my-nginx bitnami/nginx --dry-run --debug

# Wait for all resources to be ready
helm install [RELEASE_NAME] [CHART] --wait
helm install my-nginx bitnami/nginx --wait --timeout 5m
```

## Managing Releases

```bash
# List releases in current namespace
helm list
helm ls

# List releases in all namespaces
helm list --all-namespaces
helm ls -A

# List releases with a specific status
helm list --deployed
helm list --failed
helm list --pending
helm list --uninstalled

# Get release status
helm status [RELEASE_NAME]
helm status my-nginx

# Get release history
helm history [RELEASE_NAME]
helm history my-nginx

# Uninstall a release
helm uninstall [RELEASE_NAME]
helm uninstall my-nginx

# Uninstall without deleting release history
helm uninstall [RELEASE_NAME] --keep-history
helm uninstall my-nginx --keep-history
```

## Upgrading and Rollback

```bash
# Upgrade a release
helm upgrade [RELEASE_NAME] [CHART]
helm upgrade my-nginx bitnami/nginx

# Upgrade with values file
helm upgrade [RELEASE_NAME] [CHART] -f [VALUES_FILE]
helm upgrade my-nginx bitnami/nginx -f new-values.yaml

# Upgrade and install if not present
helm upgrade --install [RELEASE_NAME] [CHART]
helm upgrade --install my-nginx bitnami/nginx

# Rollback to previous release
helm rollback [RELEASE_NAME] [REVISION]
helm rollback my-nginx 1

# Force resource update through delete/recreate
helm upgrade [RELEASE_NAME] [CHART] --force
```

---

# Page 3: Chart Development & Management

## Creating Charts

```bash
# Create a new chart
helm create [CHART_NAME]
helm create my-app

# Package a chart
helm package [CHART_PATH]
helm package ./my-app

# Package with specific version
helm package [CHART_PATH] --version [VERSION]
helm package ./my-app --version 1.0.0

# Update chart dependencies
helm dependency update [CHART_PATH]
helm dependency update ./my-app

# List chart dependencies
helm dependency list [CHART_PATH]
helm dependency list ./my-app

# Build chart dependencies
helm dependency build [CHART_PATH]
```

## Chart Validation

```bash
# Lint a chart
helm lint [CHART_PATH]
helm lint ./my-app

# Validate chart installation
helm template [RELEASE_NAME] [CHART_PATH]
helm template my-release ./my-app

# Debug chart template rendering
helm template [RELEASE_NAME] [CHART_PATH] --debug
helm template my-release ./my-app --debug

# Check chart for best practices
helm lint [CHART_PATH]
helm lint ./my-app --strict
```

## Pull & Push Charts

```bash
# Pull a chart from a repository
helm pull [CHART] --untar
helm pull bitnami/nginx --untar

# Pull specific version
helm pull [CHART] --version [VERSION]
helm pull bitnami/nginx --version 9.5.0

# Save chart to local directory
helm pull [CHART] --destination [DIR]
helm pull bitnami/nginx --destination ./charts

# Push a chart to OCI registry (Helm v3.8.0+)
helm push [CHART_PACKAGE] oci://[REGISTRY]/[PROJECT]
helm push my-app-1.0.0.tgz oci://registry.example.com/helm-charts
```

## Chart Museum Interaction

```bash
# Push to Chart Museum (requires plugin)
helm cm-push [CHART_PATH] [REPO_NAME]
helm cm-push ./my-app my-repo

# Install Chart Museum plugin
helm plugin install https://github.com/chartmuseum/helm-push
```

---

# Page 4: Advanced Helm Features

## Using Templates and Values

```bash
# Render templates locally
helm template [RELEASE_NAME] [CHART]
helm template my-release ./my-app

# Render with custom values
helm template [RELEASE_NAME] [CHART] -f [VALUES_FILE]
helm template my-release ./my-app -f production-values.yaml

# Render specific template
helm template [RELEASE_NAME] [CHART] --show-only [TEMPLATE_PATH]
helm template my-release ./my-app --show-only templates/deployment.yaml

# Get computed values for a release
helm get values [RELEASE_NAME]
helm get values my-nginx

# Get all (including default) values for a release
helm get values [RELEASE_NAME] --all
helm get values my-nginx --all
```

## Working with Hooks

```bash
# View rendered hooks
helm get hooks [RELEASE_NAME]
helm get hooks my-nginx

# View manifest with hooks
helm get manifest [RELEASE_NAME]
helm get manifest my-nginx
```

## Secret Management

```bash
# Fetch decrypted secrets (requires helm-secrets plugin)
helm secrets dec [SECRET_FILE]

# Edit encrypted secrets
helm secrets edit [SECRET_FILE]

# Install with decrypted secrets
helm secrets install [RELEASE_NAME] [CHART] -f [ENCRYPTED_VALUES]
```

## Plugin Management

```bash
# Install a plugin
helm plugin install [URL]
helm plugin install https://github.com/databus23/helm-diff

# List installed plugins
helm plugin list

# Update plugins
helm plugin update [PLUGIN_NAME]

# Uninstall a plugin
helm plugin uninstall [PLUGIN_NAME]
```

## Testing

```bash
# Run chart tests
helm test [RELEASE_NAME]
helm test my-nginx

# Run with logs
helm test [RELEASE_NAME] --logs
```

---

# Page 5: Troubleshooting & Special Operations

## Troubleshooting Commands

```bash
# Debug installation
helm install [RELEASE_NAME] [CHART] --debug --dry-run
helm install my-nginx bitnami/nginx --debug --dry-run

# Get release manifest
helm get manifest [RELEASE_NAME]
helm get manifest my-nginx

# Get notes from a release
helm get notes [RELEASE_NAME]
helm get notes my-nginx

# Get all information about a release
helm get all [RELEASE_NAME]
helm get all my-nginx
```

## Environment Variables

```bash
# Set Helm home directory
export HELM_HOME=/path/to/helm/home

# Skip repository certificate verification
export HELM_SKIP_TLS_VERIFY=true

# Set custom cache directory
export HELM_CACHE_HOME=/path/to/cache

# Set custom config directory
export HELM_CONFIG_HOME=/path/to/config

# Set custom data directory
export HELM_DATA_HOME=/path/to/data

# Set repository username
export HELM_REPOSITORY_USERNAME=username

# Set repository password
export HELM_REPOSITORY_PASSWORD=password

# Set namespace for commands
export HELM_NAMESPACE=my-namespace
```

## Working with Registries

```bash
# Login to OCI registry (Helm v3.8.0+)
helm registry login [REGISTRY] --username [USERNAME] --password [PASSWORD]
helm registry login registry.example.com --username myuser --password mypass

# Logout from OCI registry
helm registry logout [REGISTRY]
helm registry logout registry.example.com
```

## Special Operations

```bash
# Convert Helm v2 release to v3
helm 3 2to3 convert [RELEASE_NAME]

# Clean up Helm v2 configuration
helm 3 2to3 cleanup

# Show differences between releases (requires helm-diff plugin)
helm diff revision [RELEASE_NAME] [REVISION1] [REVISION2]
helm diff revision my-nginx 1 2

# Show differences between current deployed release and what would be deployed
helm diff upgrade [RELEASE_NAME] [CHART]
helm diff upgrade my-nginx bitnami/nginx -f new-values.yaml

# Encrypt sensitive values (requires helm-secrets plugin)
helm secrets enc [VALUES_FILE]

# Generate auto-completion scripts
helm completion bash > ~/.helm-completion.bash
echo 'source ~/.helm-completion.bash' >> ~/.bashrc

# Perform kubeval validation (requires helm-kubeval plugin)
helm kubeval [CHART]
```
