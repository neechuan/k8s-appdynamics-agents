Steps to install Cluster Agent:

1. Install Metrics Server:
  kubectl apply -f https://github.com/kubernetes-sigs/metrics-server/releases/latest/download/components.yaml

2. Create appdynamics namespace:
  kubectl create namespace appdynamics

4. Install the Cluster Agent Operator:
  kubectl create -f cluster-agent-operator.yaml

  Verify if the operator (deployment.apps/appdynamics-operator, pod/appdynamics-operator-*) is running:
  kubectl get all -n appdynamics
  
5. Based on the Account Access Key for the Controller, create the Controller Access Key Secret that the Cluster Agent reports to:
  kubectl -n appdynamics create secret generic cluster-agent-secret --from-literal=controller-key=<access-key>
  
6. Install Cluster Agent deployment and service:
  kubectl create -f cluster-agent.yaml

  Verify if the Cluster Agent is running:
  kubectl get all -n appdynamics


Austoscale example:
cluster-agent-autoscale.yaml   

Replicas example:
cluster-agent-replicas.yaml
