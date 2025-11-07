# ACM Governance and OpenShift GitOps Integration

This repository contains a working example of integrating **Red Hat Advanced Cluster Management (ACM)** with **OpenShift GitOps (Argo CD)** and the **Policy Generator** plugin.  
The goal is to demonstrate how governance policies can be defined and deployed declaratively across hub and spoke clusters using GitOps practices.

---

##  Overview

The current setup showcases how to:
- Deploy and manage the **OpenShift GitOps Operator** using ACM’s **Governance Policy Framework**.
- Use the **Policy Generator plugin** to render policy manifests automatically from simple declarative definitions.
- Apply those generated policies across **hub** and **spoke** clusters using ACM **Placements**.
- Render and apply the same structure through Argo CD using Kustomize with `--enable-alpha-plugins`.

This structure enables the management of both compliance policies and operator lifecycle declaratively from a single Git repository.

---

##  Repository Structure

```bash operators/ ├── gitops/ │ ├── manifests/ # YAML manifests for the GitOps Operator │ ├── generator.yaml # Policy Generator definition │ ├── kustomization.yaml # Kustomize entrypoint enabling the Policy Generator │ └── placements/ # Placement and PlacementBinding definitions └── cert-manager/ # Example of another operator policy structure (work in progress) ```


## Roadmap

This is an evolving project. The next steps will include:

- Adding new Policy Generators for other use cases.
- Integrating ApplicationSet controllers to automate GitOps-driven deployments at scale.
- Demonstrating Disaster Recovery (DR) and multi-cluster synchronization scenarios.
- Exploring PolicySet dependencies and advanced placement configurations.

## Notes: 

- The project assumes an existing ACM hub cluster with one or more managed (spoke) clusters.
- OpenShift GitOps (Argo CD) must have --enable-alpha-plugins enabled and the PolicyGenerator plugin installed.
- The repository follows a modular approach to simplify future automation (e.g., via Ansible).
