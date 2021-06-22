# Configuration

## Environment Variables

Environment variables can be set and used in pods. For example, here's our Hello World example using an environment variable to store the message.

```bash
k run helloworld --image=busybox --env="MESSAGE=Hello, World" --restart=Never --dry-run -oyaml --command -- echo | tee helloworld.yaml
```

Now you can edit `helloworld.yaml` and add `$(MESSAGE)` as a command argument, then apply with `k apply -f helloworld.yaml`.

```yaml
apiVersion: v1
kind: Pod
metadata:
  creationTimestamp: null
  labels:
    run: helloworld
  name: helloworld
spec:
  containers:
  - command:
    - echo
    - $(MESSAGE)
    env:
    - name: MESSAGE
      value: Hello, World
    image: busybox
    name: helloworld
    resources: {}
  dnsPolicy: ClusterFirst
  restartPolicy: Never
status: {}
```

## Config Maps

Another way to do this is using config maps. Here we create a config map named `greeting` with the key `message` and the value "Hello, World".

```bash
k create cm greeting --from-literal="message=Hello, World"
```

For this kind of configuration we can use a yaml file. Add this to a file named `helloworld.yaml` then apply with `k apply -f helloworld.yaml`.

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: helloworld
spec:
  containers:
  - env:
    - name: MESSAGE
      valueFrom:
        configMapKeyRef:
          name: greeting 
          key: message
    image: busybox
    name: helloworld
    command:
    - echo
    - $(MESSAGE)
  dnsPolicy: ClusterFirst
  restartPolicy: Never
status: {}
```
