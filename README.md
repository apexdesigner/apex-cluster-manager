# Apex Cluster Manager

![Apex Cluster Manager Logo](/resources/ad-k8-logo-500.png)

Managing containerized applications in Kubernetes can feel overwhelming.
Apex Cluster Manager makes it easy to manage your containerized apps.

## Features

- Simple, intuitive user interface for managing applications
- Create and manage apps with simple to use templates
- See resource utilization at the app and namespace levels
- Stop and stop an app or all the apps in a namespace
- Create, view and delete namespaces

## Under the Covers

Apex Cluster Manager 
is built in the [Apex Designer low code platform](https://apexdesigner.io), 
packaged as a [docker image](https://hub.docker.com/r/apexbpm/apex-cluster-manager)
and runs inside your Kubernetes cluster. 
It manages apps with stanard Kubernetes tools:

- [kubectl](https://kubernetes.io/docs/reference/kubectl/kubectl/)
- [helm](https://helm.sh/)
- [Kubernetes API](https://kubernetes.io/docs/concepts/overview/kubernetes-api/)

## Installation

Here are the steps to install Apex Cluster Manager on your local machine. 
Steps 1-3 are for macOS. 
If you are on Windows or Linux, please see the corresponding instructions on the tool websites.

1. Install kubectl: `brew install kubectl`
1. Install helm: `brew install helm`
1. Install kind: `brew install kind`
1. Create a kind cluster

    By default, a kind cluster only exposes a single port.
    To make it easy to access apps running in your cluster, 
    you can expose additional ports on the kind cluster with a configuration file by running this command:

        curl -fsSL https://raw.githubusercontent.com/apexdesigner/apex-cluster-manager/main/kind/Cluster.yaml | kind create cluster --config -

1. Install Apex Cluster Manager

    Use helm to install Apex Cluster Manager. Be sure to replace **your.email** with your email address.

        helm install apex-cluster-manager \
            https://raw.githubusercontent.com/apexdesigner/apex-cluster-manager/main/helm-charts/apex-cluster-manager-0.0.17.tgz \
            --create-namespace -n apex-cluster-manager \
            -f https://raw.githubusercontent.com/apexdesigner/apex-cluster-manager/main/kind/apex-cluster-manager.values.yaml \
            --set environmentVariables.adminEmails=your.email
1. It will take a while to download the image and start the pod.
You can use this command to watch the status of the pod:
  
        kubectl get pods -n apex-cluster-manager
        
    When it looks like this, Apex Cluster Manager is ready to use:
    
        NAME                                    READY   STATUS    RESTARTS   AGE
        apex-cluster-manager-6685cf54f8-rs5g6   1/1     Running   0          3h38m

1. Access Apex Cluster Manager at http://localhost:30000

## Ideas and Feedback

Please feel free to open issues in this repository with any questions, ideas or feedback.
