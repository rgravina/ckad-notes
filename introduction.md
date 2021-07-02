# Running Kubernetes

[minikube](https://minikube.sigs.k8s.io/docs/) is a simple Kubernetes cluster that you can run on macOS, Linux and Windows and is perfect for development and learning. For macOS homebrew users, you can install it and run like this.

```bash
brew install minikube
minikube start
minikube dashboard # web based dashboard
```

## Terminal Shortcuts

The CKAD exam is short, so remembering and setting up a few useful shortcuts is recommended.

Create an alias for `kubectl` to make it easier to type.

```bash
alias k=kubectl
```

It is convenient to run commands in dry run mode and output the results in `yaml`. An environment variable can help.

```bash
export dr="--dry-run=client -oyaml" # for bash (probably what you will use in the CKAD exam)
export dr=(--dry-run=client -oyaml) # for zsh (macos default shell)
k run --image=busybox $dr # will print the yaml config for a pod, but not create it
```
