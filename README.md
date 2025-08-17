# Kubernetes Deployment with Minikube

This project demonstrates how to deploy and access applications in a Kubernetes cluster running on **Minikube**.

---

## 🚀 Steps to Deploy

1. **Apply Kubernetes manifests**
   ```bash
   kubectl apply -f .
   ```
   This will apply all YAML files in the current directory.

2. **Check nodes**
   ```bash
   kubectl get nodes -o wide
   ```
   This displays the internal and external IPs of the nodes.

---

## 🌐 Accessing the Application

Since we are using **Minikube** with **Docker as the VM driver**, there are two main ways to access the services:

### 1. Using Node IP & NodePort
- Get the Minikube IP:
  ```bash
  minikube ip
  ```
- Combine it with the NodePort exposed in your Service definition:
  ```
  http://<minikube-ip>:<node-port>
  ```

### 2. Using `minikube tunnel`
- Run:
  ```bash
  minikube tunnel
  ```
- This will create a tunnel to simulate an external LoadBalancer.
- Once active, you can access the services via `127.0.0.1:<port>`.

---

## 🔎 Viewing Service URLs

To quickly see the URL for a service:
```bash
minikube service <service-name>
```
This will open the service in your default browser.

---

## 📌 Notes
- Use **ClusterIP** services for internal communication (e.g., `db`, `redis`).  
- Use **NodePort** or **LoadBalancer** for external access (e.g., `vote`, `result`).  
- The **worker** pod does not need a service since it only processes background jobs.
