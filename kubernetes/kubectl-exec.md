# kubectl-exec

## Simple Execution

Perform an HTTP request using `curl`:

```sh
kubectl exec my-pod -- curl -s localhost:9200
```

## Connect To Pod

Connect to a pod using bash shell:

```sh
kubectl exec -it my-pod -- bash
```

## Multiple Commands

Find the JVM system properties for Elasticsearch using `jcmd` and the process ID:

```sh
#
# > jps
# 19170 Jps
# 1 Elasticsearch
#
kubectl exec my-pod -- bash -c 'jcmd $(jps | grep Elasticsearch | cut -d " " -f 1) VM.system_properties'
```
