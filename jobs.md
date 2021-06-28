# Jobs

Jobs can be created in `yaml`.

```yaml
apiVersion: batch/v1
kind: Job
metadata:
  name: busybox-echo-job
spec:
  backoffLimit: 5
  template:
    spec:
      containers:
      - name: busybox
        image: busybox
        command: ["/bin/sh",  "-c", "echo \"Hello, World\""]
      restartPolicy: Never
```

You can now see the output in logs.

```bash
k logs jobs/busybox-echo-job
```

## Completions and Parallelism

Jobs can be required to succeed some number of times and be run in parallel to speed things up.

```yaml
spec:
  completions: 5
  parallelism: 3
```

## Running jobs at a specific time or interval

For example, to run a job every morning at 8:30am.

```yaml
spec:
  schedule: "30 8 * * *"
```
