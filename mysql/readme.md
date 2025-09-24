Steps to deploy MySQL 8.0 on k8s: 

1. mysql.yaml is a simple YAML for a MySQL deployment and service. In a real environment, you’d likely set up persistent storage, handle secrets for credentials, etc.
2. Create MySQL deployment and service:
  kubectl apply -f mysql.yaml
3. Check that the pod and service are running:
  kubectl get pods -n dev
  kubectl get svc -n dev
   
