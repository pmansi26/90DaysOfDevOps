# Task 1
## 1.Why was Kubernetes created? What problem does it solve that Docker alone cannot?
### Why was Kubernetes created?
- Around 2014–2015, Google faced challenges in managing large-scale applications.
- Applications were running on thousands of servers, and:
- Scaling was done manually
- Handling traffic spikes was difficult
- Failures required manual intervention
- To solve this, Google developed an internal tool called Borg.
- Borg automated:
  - Deployment
  - Scaling
  - Resource management
- Later, Google open-sourced these ideas, and with the help of Cloud Native Computing Foundation, it became Kubernetes.
### What Docker does
- Docker is used for:
- Packaging applications with dependencies
- Running applications in containers
- Ensuring consistency across environments

- Limitation:
Docker works well for running containers but cannot manage them at large scale.

### Problem Kubernetes solves (Why Docker alone is not enough)
- Kubernetes is a container orchestration tool that manages containers efficiently.
- Key Problems Solved:
  - Auto Scaling
    - Automatically increases/decreases containers based on traffic
  - Self-Healing
    - Restarts failed containers
    - Replaces unhealthy instances
  - Load Balancing
    - Distributes incoming traffic across containers
  - Automated Deployment
    - Supports rolling updates and rollbacks
  - Cluster Management
    - Manages containers across multiple servers (nodes)

## 2.Who created Kubernetes and what was it inspired by?
- Google created Kubernetes based on its experience with large-scale systems.
- It was later open-sourced and is maintained by the Cloud Native Computing Foundation.
- Kubernetes was inspired by Google’s internal systems:
  - Borg – for cluster management, scaling, and self-healing
  - Omega – for advanced scheduling and resource management
## 3.What does the name "Kubernetes" mean?
- The word Kubernetes comes from the Greek language.
- It means “Helmsman” or “Pilot”.
  - A helmsman is a person who steers and controls a ship.

# Task 2
## Kubernetes Architecture
![K8s__architecture](K8s_arch)
## What happens when you run kubectl apply -f pod.yaml? Trace the request through each component.
# 1. kubectl (Client)
- Reads the pod.yaml file
- Converts it into a REST API request (JSON)
- Sends request to Kubernetes API Server
# 2. API Server
- Entry point of Kubernetes
- Performs:
  - Authentication
  - Authorization
  - Validation
- Stores desired state in etcd
# 3. etcd
- Stores cluster data (desired state)
- Example: “Pod should be running”
# 4. Scheduler
- Kubernetes Scheduler selects a suitable Node
- Based on:
  - Resource availability (CPU, Memory)
  - Policies / constraints
# 5. Controller Manager
- Kubernetes Controller Manager ensures desired state = actual state
- If Pod is missing → triggers creation
# 6. Kubelet (Node Agent)
- Kubelet receives instructions
- Pulls image and creates Pod using container runtime
# 7. Container Runtime
- Runs the container inside the Pod (Docker / containerd)
# 8. Final State
- Pod is running on the assigned Node
- Status is continuously updated to API Server
## What happens if the API server goes down?
- Kubernetes API Server is the central control point
- Impact:
  - kubectl commands fail
  - No scheduling, scaling, or updates  
  - No self-healing
  - Existing Pods continue running (managed by Kubelet)
## What happens if a worker node goes down?
- Impact:
  - Pods running on that node become unavailable
  - Kubernetes API Server detects node failure (via heartbeats)
  - Pods are marked NotReady / Unknown
- Recovery:
  - Kubernetes Controller Manager recreates Pods on other healthy nodes
  - Kubernetes Scheduler assigns new nodes
# Task 6
## What is a kubeconfig? Where is it stored on your machine?
- A kubeconfig is a configuration file used by Kubernetes tools (like kubectl) to connect and interact with a Kubernetes cluster.
- It contains all the details needed to access a cluster:
  - Cluster information (API server address)
  - User credentials (authentication)
  - Context (which cluster + user to use)
- It is stored in :- ~/.kube/config
