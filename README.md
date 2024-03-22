# Deploy Uptime Kuma in Kubernetes

![Uptime-Kuma](/images/example.png)

## Build commands

To deploy `uptime-kuma` in kubernetes go to the folder from the cloned repo that has all of the `yaml` manifest files.

Run this command from that directory

``` shell
kubectl create -k .
```

![Create-CLI](/images/create.png)

Once completed you can check the status of everything with this command

``` shell
kubectl get pod,deployment,pvc,svc -n uptime-kuma
```

![Status-CLI](/images/status.png)

## Accessing the Frontend

From a web browser you can now access the `uptime-kuma` frontend page by going to the IP address of the node it is hosted on with the `nodePort` from the `service.yaml` file which is `30002` unless changed.

Example
``` shell
http://192.168.1.10:30002
```

## Deleting deployment of Librespeed

To remove run this command

``` shell
kubectl delete namespace uptime-kuma
```

## Monitoring the Docker Socket

The Docker Socket monitoring that `uptime-kuma` is capable of will not work in a Kubernetes environment.

With the introduction of the Container Runtime Interface (CRI) in Kubernetes, and Docker being deprecated in favor of runtimes
like containerd and CRI-O, direct access to the Docker socket may not recommended.
