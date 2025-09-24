Install a Single Cluster Agent to monitor resources in all namespaces

1. Delete all the previously installed CustomResourceDefinition (CRDs) related to Splunk AppDynamics Agent by using these commands:
  kubectl get crds 
  kubectl delete crds <crd-names>

2. Add the chart repository to Helm:
  helm repo add appdynamics-cloud-helmcharts https://appdynamics.jfrog.io/artifactory/appdynamics-cloud-helmcharts/

3. Create a namespace for appdynamics in your cluster:
  kubectl create namespace appdynamics

4. Create a Helm values file, in the example called values-ca1.yaml. Update the controllerInfo properties with the credentials from your Controller. Update the clusterAgent properties to set the namespace and pods to monitor. See Configure the Cluster Agent for information about the available properties nsToMonitorRegex, nsToExcludeRegex and podFilter.

  values-ca-dev-saas-simple.yaml


5. Create a secret based on the Controller Access Key. 
  kubectl -n appdynamics create secret generic cluster-agent-secret --from-literal=controller-key='<access-key>' --from-literal=api-user=‘<username@account:password>’

6. Deploy the Cluster Agent to the appdynamics namespace:
  helm install -f ./values-ca-dev-saas-simple.yaml "<my-cluster-agent-helm-release>" appdynamics-cloud-helmcharts/cluster-agent --namespace=appdynamics


See Configuration Options for values.yaml for more information regarding the available options. Also, you can download a copy of values.yaml from the Helm Chart repository using this command:
  helm show values appdynamics-cloud-helmcharts/cluster-agent
  helm show values appdynamics-cloud-helmcharts/cluster-agent > values-defaults.yaml
  

Example to install a Single Cluster Agent to monitor resources in all namespaces,  enable Infraviz and NetViz: values-ca-dev-infraviz-saas-simple.yaml


Example to install a Single Cluster Agent with Java auto-instrumentation on dev namespace, enable Infraviz and NetViz: values-ca-dev-infraviz-autoinstrument-upgrade-saas-simple.yaml


Example to install a Single Cluster Agent with Java auto-instrumentation on dev & stage namespace, enable Infraviz and NetViz: values-ca-dev-infraviz-autoinstrument-upgrade-saas-simple.yaml
