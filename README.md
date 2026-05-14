# ⚡ Thunder GitOps Guide

This repository contains the GitOps configuration for **Thunder** managed via **OpenChoreo** and **FluxCD**. It automates the deployment lifecycle across Development, Staging, and Production environments.

---

## 🚀 Getting Started

Follow these steps to prepare your cluster and synchronize the GitOps state.

### 1. Cluster Prerequisites

- **OpenChoreo Setup:** Ensure you have an active OpenChoreo cluster and have created the `thunder-idp` namespace.
  - [OpenChoreo Quick Start Guide](https://openchoreo.dev/docs/getting-started/quick-start-guide/)
- **Component Installation:** Install the Thunder component type via Helm:
  - [Thunder Helm Chart Package](https://github.com/asgardeo/thunder/pkgs/container/helm-charts%2Fthunder-oc-componenttype)

### 2. Install FluxCD

FluxCD is the GitOps operator that reconciles the state of your cluster with this repository.

```bash
kubectl apply -f https://github.com/fluxcd/flux2/releases/latest/download/install.yaml
```

### 3. Bootstrap the GitOps Repository

Clone the GitOps repository and apply the Flux configuration to start the synchronization:

```bash
git clone https://github.com/ayeshajay/thunder-githops
cd thunder-githops
kubectl apply -f flux/
```

---

## 🔄 Change Management Workflow

Use the following workflow to onboard new changes or update existing workloads.

### Step 1: Update Workload Configuration

Modify the workload specifications in the following file:

- `workload.yaml`

### Step 2: Deploy to Development

Once a change is committed, merge the automated Pull Request in the **Pull Requests** section. Flux will automatically sync the change to the Dev environment.

### Step 3: Promote to Higher Environments

After verifying changes in Development, trigger the manual promotion workflow to move the state to Staging and Production:

- [Trigger Promote Action](https://github.com/ayeshajay/thunder-githops/actions)

---

## 🌐 Accessing the Thunder Console

### Local DNS Setup

Map the following domains to `127.0.0.1` in your `/etc/hosts` (macOS/Linux) or `C:\Windows\System32\drivers\etc\hosts` (Windows) file:

```
127.0.0.1  development-thunder-thunder-idp.openchoreoapis.demo
127.0.0.1  staging-thunder-thunder-idp.openchoreoapis.demo
127.0.0.1  production-thunder-thunder-idp.openchoreoapis.demo
```

### Environment URLs

The consoles are accessible via the following links:

| Environment | Access URL |
|-------------|------------|
| Development | http://development-thunder-thunder-idp.openchoreoapis.demo:19080/console/ |
| Staging     | http://staging-thunder-thunder-idp.openchoreoapis.demo:19080/console/ |
| Production  | http://production-thunder-thunder-idp.openchoreoapis.demo:19080/console/ |
