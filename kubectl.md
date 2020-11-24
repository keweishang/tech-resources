# kubectl

## Get

Find pods of the current k8s cluster and namespace:

```sh
kubectl get pod
```

Find pods of the target namespace `my-namespace`:

```
kubectl -n my-namespace get pod
```

Find pods of my service (`my-service`) using selector:

```sh
kubectl get pod -l service=my-service
```

## Execute

Execute a bash command on a pod `my-pod`, e.g. `curl`:

```sh
kubectl exec my-pod -- curl -s localhost:9200
```

Connect to a pod using bash shell:

```sh
kubectl exec -it my-pod -- bash
```
```sh
kubectl exec -it my-pod bash
```
