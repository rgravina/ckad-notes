# Namespaces

During the CKAD exam you will be required to work in namespaces for certain questions.

To create a namespace, use `k create namespace` (abbreviated to `ns`). For example:

```bash
k create ns <namespace>
# e.g. k create ns development
```

You can list all the namespaces, including their status.

```bash
k get ns
```

Most commands accept a namespace to work on. For example:

```bash
k get pods --namespace=ckad-study
```

## Exercises

Run each command below. Try to guess what will happen before you run each command.

```bash
k create ns ckad-study
k get ns
k get pods --namespace=ckad-study
k get pods -n=ckad-study
k delete ns ckad-study
```
