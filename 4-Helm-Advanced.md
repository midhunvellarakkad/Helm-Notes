
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
