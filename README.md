# Apex Cluster Manager
Coming soon :).

## Installation

1. Install kubectl `brew install kubectl`
1. Install helm `brew install helm`
1. Install kind `brew install kind`
1. Create a kind cluster

        curl -fsSL https://raw.githubusercontent.com/apexdesigner/apex-cluster-manager/main/kind/Cluster.yaml | kind create cluster --config -
1. Install Apex Cluster Manager

    Be sure to update the adminEmails value to your email address

        helm install apex-cluster-manager \
            https://raw.githubusercontent.com/apexdesigner/apex-cluster-manager/main/helm-charts/apex-cluster-manager-0.0.9.tgz \
            --create-namespace -n apex-cluster-manager \
            -f https://raw.githubusercontent.com/apexdesigner/apex-cluster-manager/main/kind/apex-cluster-manager.values.yaml \
            --set adminEmails=david.knapp@apexbpm.com
