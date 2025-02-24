# cc-intel-pccs

**Provisioning Certificate Caching Service (PCCS)** for caching collaterals required for quote generation and quote verification.

## Prerequisites

Ensure you have the following tools installed before proceeding:

- [Git](https://git-scm.com/downloads)
- [Helm](https://helm.sh/docs/intro/install/)
- [Kubectl](https://kubernetes.io/docs/setup/)

## Installation

Clone the repository and navigate to the project directory:

```sh
git clone https://github.com/scontain/cc-intel-pccs.git
cd cc-intel-pccs
```

## Configuration

Configure all parameters marked with "!REQUIRED" in `helm/values.yaml`.

## Deploy PCCS

Deploy PCCS using Helm:

```sh
helm install pccs ./helm --namespace pccs --create-namespace
```

This command installs PCCS in the `pccs` namespace. If the namespace does not exist, it will be created automatically.

## Interact with

To interact with PCCS locally, use kubectl `port-forward` and `curl`:

```sh
kubectl port-forward -n pccs pod/pccs-0 8081:8081 &
curl -k https://127.0.0.1:8081/sgx/certification/v4/rootcacrl
```

## Uninstallation

To remove PCCS from your cluster, run:

```sh
helm uninstall pccs --namespace pccs
```

(Optional) To delete the namespace as well:

```sh
kubectl delete namespace pccs
```
