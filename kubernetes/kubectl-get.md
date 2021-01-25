# kubectl-get

Useful examples for `kubectl get` commands.

## Prerequisite

Start minikube:

```sh
minikube start
```

Create a sample deployment with multiple replicas:

```sh
kubectl create deployment hello-minikube \
    --image=k8s.gcr.io/echoserver:1.4 \
    --replicas=3
```

## Examples

Get all the pods of the current namespace:

```sh
> kubectl get pod
NAME                              READY   STATUS    RESTARTS   AGE
hello-minikube-6ddfcc9757-2psss   1/1     Running   0          62s
hello-minikube-6ddfcc9757-rqr9t   1/1     Running   0          62s
hello-minikube-6ddfcc9757-wbltv   1/1     Running   0          62s
```

Get all the pods of a given application `app=hello-minikube` using label selector
(`-l`):

```sh
> kubectl get pod -lapp=hello-minikube
NAME                              READY   STATUS    RESTARTS   AGE
hello-minikube-6ddfcc9757-2psss   1/1     Running   0          4m42s
hello-minikube-6ddfcc9757-rqr9t   1/1     Running   0          4m42s
hello-minikube-6ddfcc9757-wbltv   1/1     Running   0          4m42s
```

Get all pod names of app `hello-minikube`:

```sh
> kubectl get pod -lapp=hello-minikube -o custom-columns=":metadata.name" --no-headers
hello-minikube-6ddfcc9757-2psss
hello-minikube-6ddfcc9757-rqr9t
hello-minikube-6ddfcc9757-wbltv
```

Get one pod using the pod name:

```sh
> kubectl get pod hello-minikube-6ddfcc9757-2psss
NAME                              READY   STATUS    RESTARTS   AGE
hello-minikube-6ddfcc9757-2psss   1/1     Running   0          5m34s
```

Get one pod in JSON format:

```
> kubectl get pod hello-minikube-6ddfcc9757-2psss -o json
{
    "apiVersion": "v1",
    "kind": "Pod",
    "metadata": {
        "creationTimestamp": "2021-01-23T17:11:55Z",
        "generateName": "hello-minikube-6ddfcc9757-",
        "labels": {
            "app": "hello-minikube",
            "pod-template-hash": "6ddfcc9757"
        },
     ...
}
```

Get field "status > start time" of a given pod using JSON path:

```sh
> kubectl get pod hello-minikube-6ddfcc9757-2psss -o jsonpath="{.status.startTime}"
2021-01-23T17:11:55Z
```
