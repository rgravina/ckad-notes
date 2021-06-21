# Pods

A pod consists of one or more containers and is the simplest deployable unit in kubernetes.

## Pods that run commands

The `busybox` image is a simple executable that contains hundreds of common unix commands, like `echo`. This example will create a Pod with one container running `busybox`, output the text "Hello, World!" and then exit. Normally, kubernetes will try to restart containers that exit, so we need to specify that it should not.

```bash
k run helloworld --image=busybox --command --restart=Never -- echo "Hello, World!"
```

The output of `echo` will be in th logs for the pod.

```bash
k logs helloworld 
```

You can also confirm that the pod ran to completion using `describe`. You should be able to see that the `Status` of the pod is `Succeeded`.

```bash
k describe pod helloworld
```
