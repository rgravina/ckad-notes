# Namespaces

During the CKAD exam you will be required to work in namespaces to keep answers to questions isolated from each other. In a real kubernetes cluster, namespaces are a useful feature too.

To create a namespace, use `k create namespace` (abbreviated to `ns`). For example:

```bash
k create ns ckad
k get ns # lists all namespaces
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

## Contexts

It's possible to set a namespace in context and switch to it so you don't have to pass the namespace to every command.

```bash
k config set-context ckad --namespace=ckad --user=minikube --cluster=minikube
k config use-context ckad # to switch contexts
k config use-context minikube # to return to the default
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
