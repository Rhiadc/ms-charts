# ms-charts

Welcome to `ms-charts`, a repository dedicated to storing Helm charts. This repository leverages GitHub Pages and the Chart Releaser Action to maintain and serve charts.

## Overview

This repository serves as base and chart repository for services as APIs, CLIs, microservices and so on. Which can be used to efficiently deploy these services on a Kubernetes cluster.

## How It Works

We use GitHub Pages in conjunction with the Chart Releaser Action. When a chart is pushed to the `main` branch, the Chart Releaser Action automatically packages the chart and releases it to GitHub Pages.

## Usage

Add a chart from the repository as a chart dependency:
```yaml
#Chart.yaml
apiVersion: v2
name: my-service
type: application
version: 0.1.0
appVersion: "1.0.0"

dependencies:
- name: ms-base-chart
  version: "0.1.0"
  repository: "https://rhiadc.github.io/ms-charts/"
```

After creating the `Chart.yaml`, create your `values.yaml`. Then you could run:
```bash
helm dep up
```

## Testing
For testing purposes, you can generate the full yaml file based on the values and template you are using:
```bash
helm template . --values values.qa.yaml -o yaml test.yaml 
```
