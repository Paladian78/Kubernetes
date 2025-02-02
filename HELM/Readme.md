# Helm Readme

## Introduction

Helm is a package manager for Kubernetes that helps you manage Kubernetes applications. It uses a packaging format called charts.

## Basic Commands

### Install Helm

```sh
curl https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 | bash
```

### Create a New Chart

```sh
helm create mychart
```

### Install a Chart

```sh
helm install myrelease mychart
```

### List Releases

```sh
helm list
```

### Upgrade a Release

```sh
helm upgrade myrelease mychart
```

### Uninstall a Release

```sh
helm uninstall myrelease
```

### Debug a Release

```sh
helm install --debug --dry-run myrelease mychart
```

### Template a Chart

```sh
helm template mychart
```

## Directory Structure

When you create a new chart, Helm will generate a directory structure like this:

```
mychart/
    Chart.yaml          # Information about the chart
    values.yaml         # The default configuration values for this chart
    charts/             # Any dependencies for the chart
    templates/          # The Kubernetes manifest templates
    templates/tests/    # Test files for the chart
```

## Helm Release Details

A Helm release is a specific instance of a chart running in a Kubernetes cluster. Each release has a name and a version. You can manage releases using the Helm CLI.

### Viewing Release History

```sh
helm history myrelease
```

### Rollback a Release

```sh
helm rollback myrelease 1
```

### Get Release Status

```sh
helm status myrelease
```

### Get Release Manifest

```sh
helm get manifest myrelease
```

## Charts Directory

The `charts` directory within a Helm chart is used to manage dependencies. When you add dependencies to your chart, they are stored in this directory. Dependencies are other Helm charts that your chart relies on.

### Adding a Dependency

To add a dependency to your chart, you need to update the `Chart.yaml` file with the dependency information and then run the following command:

```sh
helm dependency update
```

### Example `Chart.yaml` with Dependencies

```yaml
apiVersion: v2
name: mychart
version: 0.1.0
dependencies:
    - name: nginx
        version: 1.2.3
        repository: https://example.com/charts
```

## Subcharts

Subcharts are Helm charts that are included as dependencies in a parent chart. They allow you to manage complex applications by breaking them down into smaller, reusable components.

### Using Subcharts

When you include a subchart as a dependency, Helm will automatically manage the installation and upgrade of the subchart along with the parent chart. You can override the values of a subchart by specifying them in the parent chart's `values.yaml` file.

### Example `values.yaml` with Subchart Overrides

```yaml
nginx:
  replicaCount: 2
  image:
    repository: nginx
    tag: stable
```

## Conclusion

Helm simplifies the process of deploying and managing Kubernetes applications. By using Helm, you can easily package, configure, and deploy applications and services onto your Kubernetes cluster.
