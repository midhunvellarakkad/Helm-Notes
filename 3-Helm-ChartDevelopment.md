
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
