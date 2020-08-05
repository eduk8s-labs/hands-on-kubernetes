By default a pod has a restart policy of `Always`. This means that if for some reason the application were to crash, or otherwise exit, the application container would be restarted automatically.

To see this process in action run the command:

```execute-1
kubectl get pods -w
```

This sets up a watch on the state of pods in the namespace.

In the other terminal now run:

```execute-2
kubectl exec blog -- kill 1
```

This command will result in the UNIX command ``kill 1`` being run inside of the container, causing the initial process run in the container being stopped, resulting in the container as a whole being shutdown.

You should see output from the watch similar to:

```
NAME   READY   STATUS      RESTARTS   AGE
blog   1/1     Running     0          15s
blog   0/1     Completed   0          20s
blog   1/1     Running     1          25s
```

This shows how the application container exited (completed), but that it was then replaced with the status for the pod returning to running.

Delete the deployment by running:

```execute-2
kubectl delete pod blog
```

The watch output will show the application as being terminated. It will not be restarted in this case as Kubernetes knows that we have deleted the deployment.

Interrupt the watch command to stop it:

```execute-1
<ctrl-c>
```

Although a pod ensures the application will keep running, it doesn't provide any assistance when it comes to scaling up an application to multiple instances. To do this, you would need to create a new pod by way of a separate pod resource definition, with a different name.

For this reason, rather than directly deploying applications using a `Pod` resource definition, it is better to use higher level abstractions such as a `Deployment` or `StatefulSet` resource.

Regardless of the method for deploying the application, each pod will have its own IP address. To be able to load balance inbound requests across all the pods running instances of the applications, you will need to also create a `Service` resource.
