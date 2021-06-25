# Liveness and Readiness Probes

You can specify liveness and readiness probes so Kubernetes can wait until a specified time before sending requests and has a way to determine if your app is running periodically.

## Readiness Probes

Used to determine when to put the pod in a Ready state.

```yaml
readinessProbe:
  httpGet:
    path: /ready
    port: 8080
```

## Liveness Probes

Used to determine if your app is still running.

```yaml
livenessProbe:
  httpGet:
    path: /health
    port: 8080
  initialDelaySeconds: 5
  periodSeconds: 10
  failureThreshold: 1
```
