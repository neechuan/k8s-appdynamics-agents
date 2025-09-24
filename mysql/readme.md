Steps to deploy MySQL 8.0 on k8s: 

1. mysql.yaml is a simple YAML for a MySQL deployment and service. In a real environment, you’d likely set up persistent storage, handle secrets for credentials, etc.
2. Create MySQL deployment and service:
  kubectl apply -f mysql.yaml
3. Check that the pod and service are running:
  kubectl get pods -n dev
  kubectl get svc -n dev
   
Steps to deploy DB Agent on K8s:
1. Create a secret to keep the APPDYNAMICS_AGENT_ACCOUNT_ACCESS_KEY for DB Agent:
  kubectl apply -f accessKey.secret.yaml
2. Create a Service Account:
  kubectl create serviceaccount appd-db-agent -n appdynamics
3. appd-db-agent.yaml is a simple YAML for a DB Agent deployment and service. It uses the parameteres kept in dbagentProperties.configMap.yaml, references the secret for the access key and uses the appd-db-agent-sa service account we just created.
4. Deploy the AppDynamics Database Agent:
   kubectl apply -f dbagent.deployment.yaml
5. Check pod logs:
  kubectl get pods -n appdynamics
  kubectl logs deployment/appd-database-agent  -n appdynamics
  
 
