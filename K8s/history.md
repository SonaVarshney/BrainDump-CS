###  What is Kubernetes (K8s)?

Kubernetes is an **open-source container orchestration platform** used to automate deployment, scaling, and management of containerized applications.

---

###  Brief History

* **2014** – Kubernetes was **open-sourced by Google**, inspired by Google’s internal system **Borg**.
* **2015** – Donated to the **Cloud Native Computing Foundation (CNCF)**.
* **Now** – Widely adopted, supported by cloud giants (AWS, Azure, GCP), and the core of cloud-native infrastructure.

---

###  Why Use Kubernetes?

* Manages **containers** (e.g., Docker) at **scale**.
* Ensures **high availability**, **self-healing**, **auto-scaling**.
* Supports **rolling updates**, **zero downtime deployments**, and **load balancing**.

---

### Key Components

| Component              | Purpose                                                     |
| ---------------------- | ----------------------------------------------------------- |
| **Pod**                | Smallest deployable unit (contains one or more containers). |
| **Node**               | A VM or physical machine running pods.                      |
| **Cluster**            | Set of nodes managed by Kubernetes.                         |
| **Deployment**         | Manages replicas and rollout of pods.                       |
| **Service**            | Exposes a set of pods as a network service.                 |
| **ConfigMap / Secret** | Externalizes app configuration and sensitive info.          |

---

###  Common K8s Features

* **Horizontal Pod Autoscaling** 
* **Self-healing** (restarts crashed containers) 
* **Service Discovery** and **Load Balancing** 
* **Storage orchestration** 
* **Declarative configuration (YAML)** 

---

###  Basic K8s Workflow

1. You define the **desired state** (e.g., 3 replicas of an app) in YAML.
2. Kubernetes uses its **control loop** to match the actual state to the desired state.
3. If a pod dies or is deleted, it **automatically recreates** it.

---

###  Popular Tools in the Ecosystem

* **kubectl** – Command-line tool to interact with K8s.
* **Helm** – Package manager for K8s (like `apt` or `npm`).
* **Minikube** – Run a local K8s cluster.
* **K9s** – Terminal UI for managing K8s clusters.

---
