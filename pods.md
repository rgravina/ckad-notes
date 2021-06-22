# Pods

A pod consists of one or more containers and is the simplest deployable unit in kubernetes. For this section we'll focus on single container pods.

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

## Running a shell on a pod

Let's run the `busybox` pod again, this time preventing it from exiting by running `sleep infinity`.

```bash
k run helloworld --image=busybox --command --restart=Never -- sleep infinity
```

Using `get` we can see that the status is `Running`.

```bash
k get pod helloworld
```

Next, we can shell into the container and print "Hello, World!" ourselves.

```bash
k exec helloworld -it busybox -- /bin/sh
echo "Hello, World!"
```

> Why is running `/bin/sh` necessary? What happens if you leave that out and instead run `k exec helloworld -it busybox`.
>
> Do you see "Hello, World!" in the logs? Why or why not?
