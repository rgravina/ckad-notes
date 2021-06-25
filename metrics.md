# Metrics

You can see metrics like cpu and memory usage for nodes.

```bash
kubectl top node
kubectl top node --sort-by='cpu'
kubectl top node --sort-by='memory'
```

You can also see metrics of pods.

```bash
kubectl top pod
```
