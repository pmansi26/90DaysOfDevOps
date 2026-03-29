# 1.What problem Services solve and how they relate to Pods and Deployments
## What problem do Services solve?

Pods have dynamic IPs and can restart anytime, so their addresses are not reliable.
A Service provides a stable IP and DNS name to access them.

## Relation with Pods and Deployments
- Deployment → creates and manages Pods
- Service → uses labels to find those Pods and send traffic
  
Flow

User → Service → Pods (from Deployment)

# 2.Your three Service manifests with an explanation of each type
## 1. ClusterIP Service
```
apiVersion: v1
kind: Service
metadata:
  name: web-app-clusterip
spec:
  type: ClusterIP
  selector:
    app: web-app
  ports:
  - port: 80
    targetPort: 80
```
### Explanation
- Type: ClusterIP (default type)
- Exposes the application only inside the Kubernetes cluster
- Cannot be accessed from outside
- Other Pods use this Service to communicate with the application
- Use Case
  - Used for internal communication between microservices

## 2. NodePort Service
``` 
apiVersion: v1
kind: Service
metadata:
  name: web-app-nodeport
spec:
  type: NodePort
  selector:
    app: web-app
  ports:
  - port: 80
    targetPort: 80
    nodePort: 30080
```
### Explanation
- Exposes the application on a port of each Node (30080)
- Can be accessed using:
  ``` 
  http://<Node-IP>:30080
  ```
- Internally forwards traffic:
  ```
  NodePort → Service → Pod
  ```
- Use Case
    - Used to access applications externally without a cloud load balancer
## 3. LoadBalancer Service
```
apiVersion: v1
kind: Service
metadata:
  name: web-app-loadbalancer
spec:
  type: LoadBalancer
  selector:
    app: web-app
  ports:
  - port: 80
    targetPort: 80
```
### Explanation
- Exposes the application using a cloud provider’s load balancer
- Automatically assigns an external IP
- Distributes traffic across multiple Pods
- Use Case
  - Used in cloud environments for public access to applications
# 3.Difference between ClusterIP, NodePort, and LoadBalancer

| Feature        | ClusterIP                     | NodePort                              | LoadBalancer                          |
|----------------|------------------------------|----------------------------------------|----------------------------------------|
| Access         | Inside cluster only          | Outside via Node IP + Port             | Outside via External IP                |
| Exposure       | Internal                     | External (basic)                       | External (advanced)                    |
| Port           | Service port only            | Service port + NodePort                | Service port + NodePort + External IP  |
| Use Case       | Pod-to-Pod communication     | Testing / simple external access       | Production / public applications       |
| Cloud Needed   | No                           | No                                     | Yes                                    |
| Example Access | http://service-name:80       | http://NodeIP:30080                    | http://External-IP:80                  |

# 4.How Kubernetes DNS works for Service Discovery
## 1. Basic Idea

Kubernetes DNS allows Pods to communicate with Services using names instead of IP addresses.

## 2. How it works
- Kubernetes runs a DNS service called CoreDNS inside the cluster
- When a Service is created, DNS automatically creates an entry for it
- Each Service gets a DNS name mapped to its ClusterIP

## 3. Service DNS format
```
<service-name>.<namespace>.svc.cluster.local
```
Example:
```
web-app.default.svc.cluster.local
```
We can also use a short name inside the same namespace:
```
web-app
```

## 4. Request flow
```
Pod → DNS Query → CoreDNS → Service IP → Pod
```
# 5.What Endpoints are and how to inspect them

Endpoints are the actual Pod IP addresses behind a Service.
They tell the Service where to send traffic.

How to check Endpoints
```
kubectl get endpoints
kubectl describe endpoints <service-name>
```
# Screenshot of your services and the test output
