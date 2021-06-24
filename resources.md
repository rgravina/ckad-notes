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
