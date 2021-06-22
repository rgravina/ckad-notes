# Secrets

Secrets can be used for storing SSH keys, access tokens, and other information you do not want easily accessible.

>*By default secrets are base64 encoded and easily decoded*. See the [Kubernetes documentation on secrets](https://kubernetes.io/docs/concepts/configuration/secret/) for more information on how to encrypt secrets at rest.

```bash
k create secret generic greeting --from-literal="MESSAGE=Hello, World"
k describe secret greeting
```

Add this to a file named `helloworld.yaml` then apply with `k apply -f helloworld.yaml`.

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: helloworld
spec:
  containers:
  - env:
    envFrom:
    - secretRef:
        name: greeting
    image: busybox
    name: helloworld
    command:
    - echo
    - $(MESSAGE)
  dnsPolicy: ClusterFirst
  restartPolicy: Never
status: {}
```
