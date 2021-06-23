# Security Contexts

By default, pods run as the root user. The `whoami` command will print the running user to the log.

```bash
k run helloworld --image=busybox --command --restart=Never -- sleep infinity
k exec helloworld busybox -- whoami
```

Pods and containers can have a user set. Containers will inherit the user of the pod if not overridden.

```bash
apiVersion: v1
kind: Pod
metadata:
  name: helloworld
spec:
  securityContext:
    runAsUser: 1000
  containers:
  -  image: busybox
     name: busybox
     command:
       - /bin/sh
       - -c
       - "while true ; do echo `whoami` ; sleep 5 ; done"
     securityContext:
      runAsUser: 1000
 ```

Capabilities normally only available to the `root` user can be assigned to regular users. To change the system time a user needs the  `SYS_TIME` capability. The following will not work using the definition above

```bash
k exec -it helloworld -- date -s '2000-01-01 00:00:00'
```

Now try again with this pod definition, and changing the system time will work.

```bash
k delete pod helloworld
k apply -f helloworld.yaml
```

> helloworld.yaml

```bash
apiVersion: v1
kind: Pod
metadata:
  name: helloworld
spec:
  containers:
  - name: busybox
    image: busybox
    command:
      - "/bin/sh"
    args:
      - "-c"
      - "sleep infinity"
    securityContext:
      capabilities:
        add: ["SYS_TIME"]
```
