# Services and Networking

## Cluster IP

Exposing a pod interally to other pods.

```bash
k run web --image=nginx $dr | tee pod.yaml
k apply -f pod.yaml # no changes nesscary
k expose pod -h # look at the examples
k expose pod web --port=3000 --target-port=80 $dr | tee service.yaml
k apply -f service.yaml # make nginx, which runs on port 80, available on port 3000
k describe service/web # check for endpoints
k run temp --restart=Never -i --rm --image=busybox -- wget -O- web:3000 # 'web' is the Kubernetes interal name for the node. Shows the nginx welcome page
k run temp --restart=Never -i --rm --image=busybox -- wget -O- 10.107.179.222:3000 # the value of Cluster-IP also works
```

## NodePort

Change the `service.yaml` example from above.

```yaml
apiVersion: v1
kind: Service
metadata:
  creationTimestamp: null
  labels:
    server: nginx
  name: web
spec:
  type: NodePort # add the type
  ports:
  - port: 3000
    protocol: TCP
    targetPort: 80
    nodePort: 30000 # Node ports start at 30000
  selector:
    server: nginx
status:
  loadBalancer: {}
```

```bash
k run temp --restart=Never -i --rm --image=busybox -- wget -O- 10.106.197.94:3000
```

## Network Policies

For example, prevent the web server from above from accessing external URLs.

```yaml
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: no-web
  namespace: default
spec:
  podSelector:
    matchLabels:
      server: nginx
  policyTypes:
  - Egress
```

```bash
k exec -it web -- curl https://kubernetes.io/ # TODO: It should be blocked
```
