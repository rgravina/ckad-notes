# Namespaces

During the CKAD exam you will be required to work in namespaces to keep answers to questions isolated from each other. In a real kubernetes cluster, namespaces are a useful feature too.

To create a namespace, use `k create namespace` (abbreviated to `ns`). For example:

```bash
k create ns <namespace>
# e.g. k create ns ckad
```

You can list all the namespaces, including their status.

```bash
k get ns
```

Most commands accept a namespace to work on. For example:

```bash
k get pods --namespace=ckad
k get pods -n=ckad
k -n ckad get pods
```

Get commands also take a parameter for all namespaces.

```bash
k get pods --all-namespaces
```

## Exercises

Run each command below. Try to guess what will happen before you run each command.

```bash
k create ns ckad
k get ns
k get pods --namespace=ckad
k -n ckad get pods
k get pods --all-namespaces
k delete ns ckad
```
