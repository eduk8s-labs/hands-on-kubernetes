Containers are a lightweight form of virtualization which can encapsulate one or more processes. Unlike virtual machines, containers do not include a running operating system. Instead, the underlying host system upon which the container runs provides the operating system. You can run as many containers on a host system as host resources will permit.

Kubernetes is a platform for deploying applications in containers across multiple host systems and managing them. Kubernetes will schedule applications (workloads) to the different hosts systems (nodes), based on what resources (CPU and memory) are available.

When you see discussion about deploying applications to a Kubernetes cluster, although applications are run in containers, you are more likely to hear mention of an application being deployed to a pod.

A pod in Kubernetes is an abstraction which represents a group of running containers, where the containers are to be managed and scaled as a unit. All containers in a pod will be scheduled to the same node.

In most cases a pod will consist of only a single container. There are use cases for running multiple containers in one pod, but they are generally the exception rather than the rule.

An instance of your application would therefore be run in one container of a pod.

If you need to scale up the number of instances of your application, you would run more than one pod for that application. The pods for an application would be distributed across the nodes in a Kubernetes cluster.

Scaling is not performed by adding more containers to the one pod.

In the rest of this workshop you will see how you can deploy an application in a pod in Kubernetes.
