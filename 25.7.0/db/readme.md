Steps to deploy db-agent on k8s:

1. Create configMap for db-agent properties: "kubectl create -f dbagentProperties.configMap.yaml --save-config"
2. Create appd-agent-secret secret for account access-key: "kubectl create -f accessKey.secret.yaml --save-config"
3. Create appd-db-agent-log-config configMap for db-agent logs: "kubectl create -f logs.configmap.yaml --save-config"
4. Finally, create db-agent deployment: "kubectl create -f dbagent.deployment.yaml --save-config"

Steps to use db-agent parameter instead of secret for account access key:

1. Add property APPDYNAMICS_AGENT_ACCOUNT_ACCESS_KEY in appd-db-agent-properties configMap & don't encode it
2. Reapply appd-db-agent-properties configMap
3. Comment out spec.template.spec.containers.envFrom.secretRef section in dbagent.deployment.yaml
4. Reapply db-agent deployment: "kubectl apply -f dbagent.deployment.yaml"

Steps to change configMap - appd-db-agent-properties & appd-db-agent-log-config, & reflect the changes in deployment 

1. Change configMap yaml file
2. Apply configMap again: "kubectl apply -f <configmap-yaml>"
3. Rollout and restart db-agent deployment: "kubectl rollout restart deployment <deployment-name>"