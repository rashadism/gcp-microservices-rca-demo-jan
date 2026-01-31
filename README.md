# GCP Microservices RCA Demo

Demo showcasing OpenChoreo observability alerts with AI root cause analysis.

Based on [openchoreo/samples/component-alerts](https://github.com/openchoreo/openchoreo/tree/main/samples/component-alerts).

## Prerequisites

- Kubernetes cluster with OpenChoreo(0.13) and observability plane installed ([Single cluster setup guide](https://openchoreo.dev/docs/getting-started/try-it-out/on-self-hosted-kubernetes/))
- RCA agent configured ([Configuration guide](https://openchoreo.dev/docs/operations/rca-agent/))
- `kubectl` configured

## Setup

### 1. Create the Project

```bash
kubectl apply -f gcp-microservice-demo-project.yaml
```

### 2. Install Notification Channel and Alert Trait

```bash
kubectl apply -f alert-notification-channels.yaml
kubectl apply -f alert-rule-trait.yaml
```

### 3. Deploy Components

```bash
kubectl apply -f components/
```

### 4. Apply Failure Scenarios

```bash
kubectl apply -f failure-scenario-setup.yaml
```

### 5. Trigger Alerts

```bash
./trigger-alerts.sh
```

You should get get 2/3 RCA reports generated under the project view.

## Cleanup

```bash
kubectl delete -f failure-scenario-setup.yaml
kubectl delete -f components/
kubectl delete -f alert-notification-channels.yaml
kubectl delete -f alert-rule-trait.yaml
kubectl delete -f gcp-microservice-demo-project.yaml
```
