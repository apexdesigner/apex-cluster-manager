# Apex Cluster Manager
Coming soon :).

## Installation

1. Install kubectl
1. Install helm
1. Install kind
1. Create a kind cluster
1. Install Apex Cluster Manager

        helm install apex-cluster-manager \
            https://raw.githubusercontent.com/apexdesigner/apex-cluster-manager/main/helm-charts/apex-cluster-manager-0.0.9.tgz \
            --create-namespace -n apex-cluster-manager apex-cluster-manager \
            -f https://raw.githubusercontent.com/apexdesigner/apex-cluster-manager/main/kind/apex-cluster-manager.values.yaml \
            --set adminEmails=david.knapp@apexbpm.com
