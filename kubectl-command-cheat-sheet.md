
# ☸️ Kubernetes (kubectl) Command Cheat Sheet

A handy reference guide to manage and debug your Kubernetes workloads efficiently using `kubectl`.

---

## 1️⃣ Cluster & Context Management

```bash
kubectl version                              # Show client & server versions
kubectl cluster-info                         # Display cluster details
kubectl config get-contexts                  # List all contexts
kubectl config use-context <context>         # Switch current context
kubectl config view                          # View full kubeconfig settings
kubectl config set-context ...               # Modify specific context
kubectl get componentstatuses                # Health of core components
````

---

## 2️⃣ Listing & Inspecting Resources

```bash
kubectl get pods                             # List pods
kubectl get svc                              # List services
kubectl get deployments                      # List deployments
kubectl get all                              # List all resources in current namespace
kubectl get ns                               # List namespaces
kubectl describe pod <pod>                   # Detailed pod info
kubectl describe svc <svc>                   # Detailed service info
kubectl explain <resource>[,<field>]         # Get resource schema
kubectl api-resources                        # List all supported resource types
kubectl api-versions                         # List available API versions
```

---

## 3️⃣ Create / Update / Delete Resources

```bash
kubectl apply -f file.yaml                   # Create/update from manifest
kubectl create -f file.yaml                  # Create resource from file
kubectl replace -f file.yaml                 # Replace existing resource
kubectl delete -f file.yaml                  # Delete from manifest
kubectl delete pod <pod>                     # Delete a specific pod
kubectl delete svc <svc>                     # Delete a service
kubectl edit deployment <deployment>         # Edit a deployment live
kubectl patch deployment <dep> -p '{...}'    # Patch a deployment (JSON merge)
```

---

## 4️⃣ Rollouts, Scaling & Updates

```bash
kubectl rollout status deploy/<dep>          # Monitor rollout status
kubectl rollout history deploy/<dep>         # View rollout history
kubectl rollout undo deploy/<dep>            # Rollback to previous version
kubectl scale deploy/<dep> --replicas=N      # Scale deployment
kubectl set image deploy/<dep> CNT=IMAGE     # Update container image
kubectl autoscale deploy <dep> --min=2 --max=5 --cpu-percent=80  # HPA
```

---

## 5️⃣ Debugging, Logs & Port Forwarding

```bash
kubectl logs <pod>                           # View logs of a pod
kubectl logs <pod> -c <container> --follow   # Stream logs from a container
kubectl exec -it <pod> -- /bin/sh            # Shell into running container
kubectl port-forward svc/<svc> 8080:80       # Forward local 8080 to svc port 80
kubectl cp file.txt <pod>:/path              # Copy file to pod
kubectl get events --sort-by=.metadata.creationTimestamp  # Events log
```

---

## 6️⃣ Monitoring Cluster Resources

```bash
kubectl top nodes                            # CPU/memory usage per node
kubectl top pods                             # CPU/memory usage per pod
kubectl get hpa                              # View Horizontal Pod Autoscalers
```

---

## 7️⃣ Node & Resource Management

```bash
kubectl cordon <node>                        # Mark node unschedulable
kubectl uncordon <node>                      # Re-enable scheduling on node
kubectl drain <node> --ignore-daemonsets     # Safely evict pods from node
kubectl taint nodes <node> key=value:NoSchedule  # Add taint to node
kubectl label pod <pod> env=prod             # Add label to pod
kubectl annotate svc <svc> key=value         # Add annotation to service
kubectl auth can-i <verb> <resource>         # Check RBAC permissions
kubectl auth can-i create pods --as=system:serviceaccount:default:my-sa  # Specific check
```

---

## 🔄 Bonus: Namespace Management

```bash
kubectl get namespaces                       # List all namespaces
kubectl create namespace dev                 # Create a new namespace
kubectl delete namespace dev                 # Delete a namespace
kubectl config set-context --current --namespace=dev  # Set default ns
```

---

