
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
