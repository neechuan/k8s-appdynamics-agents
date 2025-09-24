Author: <b>Gary Chew</b>

These repos show examples using AppDynamics agents to monitor Kubernetes node, cluster resources and its workloads.

<h2>AppDynamics Cluster Agent</h2>
The AppDynamics Cluster Agent is a lightweight monitoring agent designed specifically for Kubernetes and OpenShift clusters. It functions by collecting metrics, metadata, and events for the entire Kubernetes cluster, including all nodes, namespaces, and down to the container level. This enables organizations to monitor the health and performance of their Kubernetes infrastructure and understand how it impacts application and business performance.

<h3>Key Features</h3>
1. Cluster Health Monitoring: It provides an overview of cluster health, capacity, and current load through a cluster dashboard accessible in the AppDynamics UI.<br/>
Pod and Container Monitoring: The agent tracks pods in various states, container metrics, cluster events related to pods, and detailed pod information to help troubleshoot applications running in the cluster.<br/>
2. Support for Major Kubernetes Platforms: The Cluster Agent supports all major Kubernetes distributions, including Red Hat OpenShift, Amazon EKS, Azure AKS, and Rancher.<br/>
3. Auto-Instrumentation: For Kubernetes workloads running Java, .NET Core, and Node.js applications, the Cluster Agent supports auto-instrumentation, dynamically injecting application performance monitoring agents into application containers. This is the recommended deployment method for AppDynamics agents in Kubernetes environments.<br/>
4. Deployment Methods: The Cluster Agent can be installed using Kubernetes CLI (kubectl) or Helm charts, with the Cluster Agent Operator installed first, followed by the Cluster Agent itself.<br/>

Overall, the Cluster Agent provides comprehensive visibility into Kubernetes clusters, enabling proactive monitoring and troubleshooting of cloud-native applications deployed in containerized environments.

<h2>AppDynamics InfraViz Agent</h2>
1. The InfraViz Agent is part of the AppDynamics Infrastructure Visibility solution designed to monitor Kubernetes clusters.<br/>
2. It is deployed as a Kubernetes DaemonSet and works alongside the Cluster Agent to provide detailed visibility into the Kubernetes infrastructure.<br/>
3. The InfraViz Agent collects metrics and metadata from Kubernetes nodes, grouping them by roles such as master, worker, infra, and worker-infra.<br/>
4. It supports monitoring of container runtimes including Docker and containerd, with configurable flags to enable or disable Docker and containerd visibility.<br/>
5. The agent sends collected metrics to the AppDynamics Controller, where the cluster and node health can be visualized.<br/>
6. Configuration is managed via an infraviz.yaml file, where parameters such as account name, controller URL, cluster name, logging level, and resource limits can be set.<br/>
7. The agent supports enabling Server Visibility for master nodes, although this is limited on managed Kubernetes providers where the master plane is not accessible.<br/>
8. Network Visibility can be enabled by deploying a Network Agent as a sidecar container alongside the InfraViz Machine Agent.<br/>
9. The InfraViz Agent logs and status can be checked using Kubernetes CLI commands to ensure successful deployment and operation.<br/>

<h3>Key Features</h3>
1. Provides detailed node-level visibility within Kubernetes clusters.<br/>
2. Supports grouping and visualization of nodes by their roles.<br/>
3. Enables monitoring of container runtimes (Docker and containerd).<br/>
4. Integrates with AppDynamics Controller for centralized monitoring.<br/>
5. Supports configuration of logging verbosity and resource allocation.<br/>
6. Allows enabling or disabling of Server Visibility and Docker Visibility features.<br/>
7. Supports deployment with Kubernetes Cluster Agent Operator or standalone DaemonSet YAML.<br/>

This agent is essential for gaining comprehensive insights into Kubernetes cluster health, resource utilization, and network activity, helping to diagnose issues such as pod failures, node resource starvation, and network connectivity problems within the cluster.
