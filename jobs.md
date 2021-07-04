# Jobs

To get started, look at the help for the command. Here we create yaml for a job that outputs the current time.

```bash
k create job -h # lists options
k create job showdate --image=busybox -- date $dr | tee showdate.yaml
```

You can also set the number of `completions` and `parallelism` of the job

```yaml
apiVersion: batch/v1
kind: Job
metadata:
  creationTimestamp: null
  name: showdate
spec:
  completions: 5 # log the date five times in five different pods
  parallelism: 2 # run up to two in parallel
  template:
    metadata:
      creationTimestamp: null
    spec:
      containers:
      - command:
        - date
        image: busybox
        name: showdate
        resources: {}
      restartPolicy: Never
status: {}
```

You can now see the output in logs.

```bash
k logs job/showdate # Should see the current date and time from one of the pods
k logs pod/showdate-qj2c6 # Alternatively, you can access the pod directly
k delete job/showdate # deletes jobs and pods
```

## Running jobs at a specific time or interval

The create cronjob help has a good example of running a job every minute that shows the date. 

```bash
k create cronjob -h
k create cronjob showdate --image=busybox --schedule="*/1 * * * *" $dr -- date | tee showdate-cron.yaml
k apply -f showdate-cron.yaml # get all pods and look at logs... see that the jobs are running
k delete cronjob.batch/showdate
```

The yaml for a cronjob contains a job in the `jobTemplate` section.

```yaml
apiVersion: batch/v1beta1
kind: CronJob
metadata:
  creationTimestamp: null
  name: showdate
spec:
  jobTemplate:
    metadata:
      creationTimestamp: null
      name: showdate
    spec:
      template:
        metadata:
          creationTimestamp: null
        spec:
          containers:
          - command:
            - date
            image: busybox
            name: showdate
            resources: {}
          restartPolicy: OnFailure
  schedule: '*/1 * * * *'
status: {}
```
