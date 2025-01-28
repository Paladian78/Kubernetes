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

## Conclusion

Helm simplifies the process of deploying and managing Kubernetes applications. By using Helm, you can easily package, configure, and deploy applications and services onto your Kubernetes cluster.
