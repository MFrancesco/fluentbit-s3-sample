# fluentbit-s3-sample

### This repository contains the code explained in [this article](https://medium.com/@malerba.francesco.89/a-practical-guide-to-kubernetes-partitioned-log-storage-on-s3-with-fluent-bit-61eee83f4679?source=friends_link&sk=5e60a11acfc777d4ff9cca8398d8c4e2)

Is used to deploy a Fluent Bit chart to collect logs from your Kubernetes cluster and send
them to S3 using partitioned folder structure that consider the namespace and (for this case) 
the app name label extracted from the metadata but could be easily modified to consider other labels/needs.  

### How to use it
Feel free to use this repo as a template and edit it to fit your needs.

You probably wish to change the values in the `custom_script.lua` file to extract the labels you need from the kubernetes object, and then using them in the `rewrite_rule` 


Before installing the app just consider that you need to create a secret called `s3-auth` in the namespace 
you wish to install the chart to access your S3 bucket with the following keys `access_key` and `secret_key`


We got 2 files the [values.yaml](values.yaml) and the [argoproject.yaml](argoproject.yaml)

- [values.yaml](values.yaml) is the values file for the [Fluent Bit chart](https://github.com/fluent/helm-charts/tree/main/charts/fluent-bit)
- [argoproject.yaml](argoproject.yaml) is the ArgoCD application file in case you need to deploy it using ArgoCD
