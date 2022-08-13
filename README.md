# linux-conntrack

Pulled from Connection Tracking (conntrack): Design and Implementation Inside Linux Kernel
https://arthurchiao.art/blog/conntrack-design-and-implementation/#1-introduction

## Introduction

Connection tracking is the basis of many network services and applications. For example, Kubernetes Service, ServiceMesh sidecar, software layer 4 load balancer (L4LB) LVS/IPVS, Docker network, OpenvSwitch (OVS), OpenStack security group (host firewall), etc, all rely on it.
