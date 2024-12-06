# NVIDIA Cloud Native Stack 


## Introduction

NVIDIA Cloud Native Stack (CNS) is a collection of software to run cloud native workloads on NVIDIA GPUs. NVIDIA Cloud Native Stack is based on Ubuntu/RHEL, Kubernetes, Helm and the NVIDIA GPU and Network Operator.

Interested in deploying NVIDIA Cloud Native Stack? This repository has [install guides](https://github.com/NVIDIA/cloud-native-stack/tree/master/install-guides) for manual installations and [ansible playbooks](https://github.com/NVIDIA/cloud-native-stack/tree/master/playbooks) for automated installations.

Interested in a pre-provisioned NVIDIA Cloud Native Stack environment? [NVIDIA LaunchPad](https://www.nvidia.com/en-us/data-center/launchpad/) provides pre-provisioned environments so that you can quickly get started.

## Objective

- CNS comes as a reference architecture that list all components that have been tested successfully together. the CNS reference architecture can be used as specification for production deployments.

- CNS also comes as installation guides and playbook that can be used to instantiate a quick K8s environment with NVIDIA operators. The CNS installation guides and playbook are intended only for test and PoC environments.

  Note: The K8s layer that CNS install guide or playbook deploys is basic (no HA for instance) and as such cannot be used for production. However all NVIDIA componants in CNS are fully operable in production environment. 

## Life Cycle

When NVIDIA Cloud Native Stack batch is released, the previous batch enters maintenance support and only receives patch release updates. All prior batches enter end-of-life (EOL) and are no longer supported and do not receive patch updates.

> Note: Upgrades are only supported from previous batch to latest batch.


|  Batch  | Status              |
| :-----: | :--------------:|
| [24.11.1](https://github.com/NVIDIA/cloud-native-stack/releases/tag/v24.11.0)                   | Generally Available | 
| [24.8.1](https://github.com/NVIDIA/cloud-native-stack/releases/tag/v24.8.1)                   | Maintenance         |
| [24.5.0](https://github.com/NVIDIA/cloud-native-stack/releases/tag/v24.5.0) and lower                   | EOL                 |


For more information, Refer [Cloud Native Stack Releases](https://github.com/NVIDIA/cloud-native-stack/releases)

## Component Matrix

#### Cloud Native Stack Batch 24.11.0 (Release Date: 14 November 2024)

| CNS Version               | 14.0    | 13.2 | 12.3 |
| :-----:                   | :-----: | :------: | :------: |
| Platforms                 | <ul><li>NVIDIA Certified Server (x86 & arm64)</li><li>DGX Server</li></ul> | <ul><li>NVIDIA Certified Server (x86 & arm64)</li><li>DGX Server</li></ul> | <ul><li>NVIDIA Certified Server (x86 & arm64)</li><li>DGX Server</li></ul> |
| Supported OS              |  <ul><li>Ubuntu 22.04 LTS</li><li>RHEL 8.10</li><li>DGX OS 6.2(Ubuntu 22.04 LTS)</li></ul> |  <ul><li>Ubuntu 22.04 LTS</li><li>RHEL 8.10</li><li>DGX OS 6.2(Ubuntu 22.04 LTS)</li></ul> |  <ul><li>Ubuntu 22.04 LTS</li><li>RHEL 8.10</li><li>DGX OS 6.2(Ubuntu 22.04 LTS)</li></ul> |
| Containerd                | 1.7.23 | 1.7.23 | 1.7.23 |
| NVIDIA Container Toolkit  | 1.17.3 | 1.17.3 | 1.17.3 |
| CRI-O                     | 1.31.2 | 1.30.6 | 1.29.10 |
| Kubernetes                | 1.31.2 | 1.30.6 | 1.29.10 |
| CNI (Calico)              | 3.28.2 | 3.28.2 |  3.28.2 |
| NVIDIA GPU Operator       | 24.9.1 | 24.9.1 | 24.9.1 |
| NVIDIA Network Operator   | 24.7.0 | 24.7.0 | 24.7.0 |
| NVIDIA Data Center Driver | 550.127.08 | 550.127.08 | 550.127.08 |
| Helm                      | 3.16.2 | 3.16.2 | 3.16.2 |

> Note: To Previous Cloud Native Stack release information can be found [here](https://github.com/NVIDIA/cloud-native-stack/tree/24.5.0?tab=readme-ov-file#nvidia-cloud-native-stack-component-matrix)

`NOTE:` Cloud Native Stack versions are available with the master branch but it's recommend to use the specific branch.

# Software

`NOTE:` currently MicroK8s functionality is limited with GPU Operator 24.9.0 as there's known [bug](https://github.com/NVIDIA/gpu-operator/issues/1109). we expected to fix this with another release soon. 

- Kubernetes
  - [GPU Operator](https://github.com/NVIDIA/gpu-operator)
  - [Network Operator](https://github.com/Mellanox/network-operator)  
  - [NVIDIA NIM Operator](https://docs.nvidia.com/nim-operator/latest/index.html)
  - [FeatureGates](https://github.com/NVIDIA/cloud-native-stack/tree/master/playbooks#enable-feature-gates-to-cloud-native-stack)
- [MicroK8s on CNS](https://github.com/NVIDIA/cloud-native-stack/tree/master/playbooks#enable-microk8s)
- [Installation on CSP's](https://github.com/NVIDIA/cloud-native-stack/tree/master/playbooks#installation-on-csps)
- [Storage on CNS](https://github.com/NVIDIA/cloud-native-stack/tree/master/playbooks#storage-on-cns)
- [Monitoring on CNS](https://github.com/NVIDIA/cloud-native-stack/tree/master/playbooks#monitoring-on-cns)
- [LoadBalancer on CNS](https://github.com/NVIDIA/cloud-native-stack/tree/master/playbooks#load-balancer-on-cns)
- [Kserve](https://github.com/NVIDIA/cloud-native-stack/tree/master/playbooks#enable-kserve-on-cns)
- [LeaderWorkerSet(lws)](https://github.com/NVIDIA/cloud-native-stack/tree/master/playbooks#enable-leaderworkerset)

| CNS Version               | 14.0    | 13.2 | 12.3 |
| :-----:                   | :-----: | :------: | :------: |
| MicroK8s                  | 1.31    | 1.30     | 1.29 |
| KServe                    | <br /> **0.14** <br /> <br /> <ul><li>Istio: 1.23.2</li><li>Knative: 1.15.7</li><li>CertManager: 1.16.1</li></ul> | <br /> **0.14** <br /> <br /> <ul><li>Istio: 1.23.2</li><li>Knative: 1.15.7</li><li>CertManager: 1.16.1</li></ul>  | <br /> **0.14** <br /> <br /> <ul><li>Istio: 1.23.2</li><li>Knative: 1.15.7</li><li>CertManager: 1.16.1</li></ul> | 
| LeaderWorkerSet           | 0.4.1 | 0.4.1 | 0.4.1|
| LoadBalancer              | MetalLB: 0.14.5 | MetalLB: 0.14.5 | MetalLB: 0.14.5 |
| Storage                   | NFS: 4.0.18 <br /> Local Path: 0.0.30 | NFS: 4.0.18 <br /> Local Path: 0.0.30 | NFS: 4.0.18 <br /> Local Path: 0.0.30 | 
| Monitoring                | Prometheus: 25.27.0 <br /> Prometheus Adapter: 4.11.0 <br /> Elastic: 8.15.3 | Prometheus: 25.27.0 <br /> Prometheus Adapter: 4.11.0 <br /> Elastic: 8.15.3 | Prometheus: 25.27.0 <br /> Prometheus Adapter: 4.11.0 <br /> Elastic: 8.15.3 |

# Getting Started

#### Prerequisites

Please make sure to meet the following prerequisites to Install the Cloud Native Stack

- system has direct internet access
- system should have an Operating system either Ubuntu 22.04 and above or RHEL 8.10
- system has adequate internet bandWidth
- DNS server is working fine on the System
- system can access Google repo(for k8s installation)
- system has only 1 network interface configured with internet access. The IP is static and doesn't change
- UEFI secure boot is disabled
- Root file system should has at least 40GB capacity
- system has 2CPU and 4GB Memory
- At least one NVIDIA GPU attached to the system

#### Installation 

Run the below commands to clone the NVIDIA Cloud Native Stack.

```
git clone https://github.com/NVIDIA/cloud-native-stack.git
cd cloud-native-stack/playbooks
```

Update the hosts file in playbooks directory with master and worker nodes(if you have) IP's with username and password like below

```
nano hosts

[master]
<master-IP> ansible_ssh_user=nvidia ansible_ssh_pass=nvidipass ansible_sudo_pass=nvidiapass ansible_ssh_common_args='-o StrictHostKeyChecking=no'
[nodes]
<worker-IP> ansible_ssh_user=nvidia ansible_ssh_pass=nvidiapass ansible_sudo_pass=nvidiapass ansible_ssh_common_args='-o StrictHostKeyChecking=no'
```

Install the NVIDIA Cloud Native Stack stack by running the below command. "Skipping" in the ansible output refers to the Kubernetes cluster is up and running.

```
bash setup.sh install
```
For more Information about customize the values, please refer [Installation](https://github.com/NVIDIA/cloud-native-stack/tree/master/playbooks#installation)

# Topologies

- Cloud Native Stack allows to deploy:
    - 1 node with both control plane and worker functionalities
    - 1 control plane node and any number of worker nodes

`NOTE:` (Cloud Native Stack does not allow the deployment of several control plane nodes)

# Troubleshooting

[Troubleshoot CNS installation issues](https://github.com/NVIDIA/cloud-native-stack/blob/master/troubleshooting/README.md)

# Getting help or Providing feedback

Please open an [issue](https://github.com/NVIDIA/cloud-native-stack/issues) on the GitHub project for any questions. Your feedback is appreciated.

# Useful Links
- [NVIDIA LaunchPad](https://www.nvidia.com/en-us/data-center/launchpad/)
- [NVIDIA LaunchPad Labs](https://docs.nvidia.com/launchpad/index.html)
- [Cloud Native Stack on LaunchPad](https://docs.nvidia.com/LaunchPad/developer-labs/overview.html)
- [NVIDIA GPU Operator](https://docs.nvidia.com/datacenter/cloud-native/gpu-operator/overview.html)
- [NVIDIA Network Operator](https://docs.nvidia.com/networking/display/COKAN10/Network+Operator)
- [NVIDIA Certified Systems](https://www.nvidia.com/en-us/data-center/products/certified-systems/)
- [NVIDIA GPU Cloud (NGC)](https://catalog.ngc.nvidia.com/)
