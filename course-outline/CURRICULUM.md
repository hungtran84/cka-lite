# CKA 32-hour outline — by official domain & skill

**Total: 32 hours** (round suggested minutes to fit your session lengths).  
**Weights** are the usual CKA split; hours are approximate shares of 32h.

| Domain | Exam weight | Course hours (guide) |
|--------|-------------|----------------------|
| Cluster Architecture, Installation & Configuration | 25% | **8h** |
| Workloads & Scheduling | 15% | **5h** |
| Services & Networking | 20% | **6h** |
| Storage | 10% | **3h** |
| Troubleshooting | 30% | **9h** |
| Exam logistics & timed practice | — | **1h** |

---

## 0. Prerequisites (before Domain 1)

| Topic | Why | Suggested time | Lab mapping (lab pack) |
|-------|-----|----------------|-------------------------|
| Lab environment and SSH / nodes | Needed for all domains | 30–45 min | **`lab-setup/`** — Lab Setup Guide |
| Container image basics | Runtime context for kubelet/CRI | 30–45 min | **`d0_kubernetes_essentials/`** — Containerize Application |
| First contact with API / cluster | `kubectl`, contexts | 30–45 min | **`d0_kubernetes_essentials/`** — Exploring K8s Cluster |
| Optional: multi-service local stack | Not exam-critical | homework | **`d0_kubernetes_essentials/`** — Docker Compose |

*Include block 0 inside the 32h by borrowing from the 1h exam slot or trimming optional compose.*

---

## Domain: Cluster Architecture, Installation & Configuration (~25% → **8h**)

| # | Curriculum skill (master for the exam) | Suggested time | Lab mapping (lab pack) |
|---|----------------------------------------|----------------|-------------------------|
| 1.1 | **RBAC** — Roles, ClusterRoles, RoleBindings, ClusterRoleBindings; least-privilege access to API resources | 1h 15m | **`d7-kubernetes-security-fundamentals/`** — Security Fundamentals (RBAC focus) |
| 1.2 | **Install cluster with kubeadm** — `kubeadm init`, `join`, tokens, basic options | 1h 30m | **`d1_k8s_installation_configuration_fundamentals/`** — Setup Cluster Using Kubeadm |
| 1.3 | **Cluster lifecycle** — `kubeadm upgrade` workflow (control plane & nodes per curriculum) | 1h 15m | **`d6-maintaining-monitoring-troubleshooting-kubernetes/`** — Cluster Upgrade |
| 1.4 | **etcd backup and restore** — snapshot/restore procedures with cluster tooling as specified in syllabus | 1h | **`d6-maintaining-monitoring-troubleshooting-kubernetes/`** — ETCD & Containerd (etcd portions) |
| 1.5 | **Cluster components** — API server, scheduler, controller-manager, etcd; node: kubelet, kube-proxy, **container runtime (CRI)** | 1h | **`d3_managing_k8s_controllers/`** — Exploring Kube System; **`d6-maintaining-monitoring-troubleshooting-kubernetes/`** — ETCD & Containerd |
| 1.6 | **kubeconfig** — contexts, users, clusters; `kubectl config` | 45m | **`d2_managing_api_server/`** — tie-in while using API Objects / Namespace / Labels |
| 1.7 | **Certificates** — locate cluster CA and certs, renew/reconfigure **as required by current PDF** | 45m | Same as installation / maintenance labs; use syllabus tasks + **`d1_...`** / **`d6_...`** troubleshooting notes |
| 1.8 | **Static Pods** — manifests under static pod path; kubelet-managed | 45m | Reinforce with **`d1_...`** kubeadm lab + control-plane troubleshooting in **`d6_...`** |
| 1.9 | **Extension interfaces (knowledge)** — **CNI / CSI / CRI** roles | 30m | Concept lecture; reinforce with **`d5-...`** (CNI) and **`d4_...`** (CSI) labs |
| 1.10 | **Underlying infrastructure** — OS prep, swap, modules, ports (as needed for kubeadm) | 30m | Embedded in **`d1_...`** Setup Cluster Using Kubeadm |

**Optional / cloud variant (not required by core CKA skills):** **`d1_k8s_installation_configuration_fundamentals/`** — Create GKE Cluster (homework if you use cloud).

**If your PDF lists Helm / Kustomize for cluster components:** add 30–45m and attach a small exercise under **`d1_...`** or a dedicated manifest repo; otherwise defer.

---

## Domain: Workloads & Scheduling (~15% → **5h**)

| # | Curriculum skill | Suggested time | Lab mapping (lab pack) |
|---|------------------|----------------|-------------------------|
| 2.1 | **API resources & versioning** — `apiVersion`, kind; discover with `kubectl explain` | 30m | **`d2_managing_api_server/`** — API Objects, API Object Version |
| 2.2 | **API request flow (awareness)** — how kubectl talks to apiserver | 15m | **`d2_managing_api_server/`** — Anatomy API Request |
| 2.3 | **Pods** — create, inspect, delete; multi-container when syllabus requires | 45m | **`d2_managing_api_server/`** — Running Pods; Multi-Containers — Ambassador / Sidecar (pick **one** pattern if time tight) |
| 2.4 | **Pod lifecycle & probes** | 45m | **`d2_managing_api_server/`** — Pod Lifecycle, Probes |
| 2.5 | **Labels, annotations, namespaces** | 30m | **`d2_managing_api_server/`** — Namespace, Labels |
| 2.6 | **Deployments & ReplicaSets** — scaling, rolling updates, rollbacks | 1h 15m | **`d3_managing_k8s_controllers/`** — Deployment Basics, ReplicaSet; Updating Deployment; Rollback and Restart Deployment; Control Rollout |
| 2.7 | **DaemonSets** | 30m | **`d3_managing_k8s_controllers/`** — DaemonSet |
| 2.8 | **Jobs & CronJobs** | 30m | **`d3_managing_k8s_controllers/`** — Job & CronJob |
| 2.9 | **StatefulSets** (when in syllabus) | 30m | **`d3_managing_k8s_controllers/`** — StatefulSet |
| 2.10 | **Scheduling** — requests/limits, nodeSelector, affinity/anti-affinity, **taints & tolerations** | 1h | **`d3_managing_k8s_controllers/`** — Scheduler Event, Scheduling, Node Cordoning |

**Config as workload config (often practiced with workloads):** **`d4_configuring_managing_k8s_storage/`** — Environment Variables, ConfigMap, Secrets, Docker Registry Secret (see also Domain 4).

---

## Domain: Services & Networking (~20% → **6h**)

| # | Curriculum skill | Suggested time | Lab mapping (lab pack) |
|---|------------------|----------------|-------------------------|
| 3.1 | **Cluster DNS** — CoreDNS behavior, debugging name resolution | 1h | **`d5-configuring-managing-kubernetes-networking/`** — Configuring DNS |
| 3.2 | **Services** — ClusterIP, NodePort, LoadBalancer; endpoints | 1h 30m | **`d5-configuring-managing-kubernetes-networking/`** — Services, Service Discovery |
| 3.3 | **NetworkPolicy** — default deny, pod selectors, ports | 1h 30m | **`d5-configuring-managing-kubernetes-networking/`** — Understanding NetworkPolicy |
| 3.4 | **Ingress** — Ingress rules, controller assumptions at CKA depth | 1h 30m | **`d5-configuring-managing-kubernetes-networking/`** — Ingress |
| 3.5 | **Pod-to-pod connectivity concepts** | 30m | Reinforce in **`d5-...`** Services + DNS labs |

---

## Domain: Storage (~10% → **3h**)

| # | Curriculum skill | Suggested time | Lab mapping (lab pack) |
|---|------------------|----------------|-------------------------|
| 4.1 | **Volumes** — `emptyDir`, config-backed volumes as per tasks | 30m | **`d4_configuring_managing_k8s_storage/`** — Environment Variables / ConfigMap / Secrets (volume mounts) |
| 4.2 | **PersistentVolume & PersistentVolumeClaim** — binding, access modes | 1h | **`d4_configuring_managing_k8s_storage/`** — Static Provisioning PV |
| 4.3 | **StorageClass & dynamic provisioning** | 1h | **`d4_configuring_managing_k8s_storage/`** — Dynamic Provisioning |
| 4.4 | **Reclaim policy & volume mode (as in PDF)** | 30m | Same **`d4_...`** labs; use `kubectl explain` for fields |

---

## Domain: Troubleshooting (~30% → **9h**)

| # | Curriculum skill | Suggested time | Lab mapping (lab pack) |
|---|------------------|----------------|-------------------------|
| 5.1 | **Application failure** — `describe`, events, logs, probes, resource pressure | 2h | **`d6-maintaining-monitoring-troubleshooting-kubernetes/`** — Troubleshooting Workload; **`d2_...`** Probes / Pod Lifecycle for root causes |
| 5.2 | **Control plane failure** — API server, etcd, scheduler, controller-manager symptoms | 2h | **`d6-maintaining-monitoring-troubleshooting-kubernetes/`** — Troubleshooting Control Plane |
| 5.3 | **Worker node failure** — kubelet, runtime, node conditions | 2h | **`d6-maintaining-monitoring-troubleshooting-kubernetes/`** — Troubleshooting Nodes |
| 5.4 | **Networking / DNS** — Service, NetworkPolicy, CNI-level symptoms | 1h 30m | **`d5-configuring-managing-kubernetes-networking/`** + **`d6_...`** cross-troubleshooting |
| 5.5 | **Scheduling failures** — Pending pods, taints, affinity | 1h | **`d3_managing_k8s_controllers/`** Scheduling labs under failure scenarios |
| 5.6 | **Observability tooling** — cluster/workload logging, practical `kubectl` | 30m | **`d6-maintaining-monitoring-troubleshooting-kubernetes/`** — Logging, JSONPath, Monitoring (focus on exam-relevant commands, not building stacks) |

---

## Capstone: Exam logistics & timed practice (**1h**)

| Topic | Lab mapping |
|-------|-------------|
| Doc bookmarks, aliases, timeboxing | Any 2–3 short break/fix labs drawn from **`d3_...`**, **`d5_...`**, **`d6_...`** |
| Verify fixes with explicit `kubectl` checks | Same |

---

## Time reconciliation

- Domain sub-rows are **intentionally slightly over** 32h in raw minutes so you can **trim** (e.g. skip second multi-container pattern, shorten Monitoring to JSONPath only, or merge certificate theory into kubeadm day).
- **Troubleshooting** should stay the **largest** block; thread **`describe` → events → logs** from the first Pod lab onward.

## PDF drift

When Kubernetes minor versions change, **diff the new CKA PDF** against the tables above and add/remove rows; keep lab folder names if your lab pack still matches this layout.
