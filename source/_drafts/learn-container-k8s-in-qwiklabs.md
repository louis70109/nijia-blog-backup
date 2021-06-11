---
title: 【標題】題目
categories: 學習紀錄
tags:
---

<style>
  section.compact {
    font-size: 150%  
  }
  img[alt~="center"] {
    display: block;
    margin: 0 auto;
  }
</style>

![](https://nijialin.com/images/2021/)

# 前言

<!-- more -->

# 介紹

# 結論

## [Pods](https://kubernetes.io/docs/concepts/workloads/pods/)

![](https://cdn.qwiklabs.com/tzvM5wFnfARnONAXX96nz8OgqOa1ihx6kCk%2BelMakfw%3D)
Pods also have [Volumes](https://kubernetes.io/docs/concepts/storage/volumes/). Volumes are data disks that live as long as the pods live, and can be used by the containers in that pod. Pods provide a shared namespace for their contents which means that the two containers inside of our example pod can communicate with each other, and they also share the attached volumes.

Pods also share a network namespace. This means that there is one IP Address per pod.

## Services

Pods aren't meant to be persistent. They can be stopped or started for many reasons - like failed liveness or readiness checks - and this leads to a problem:

What happens if you want to communicate with a set of Pods? When they get restarted they might have a different IP address.

That's where [Services](https://kubernetes.io/docs/concepts/services-networking/service/) come in. Services provide stable endpoints for Pods.
![](https://cdn.qwiklabs.com/Jg0T%2F326ASwqeD1vAUPBWH5w1D%2F0oZn6z5mQ5MubwL8%3D)

Services use labels to determine what Pods they operate on. If Pods have the correct labels, they are automatically picked up and exposed by our services.

Service 透過 label 來判斷哪個 pods 是他的，若是他的即會把 pods expose 出去

如果你要訪問當前 Services，可使用以下三個支援類型：

ClusterIP (internal) -- the default type means that this Service is only visible inside of the cluster,
NodePort gives each node in the cluster an externally accessible IP and
LoadBalancer adds a load balancer from the cloud provider which forwards traffic from the service to Nodes within it.
