

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
