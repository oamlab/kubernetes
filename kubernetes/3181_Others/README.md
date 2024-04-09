- OAMlab
- https://github.com/oamlab

# 关于部署Kubernetes的概要资料(Overview of deploying Kubernetes)

---

# Kubernetes


## For Install Kubernetes 1.27.6 1.28.x 1.29.x


### Server Configuration
````
KVM, 4C-16G-10T
KVM, 16C-64G-10T
KVM, 32C-128G-10T

或者使用其他虚拟主机服务器配置。
or use other virtual host server configurations.
````

### Environment deployment planning
- Kubernetes for Middleware

|     Environment Name     | Number of Containers per Set |  Number of Hosts per Set  | Quantity(sets)  |  Number of Hosts  |
|:------------------------:|:----------------------------:|:-------------------------:|:---------------:|:-----------------:|
|         **dev**          |              ≤100            |             ≥3            |        2        |        ≥6         |
|         **test**         |              ≤100            |             ≥3            |        2        |        ≥6         |
|         **prod**         |              ≤100            |             ≥3            |        2        |        ≥6         |

- Kubernetes for Enterprise business application container

|     Environment Name     | Number of Containers per Set |  Number of Hosts per Set  | Quantity(sets) | Number of Hosts |
|:------------------------:|:----------------------------:|:-------------------------:|:--------------:|:---------------:|
|         **dev**          |              ≤10000          |               ≥3          |       2        |       ≥6        |
|         **test**         |              ≤10000          |               ≥3          |       2        |       ≥6        |
|         **prod**         |              ≤10000          |               ≥3          |       3        |       ≥9        |

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
Method A: yum
https://kubernetes.io/zh-cn/docs/setup/production-environment/tools/kubeadm/install-kubeadm/
````

````
Method B: rpm
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
- 不鼓励依赖于使用Web管理面板，应通过命令行去理解kubernetes。应注重使用Kubernetes的原生命令行：kubectl apply -f Deployment_xxx.yaml
- 或者只使用Web管理面板查询。
- Web管理面板即插即用，可卸载。
- Web管理面板的QPS能力为10就可以了。
- 
- Reliance on using the web management panel is discouraged and Kubernetes should be understood through the command line. Attention should be paid to using the native command line of Kubernetes: kubectl apply -f Deployment_xxx.yaml
- Or just query using the web management panel.
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

Install Categraf:
https://github.com/flashcatcloud/categraf/blob/main/k8s/daemonset.yaml
````

### Collect logs
````
https://github.com/elastic/helm-charts/tree/main/elasticsearch

https://github.com/elastic/helm-charts/tree/main/kibana

https://www.elastic.co/guide/en/beats/filebeat/current/running-on-kubernetes.html
https://github.com/elastic/beats/blob/main/deploy/kubernetes/filebeat-kubernetes.yaml
````

### Backup
````
scp Centos_Stream_9_Kubernetes.qcow2 root@192.x.x.x:/opt/backup/Kubernetes/Centos_Stream_9_Kubernetes_20240312_2033.qcow2
````

### Others
1、For Helm
````
https://github.com/bitnami/charts/tree/main/bitnami/mysql

https://github.com/bitnami/charts/tree/main/bitnami/redis-cluster

https://github.com/bitnami/charts/tree/main/bitnami/mongodb

https://github.com/bitnami/charts/tree/main/bitnami/minio

https://github.com/bitnami/charts/tree/main/bitnami/kafka

https://github.com/bitnami/charts/tree/main/bitnami/rabbitmq
````

2、About certificates
````
https://kubernetes.io/zh-cn/docs/tasks/administer-cluster/kubeadm/kubeadm-certs/

自动更新证书
kubeadm 会在控制面升级的时候更新所有证书。
这个功能旨在解决最简单的用例；如果你对此类证书的更新没有特殊要求， 并且定期执行 Kubernetes 版本升级（每次升级之间的间隔时间少于 1 年）， 则 kubeadm 将确保你的集群保持最新状态并保持合理的安全性。

Automatic certificate renewal
kubeadm renews all the certificates during control plane upgrade.
This feature is designed for addressing the simplest use cases; if you don't have specific requirements on certificate renewal and perform Kubernetes version upgrades regularly (less than 1 year in between each upgrade), kubeadm will take care of keeping your cluster up to date and reasonably secure.
````

<p align="center">
	<img alt="kubernetes_3181_img" src="https://www.wegoodgoodstudydaydayup.com/kubernetes_3181.webp?v=202403132123">
</p>

<br>