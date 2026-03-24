# The four required fields of a Kubernetes manifest and what each does
## 1. apiVersion
- Defines the API version used to create the object
- Helps Kubernetes understand which schema to use
## 2. kind
- Specifies the type of Kubernetes resource
## 3. metadata
- Contains basic information about the resource
- Used for identification and organization
- Common fields:
  - name → Unique name of the resource
  - labels → Key-value pairs for grouping
## 4. spec
- Defines the desired state/configuration of the resource
- This is the most important section
- Includes:
  - Containers
  - Images
  - Ports
# nginx, busybox, and third pod manifests
## nginx-pod.yaml
``` bash
---
apiVersion: v1
kind: Pod
metadata:
  name: nginx-pod
  labels:
    app: nginx
    environment: prod
spec:
  containers:
    - name: nginx
      image: nginx:latest
      ports:
        - containerPort: 80
```
## busybox-pod.yaml
``` bash
apiVersion: v1
kind: Pod
metadata:
        name: busybox-pod
        labels:
                app: busybox
                environment: dev
spec:
     containers:
     - name: busybox
       image: busybox:latest
       command: ["sh", "-c", "echo Hello from BusyBox && sleep 3600"]
```
## apache-pod.yaml
``` bash
---
apiVersion: v1
kind: Pod
metadata:
  name: apache-pod
  labels:
    app: apache
    environment: test
    team: dev
spec:
  containers:
    - name: apache
      image: httpd:latest
      ports:
        - containerPort: 80
```
# Difference between imperative (kubectl run) and declarative (kubectl apply -f)
## Imperative Approach (kubectl run)
In the imperative approach, commands are directly executed to create or manage resources. The user specifies how Kubernetes should perform the action.
example
``` bash
kubectl run pod-name --image=image_name
```
## Declarative Approach (kubectl apply -f)
In the declarative approach, the desired state of the system is defined in a YAML file. Kubernetes ensures that the actual state matches the defined state.
# What happens when you delete a standalone Pod?
A standalone Pod is a Pod that is not managed by any controller (such as Deployment, ReplicaSet, or StatefulSet).
- Standalone Pods are temporary in nature
- If deleted, they are permanently gone
- There is no self-healing mechanism
