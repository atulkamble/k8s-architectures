<div align="center">
<h1>🚀 MyApp</h1>
<p><strong>Built with ❤️ by <a href="https://github.com/atulkamble">Atul Kamble</a></strong></p>

<p>
<a href="https://codespaces.new/atulkamble/template.git">
<img src="https://github.com/codespaces/badge.svg" alt="Open in GitHub Codespaces" />
</a>
<a href="https://vscode.dev/github/atulkamble/template">
<img src="https://img.shields.io/badge/Open%20with-VS%20Code-007ACC?logo=visualstudiocode&style=for-the-badge" alt="Open with VS Code" />
</a>
<a href="https://vscode.dev/redirect?url=vscode://ms-vscode-remote.remote-containers/cloneInVolume?url=https://github.com/atulkamble/template">
<img src="https://img.shields.io/badge/Dev%20Containers-Ready-blue?logo=docker&style=for-the-badge" />
</a>
<a href="https://desktop.github.com/">
<img src="https://img.shields.io/badge/GitHub-Desktop-6f42c1?logo=github&style=for-the-badge" />
</a>
</p>

<p>
<a href="https://github.com/atulkamble">
<img src="https://img.shields.io/badge/GitHub-atulkamble-181717?logo=github&style=flat-square" />
</a>
<a href="https://www.linkedin.com/in/atuljkamble/">
<img src="https://img.shields.io/badge/LinkedIn-atuljkamble-0A66C2?logo=linkedin&style=flat-square" />
</a>
<a href="https://x.com/atul_kamble">
<img src="https://img.shields.io/badge/X-@atul_kamble-000000?logo=x&style=flat-square" />
</a>
</p>

<strong>Version 1.0.0</strong> | <strong>Last Updated:</strong> January 2026
</div>

## 🧩 Kubernetes Architecture — Big Picture

![Image](https://kubernetes.io/images/docs/components-of-kubernetes.svg)

![Image](https://kubernetes.io/images/docs/kubernetes-cluster-architecture.svg)

At its core, Kubernetes follows a **master–worker (control plane–node)** architecture and is governed by the **Cloud Native Computing Foundation (CNCF)**.

---

# 1️⃣ Core Kubernetes Cluster Architecture (Mandatory)

## 1.1 Control Plane (Master Node)

![Image](https://images.ctfassets.net/ud9dfq0vudar/1TGgwO9MZwTFgE2w02M2Zv/918795d7bbd0b20b38d8bba07f3443b4/Architecture_2.png)

![Image](https://miro.medium.com/v2/resize%3Afit%3A1200/1%2Ax_hbMOWBxy65ceS0e7d3UQ.png)

**Components:**

* **kube-apiserver** – Entry point (REST API)
* **etcd** – Distributed key-value store (cluster state)
* **kube-scheduler** – Assigns Pods to Nodes
* **kube-controller-manager** – Runs controllers (ReplicaSet, Node, Job)
* **cloud-controller-manager** (cloud only)

📌 *Brain of the cluster*

---

## 1.2 Worker Node Architecture

![Image](https://kubernetes.io/images/docs/components-of-kubernetes.svg)

![Image](https://devopscube.com/content/images/2025/03/kubelet-architecture-1.png)

**Components:**

* **kubelet** – Node agent
* **kube-proxy** – Networking & Services
* **Container Runtime** – containerd / CRI-O
* **Pods & Containers**

📌 *Executes workloads*

---

# 2️⃣ Single-Node vs Multi-Node Architecture

## 2.1 Single-Node Cluster

![Image](https://www.researchgate.net/publication/360803945/figure/fig4/AS%3A1159097445548033%401653361774483/An-example-of-a-single-node-Kubernetes-cluster-setup-for-a-Fed-DART-FACT-ML-application.png)

![Image](https://i.sstatic.net/tC5NmLgy.png)

* Control Plane + Worker on same node
* Used for **learning & testing**
* ❌ Not production-ready

Examples:

* Minikube
* Kind
* MicroK8s

---

## 2.2 Multi-Node Cluster (Production)

![Image](https://eevans.co/blog/kubernetes-multi-node/multi-node-network.svg)

![Image](https://kubernetes.io/images/docs/components-of-kubernetes.svg)

* Separate Control Plane & Workers
* High availability
* Horizontal scalability

---

# 3️⃣ High Availability (HA) Kubernetes Architecture

![Image](https://kubernetes.io/images/kubeadm/kubeadm-ha-topology-stacked-etcd.svg)

![Image](https://media.licdn.com/dms/image/v2/D4D12AQHnXhDOQrSHbg/article-cover_image-shrink_720_1280/article-cover_image-shrink_720_1280/0/1692213110802?e=2147483647\&t=_KM_Hm7V0_nRJB6iF3SZcU830YbNq95Z7ffZvYjusws\&v=beta)

### HA Control Plane

* Multiple control plane nodes
* External Load Balancer
* etcd cluster (odd number: 3/5)

✅ No single point of failure

---

# 4️⃣ Networking Architecture

![Image](https://cloudnativenow.com/wp-content/uploads/2023/12/Screenshot-2023-12-03-at-8.53.56-PM.png)

![Image](https://www.tigera.io/app/uploads/2021/12/K8s-CNI-diagram01.png)

### Networking Layers

* **Pod-to-Pod**
* **Pod-to-Service**
* **External-to-Service**

### CNI Plugins

* Calico
* Cilium
* Flannel
* Weave

📌 *Flat network, no NAT between Pods*

---

# 5️⃣ Storage Architecture

![Image](https://dz2cdn1.dzone.com/storage/temp/16244676-diagram-55-1.jpg)

![Image](https://miro.medium.com/0%2ASR7qRChnbjn01QhK.jpg)

### Components

* PersistentVolume (PV)
* PersistentVolumeClaim (PVC)
* StorageClass
* CSI Drivers

Supports:

* NFS
* Cloud disks (EBS, Azure Disk)
* Distributed storage (Ceph)

---

# 6️⃣ Deployment & Workload Architecture

![Image](https://platform9.com/media/kubernetes-constructs-concepts-architecture.jpg)

![Image](https://i0.wp.com/azuredays.com/wp-content/uploads/2020/11/k8s-exposed-pod-1.png?resize=748%2C417\&ssl=1)

### Workload Types

* Deployment → Stateless apps
* StatefulSet → Databases
* DaemonSet → Agents (logs, monitoring)
* Job / CronJob → Batch workloads

---

# 7️⃣ Service & Ingress Architecture

![Image](https://miro.medium.com/v2/resize%3Afit%3A1200/1%2AtnK94zrEwyNe1hL-PhJXOA.png)

![Image](https://media.geeksforgeeks.org/wp-content/uploads/20240506105314/Kubernetes-Ingress-Architecture-%281%29.webp)

### Service Types

* ClusterIP
* NodePort
* LoadBalancer
* ExternalName

### Ingress

* Ingress Controller (NGINX, Traefik)
* TLS termination
* Path-based routing

---

# 8️⃣ Security Architecture

![Image](https://platform9.com/media/kubernetes-constructs-concepts-architecture.jpg)

![Image](https://svg.template.creately.com/SFOexgh5zLz)

### Key Security Layers

* RBAC
* Namespaces
* Network Policies
* Secrets & ConfigMaps
* Pod Security Standards
* Admission Controllers

---

# 9️⃣ Observability & Monitoring Architecture

![Image](https://miro.medium.com/1%2AAIRMKYEhJ1RhEVE_7z1f6A.jpeg)

![Image](https://kubernetes.io/images/docs/user-guide/logging/logging-with-streaming-sidecar.png)

### Pillars

* Metrics → Prometheus
* Logs → Fluent Bit / ELK
* Tracing → Jaeger
* Visualization → Grafana

---

# 🔟 Cluster Federation & Multi-Cluster Architecture

![Image](https://www.apptio.com/wp-content/uploads/kubernetes-multi-cluster-architecture.png)

![Image](https://www.xenonstack.com/hubfs/kubernetes-cluster-federation-xenonstack.png)

### Patterns

* Federation (KubeFed)
* Service Mesh multi-cluster
* GitOps-managed clusters

Used for:

* DR
* Global traffic
* Compliance isolation

---

# 1️⃣1️⃣ Service Mesh Architecture

![Image](https://www.tigera.io/app/uploads/2024/07/Service-Mesh-Architecture.png)

![Image](https://istio.io/latest/docs/ops/deployment/architecture/arch.svg)

### Components

* Sidecar proxies
* Control plane
* mTLS
* Traffic shaping

Examples:

* Istio
* Linkerd
* Cilium Mesh

---

# 1️⃣2️⃣ GitOps Architecture

![Image](https://braindose.blog/wp-content/uploads/2020/03/screenshot-2020-03-18-at-10.00.42-am.png)

![Image](https://miro.medium.com/0%2ABiRm9BiQMsZUj_Fv.png)

### Flow

```
Git → GitOps Tool → Kubernetes API → Cluster
```

Tools:

* Argo CD
* Flux

Benefits:

* Auditable
* Declarative
* Rollback-friendly

---

# 1️⃣3️⃣ Cloud-Managed Kubernetes Architecture

![Image](https://miro.medium.com/v2/resize%3Afit%3A1400/1%2A1fYlrnT0jR2Dw2gpCMLD6A.png)

![Image](https://kubernetes.io/images/docs/components-of-kubernetes.svg)

### Characteristics

* Control plane managed by cloud provider
* Auto upgrades & patching
* Integrated IAM & networking

Examples:

* EKS
* AKS
* GKE

---

# 1️⃣4️⃣ Edge & Lightweight Kubernetes Architecture

![Image](https://miro.medium.com/1%2AGFVIZXVQbn3PqMBU5Zvp7g.gif)

![Image](https://docs.k3s.io/assets/images/how-it-works-k3s-revised-9c025ef482404bca2e53a89a0ba7a3c5.svg)

### Used for

* IoT
* Edge computing
* Low-resource environments

Tools:

* K3s
* MicroK8s

---

# 🧠 Summary Table

| Architecture Type | Purpose                     |
| ----------------- | --------------------------- |
| Core Cluster      | Foundation                  |
| HA Cluster        | Production resilience       |
| Networking        | Pod & Service communication |
| Storage           | Stateful workloads          |
| Security          | Zero-trust access           |
| Observability     | Monitoring & logging        |
| Multi-Cluster     | DR & geo-scale              |
| Service Mesh      | Traffic & security          |
| GitOps            | Declarative ops             |
| Managed K8s       | Reduced ops                 |
| Edge K8s          | Lightweight deployments     |

---

