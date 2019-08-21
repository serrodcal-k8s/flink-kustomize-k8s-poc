# Proof of Concept for installing Apache Flink on K8s using Kustomize

[Here](https://medium.com/@serrodcal/usando-kustomize-para-instalar-apache-flink-en-kubernetes-9eb59a27b164) you have the link to a medium post where this example is explained (in Spanish).

## Prerequisites

* Kubernetes local cluster
* [Kustomize](https://kustomize.io/)

## Usage

First, select which overlay you want to apply: `local|test|production` and follow above instruction:

```bash
$ kustomize build overlays/production | kubectl apply -f -
```

**Note**: check your final YAML definition removing `| kubectl apply -f -` from last command.

## Check

Check the instalation by number of replicas, for example, in production the number of replicas for _taskmanager_ is 4:

```bash
$ kubectl get pods
NAME                                 READY   STATUS    RESTARTS
flink-jobmanager-79d94d4dc9-67g84    1/1     Running   0          
flink-taskmanager-78984c8bc4-zc8h5   1/1     Running   0          
flink-taskmanager-78984c8bc4-twp9p   1/1     Running   0
flink-taskmanager-78984c8bc4-jzf2x   1/1     Running   0          
flink-taskmanager-78984c8bc4-lbhrw   1/1     Running   0
```

## Kustomize in a nutshell

[This](https://speakerdeck.com/spesnova/introduction-to-kustomize) presentation is a good point to start understanding Kustomize.
