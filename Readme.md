# Welcome

These notes will help you prepare for the Certified Kubernetes Application Developer (CKAD) certification. The certification broadly covers skills needed to develop applications that run on kubernetes. Administration is out of scope of this guide and the certification. For more information, see the [certification website](https://www.cncf.io/certification/ckad/).

* Read the [introduction and setup](introduction.md) section so you can get a local Kubernetes environment running.

## Tutorial

First, it helps to go over the main areas the certification covers before trying questions that combine several topics. Some examples use the `k` alias and `$dr` environment variable shortcut. See the [introduction](introduction.md) for instructions on setting this up.

This first section covers working with namespaces and pods in simple, single container configurations.

* [Working with Namespaces](namespaces.md)
* [Creating and Using Pods](pods.md)

Now you have the pod basics covered, see how to configure the running environment, resources and user accounts for your pods.

* [Config Maps and Environment Variables](configuration.md)
* [Storing and Using Secrets](secrets.md)
* [Running Security Contexts](security.md)
* [Setting Resource Limits](resources.md)
* [Service Accounts](service-accounts.md)

Pods can be categorised and Kubernetes will assign them to nodes based on taints/tolerations or labels/selectors.

* [Using Taints and Tolerations to control where pods run](nodes.md)
* [Usiung Labels and Selectors](labels.md)

Pod health can be monitored by liveness and readiness probes, and by inspecting logs.

* [Liveness and Readiness Probes](probes.md)
* [Logs](logs.md)
* [Metrics](metrics.md)

Kubernetes can handle zero downtime deployments and allows you to rollback deployments.

* [Rolling Updates and Rollbacks](updates.md)

Schedule one off or repeating tasks with jobs.

* [Running and Scheduling Jobs](jobs.md)

Store data on persistent volumes.

* [Persistent Volumes](volumes.md)

Services and networking.

* [Services and Networking](networking.md)

## Practice Questions

Try to get practice with questions that combine several topics and tasks to complete a goal, and troubleshooting questions. These resources may be helpful.

## Free Resources

* These [CKAD Exercises](https://github.com/dgkanatsios/CKAD-exercises) and these [CKAD Exercises](https://github.com/bmuschko/ckad-prep/) are arranged by exam topic and can be followed locally using `minikube`.
* The [Kube Academy CKAD Practice Course](https://kube.academy/courses/ckad-practice) can be completed in the browser.

## Paid Resources

* Since June 2021, the Linux Foundation has been offering two free [Killer.sh CKAD exam simulator](https://killer.sh/ckad) sessions with an exam booking. Alternative they can be purchased separately. These questions are similar to the harder questions on the exam and are excellent practice.
* The [KodeKloud CKAD Course and Labs](https://beta.kodekloud.com/). Requires purchase of the KodeKloud course or the associated Udemy course.

## References

* The [Kubernetes Documentation](https://kubernetes.io/docs/) is the one of the few resources you can refer to during the exam. It's great for preparation too. There are some [interactive tutorials](https://kubernetes.io/docs/tutorials/) which may help with getting practice.

*The author can not guarantee the content is error free, up to date, or that you will pass the exam using this information. The content was prepared based on the freely available curriculum and official documentation and is intended to be used for educational purposes only.*
