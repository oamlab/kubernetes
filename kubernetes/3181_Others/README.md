- OAMlab
- https://github.com/oamlab

# 关于部署Kubernetes的概要资料(Overview of deploying Kubernetes)

---

# Kubernetes


## For Install Kubernetes 1.27.6 1.28.x 1.29.x


### Operating System
````
CentOS Stream 9 x86 64
https://mirrors.tuna.tsinghua.edu.cn/centos-stream/9-stream/BaseOS/x86_64/iso/CentOS-Stream-9-latest-x86_64-boot.iso
````

### Install Docker
````
https://docs.docker.com/engine/install/centos/
````

### Install Containerd
````
https://kubernetes.io/zh-cn/docs/setup/production-environment/container-runtimes/
````

### Install Kubernetes
````
Method A:
https://kubernetes.io/zh-cn/docs/setup/production-environment/tools/kubeadm/install-kubeadm/
````

````
Method B:
https://mirrors.tuna.tsinghua.edu.cn/kubernetes/yum/repos/kubernetes-el7-x86_64/Packages/
https://mirrors.tuna.tsinghua.edu.cn/kubernetes/yum/repos/kubernetes-el7-x86_64/Packages/12592ba0c35220af878a91ded391d796243155f29032739b0a7b4f53f2134cf9-kubelet-1.27.6-0.x86_64.rpm
https://mirrors.tuna.tsinghua.edu.cn/kubernetes/yum/repos/kubernetes-el7-x86_64/Packages/873fd10acbb0d4c6fa1041c70a733cc99f403dbce8fb3f3c825a11ebbe0792aa-kubectl-1.27.6-0.x86_64.rpm
https://mirrors.tuna.tsinghua.edu.cn/kubernetes/yum/repos/kubernetes-el7-x86_64/Packages/b551bc583f95854dd3f0e3cb8361cc1cef57ada75aef31b709c63f0da37b1fbd-kubeadm-1.27.6-0.x86_64.rpm
````

### Create Kubernetes cluster
````
https://kubernetes.io/zh-cn/docs/setup/production-environment/tools/kubeadm/create-cluster-kubeadm/
````

### Install Helm
````
https://helm.sh/docs/intro/install/
````

### Install Web Management Panel
- 应注重使用Kubernetes的原生命令行：kubectl apply -f Deployment_xxx.yaml
- Web管理面板即插即用，可卸载。
- Web管理面板的QPS能力为10就可以了。
- 
- Attention should be paid to using the native command line of Kubernetes: kubectl apply -f Deployment_xxx.yaml
- The web management panel is plug and play and can be uninstalled.
- A QPS capability of 10 for the web management panel is sufficient.
````
Dashboard:
https://github.com/kubernetes/dashboard

Rancher:
https://ranchermanager.docs.rancher.com/zh/getting-started/installation-and-upgrade/other-installation-methods/rancher-on-a-single-node-with-docker

Kuboard:
https://www.kuboard.cn/install/v3/install-in-k8s.html

KubeSphere:
https://kubesphere.io/zh/docs/v3.4/installing-on-kubernetes/introduction/overview/

Others ...
````

### Monitor
````
Install Nightingale:
Nightingale: compose-host-network
https://flashcat.cloud/docs/content/flashcat-monitor/nightingale-v6/install/docker-compose/
https://gitlink.org.cn/ccfos/nightingale/tree/main/docker%2Fcompose-host-network

Install Categraf
https://github.com/flashcatcloud/categraf/blob/main/k8s/daemonset.yaml
````

### Collect logs
````
https://www.elastic.co/guide/en/beats/filebeat/current/running-on-kubernetes.html
https://github.com/elastic/beats/blob/main/deploy/kubernetes/filebeat-kubernetes.yaml
````

### Backup
````
scp Centos_Stream_9_Kubernetes.qcow2 root@192.x.x.x:/opt/backup/Kubernetes/Centos_Stream_9_Kubernetes_20240312_2033.qcow2
````

### Others
````
...
````