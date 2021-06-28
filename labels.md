# Labels and Selectors

Labels are key=value pairs you can assign to pods and use to filter commands and limit certain setup in pod files.

```bash
# get all pods in the dev environment
k get pods --selector environment=dev
# get all objects in the prod environment
k get all --selector environment=prod
# get all pods in the dev environment in the frontend tier
k get pods --selector environment=dev,tier=frontend
```
