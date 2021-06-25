# Welcome

These notes will help you prepare for the Certified Kubernetes Application Developer (CKAD) certification. The certification broadly covers skills needed to develop applications that run on kubernetes. Administration is out of scope of this guide and the certification. For more information, see the [certification website](https://www.cncf.io/certification/ckad/).

* [Introduction and Setup](introduction.md)

## Getting Started

This section covers working with namespaces and pods in simple, single container configurations.

* [Namespaces](namespaces.md)
* [Pods](pods.md)

Now you have the basics covered, see how to configure the running environment, resources and user accounts for your pods.

* [Config Maps and Environment Variables](configuration.md)
* [Storing Secrets](secrets.md)
* [Running Security Contexts](security.md)
* [Resource Limits](resources.md)
* [Service Accounts](serviceaccounts.md)

Pods can be categorised and Kubernetes will assign them to nodes based on taints/tolerances or labels/selectors.

* [Taints and Tolerances](nodes.md)
* [Labels and Selectors](labels.md)

Pod health can be monitored by liveness and readiness probes, and by inspecting logs.

* [Liveness and Readiness Probes](probes.md)
* [Logs](logs.md)
* [Metrics](metrics.md)

Dealing with deployments.

* [Rolling Updates and Rollbacks](updates.md)

Scheduling tasks.

* [Scheduling Jobs](jobs.md)

Persistent volumes.

* [Persistent Volumes](volumes.md)

Services and networking.

* [Services and Networking](networking.md)

## References

[Kubernetes Documentation](https://kubernetes.io/docs/)

*The author can not guarantee the content is error free, up to date, or that you will pass the exam using this information. The content was prepared based on the freely available curriculum and official documentation and is intended to be used for educational purposes only.*
