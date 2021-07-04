# Resources

The `resources` section can be used to specify memory limits. Your pod might be shutdown if it runs out of memory with the reason `OOMKilled`.

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: helloworld
spec:
  containers:
  - name: busybox
    image: busybox
    resources:
      limits:
        memory: "10Mi"
      requests:
        memory: "2Mi"
    command:
      - "/bin/sh"
    args:
      - "-c"
      - "sleep infinity"
```

Try running a deployment with many replicas with low cpu and memory requirements so you can see what happens in real time.

```bash
k create deployment bb --image=busybox --replicas=10 $dr | tee deployment.yaml
```

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  creationTimestamp: null
  labels:
    app: bb
  name: bb
spec:
  replicas: 10
  selector:
    matchLabels:
      app: bb
  strategy: {}
  template:
    metadata:
      creationTimestamp: null
      labels:
        app: bb
    spec:
      containers:
      - image: busybox
        name: busybox
        resources: # add this section
          requests:
            memory: "32Mi" # Just enough to run busybox
            cpu: "100m" # This is 0.1 of a CPU
          limits: # These are just double the requested amount, just in case
            memory: "64Mi"
            cpu: "200m"
status: {}
```

```bash
k apply -f deployment.yaml
k get pods # see the pods
k delete deployment bb
```
