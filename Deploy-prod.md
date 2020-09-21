# Production environment

**Be careful, follow step-by-step installation bellow:**

**- OS: CentOS 7.**

## Container runtimes: Docker

```none
# (Install Docker CE)
## Set up the repository
### Install required packages
yum install -y yum-utils device-mapper-persistent-data lvm2
```

```none
## Add the Docker repository
yum-config-manager --add-repo \
https://download.docker.com/linux/centos/docker-ce.repo
```

```none
# Install Docker CE
yum update -y && yum install -y \
  containerd.io-1.2.13 \
  docker-ce-19.03.11 \
  docker-ce-cli-19.03.11
```

```none
## Create /etc/docker
mkdir /etc/docker
```

```none
# Set up the Docker daemon
cat > /etc/docker/daemon.json <<EOF
{
  "exec-opts": ["native.cgroupdriver=systemd"],
  "log-driver": "json-file",
  "log-opts": {
    "max-size": "100m"
  },
  "storage-driver": "overlay2",
  "storage-opts": [
    "overlay2.override_kernel_check=true"
  ]
}
EOF
```

```none
mkdir -p /etc/systemd/system/docker.service.d
```

```none
# Restart Docker
systemctl daemon-reload
systemctl restart docker
```

If you want the docker service to start on boot, run the following command:

```none
sudo systemctl enable docker
```

## Installing kubeadm

```none
cat <<EOF | sudo tee /etc/sysctl.d/k8s.conf
net.bridge.bridge-nf-call-ip6tables = 1
net.bridge.bridge-nf-call-iptables = 1
EOF
sudo sysctl --system
```

```none
cat <<EOF | sudo tee /etc/yum.repos.d/kubernetes.repo
[kubernetes]
name=Kubernetes
baseurl=https://packages.cloud.google.com/yum/repos/kubernetes-el7-\$basearch
enabled=1
gpgcheck=1
repo_gpgcheck=1
gpgkey=https://packages.cloud.google.com/yum/doc/yum-key.gpg https://packages.cloud.google.com/yum/doc/rpm-package-key.gpg
exclude=kubelet kubeadm kubectl
EOF

# Set SELinux in permissive mode (effectively disabling it)
sudo setenforce 0
sudo sed -i 's/^SELINUX=enforcing$/SELINUX=permissive/' /etc/selinux/config

sudo yum install -y kubelet kubeadm kubectl --disableexcludes=kubernetes

sudo systemctl enable --now kubelet
```

```none
systemctl daemon-reload
systemctl restart kubelet
```

## Creating a cluster with kubeadm

```none
kubeadm init --apiserver-advertise-address={IP_SERVER} --pod-network-cidr=192.168.0.0/16
```

```none
kubectl apply -f https://docs.projectcalico.org/v3.16/manifests/calico.yaml
```
