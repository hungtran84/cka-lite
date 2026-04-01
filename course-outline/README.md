# CKA — 32-hour course (curriculum-aligned)

This folder holds a **32-hour** agenda built from the **official CNCF CKA exam domains and skills**, with **hands-on labs** mapped to the common **CKA lab pack** directory layout (`d0_…` through `d7_…`, `lab-setup/`).

## CKA exam format

The certification exam is **2 hours**, **performance-based**, and **hands-on in a live terminal** (solve tasks on a real cluster). There are **no multiple-choice** or theory-only sections—every scored item is practical work. Details and policies are on the [CNCF CKA page](https://www.cncf.io/certification/cka/).

Hands-on work in **this course** uses a **lab environment you stand up at the beginning** (see `lab-setup/` in your lab pack)—not CNCF’s live exam environment, but the same kind of terminal-and-cluster tasks.

## Canonical syllabus

Always reconcile wording with the current PDF:

- [Certified Kubernetes Administrator (CKA) | CNCF](https://www.cncf.io/certification/cka/)
- [CKA curriculum PDF (e.g. `CKA_Curriculum_v1.35.pdf`) — cncf/curriculum](https://github.com/cncf/curriculum/blob/master/CKA_Curriculum_v1.35.pdf)

## Where to read the outline

- **[`OUTLINE.md`](OUTLINE.md)** — topics only: domains and sub-items (no times or labs).
- **[`CURRICULUM.md`](CURRICULUM.md)** — full breakdown: each skill, suggested time, and lab mapping.

## Lab pack layout (paths)

Lab exercises are referenced by top-level folder names (clone any CKA lab repository that follows this structure):

| Folder | Role |
|--------|------|
| `lab-setup/` | Environment and cluster access |
| `d0_kubernetes_essentials/` | Containers, compose, first cluster contact |
| `d1_k8s_installation_configuration_fundamentals/` | Kubeadm, optional cloud cluster |
| `d2_managing_api_server/` | API awareness, Pods, probes, labels, namespaces |
| `d3_managing_k8s_controllers/` | Workloads, rollout, scheduler, cordon |
| `d4_configuring_managing_k8s_storage/` | PV/PVC/SC, ConfigMaps, Secrets |
| `d5-configuring-managing-kubernetes-networking/` | DNS, Services, NetworkPolicy, Ingress |
| `d6-maintaining-monitoring-troubleshooting-kubernetes/` | etcd, upgrades, logs, troubleshooting |
| `d7-kubernetes-security-fundamentals/` | Security topics overlapping CKA (e.g. RBAC) |

If your PDF adds or removes a skill, adjust **`CURRICULUM.md`** and the linked labs in the same row.
