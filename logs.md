# Logs

You can see the logs of a pod. When there is more than one container in the pod, you also need to specify it.

```bash
k logs pod helloworld # if single container
k logs pod helloworld busybox  # if multiple containers
```
