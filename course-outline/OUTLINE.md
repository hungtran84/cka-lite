# CKA course outline (topics only)

Hierarchical outline aligned with the official CKA domains. For times, labs, and notes see [`CURRICULUM.md`](CURRICULUM.md).

---

## Prerequisites

- Lab environment and node access
- Container image basics
- First contact with the cluster API (`kubectl`, contexts)
- Optional: multi-service local stack (Docker Compose)

---

## 1. Cluster Architecture, Installation & Configuration

- RBAC
  - Roles and ClusterRoles
  - RoleBindings and ClusterRoleBindings
  - Least-privilege access to API resources
- Install cluster with kubeadm
  - `kubeadm init`, `join`, tokens, basic options
- Cluster lifecycle
  - Upgrades with `kubeadm` (control plane and nodes per syllabus)
- etcd backup and restore
- Cluster components
  - Control plane: API server, scheduler, controller-manager, etcd
  - Nodes: kubelet, kube-proxy, container runtime (CRI)
- kubeconfig
  - Contexts, users, clusters
  - `kubectl config`
- Certificates
  - Cluster CA and cert locations
  - Renew or reconfigure per current syllabus
- Static Pods
- Extension interfaces (conceptual)
  - CNI
  - CSI
  - CRI
- Underlying infrastructure for installation
  - OS prep, swap, modules, ports as needed for kubeadm
- Optional: cloud-managed cluster creation (e.g. GKE)
- Optional: Helm / Kustomize for cluster components (if listed in current PDF)

---

## 2. Workloads & Scheduling

- API resources and versioning
  - `apiVersion`, `kind`, `kubectl explain`
- API request flow (awareness)
- Pods
  - Create, inspect, delete
  - Multi-container patterns (as required by syllabus)
- Pod lifecycle
- Probes (readiness, liveness, startup as applicable)
- Labels, annotations, namespaces
- Deployments and ReplicaSets
  - Scaling
  - Rolling updates and rollbacks
- DaemonSets
- Jobs and CronJobs
- StatefulSets (when in syllabus)
- Scheduling
  - Resource requests and limits
  - nodeSelector
  - Affinity and anti-affinity
  - Taints and tolerations
- Configuration for workloads (with workloads practice)
  - Environment variables
  - ConfigMaps and Secrets
  - Image pull secrets (registry)

---

## 3. Services & Networking

- Cluster DNS (CoreDNS)
  - Behavior and debugging name resolution
- Services
  - ClusterIP, NodePort, LoadBalancer
  - Endpoints
- Service discovery
- NetworkPolicy
  - Default deny, selectors, ports
- Ingress
  - Rules and controller assumptions at CKA depth
- Pod-to-pod connectivity (concepts)

---

## 4. Storage

- Volumes and volume mounts
  - Examples: `emptyDir`, config-backed volumes per tasks
- PersistentVolume and PersistentVolumeClaim
  - Binding and access modes
- StorageClass and dynamic provisioning
- Reclaim policy and volume mode (per syllabus)

---

## 5. Troubleshooting

- Application failure
  - Events, logs, probes, resource pressure
- Control plane failure
  - API server, etcd, scheduler, controller-manager
- Worker node failure
  - kubelet, runtime, node conditions
- Networking and DNS
  - Services, NetworkPolicy, CNI-level symptoms
- Scheduling failures
  - Pending pods, taints, affinity
- Observability
  - Logging, JSONPath, practical monitoring with `kubectl`

---

## 6. Exam logistics and timed practice

- Documentation bookmarks and allowed references
- Shell aliases and efficiency
- Timeboxing and verification commands
