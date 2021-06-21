# Running Kubernetes

You can install [minikube](https://minikube.sigs.k8s.io/docs/) on macOS, Linux and Windows to run a simple kubernetes environment on your computer. Refer to the Minikube documentation for full installation instructions. For macOS, assuming you are using Homebrew you can install and run minikube.

```bash
brew install minikube
minikube start
```

## Useful Shortcuts

The CKAD exam is short, so remembering and setting up a few useful shortcuts is recommended.

Create an alias for `kubectl` to make it easier to type.

```bash
alias k=kubectl
```

It is convenient to run commands in dry run mode and output the results in `yaml`. An environment variable can help.

```bash
export DR="--dry-run=client -oyaml"
```
