# Services and Networking

Kubernetes creates a `kubernetes` service at launch.

```bash
k get service
```

## NodePort

The `NodePort` type can be used to expose a node port.

```yaml
apiVersion: v1
kind: Service
metadata:
  name: helloworld-service
spec:
  type: NodePort
  selector:
    name: helloworld
  ports:
    - port: 80
      targetPort: 8080
```

## Networking

You can list network policies.

```bash
k get networkpolicy
```
