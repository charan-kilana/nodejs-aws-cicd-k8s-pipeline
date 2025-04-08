## 🛠️ Prerequisites

## Make sure Git is installed on your machine. You can install it using the following command:

```bash
yum install git -y
```
## Make sure Jenkins is installed on your machine. You can install it using the following command:
```bash
yum install jenkins -y
```
## Install Trivy on your machine. You can install it using the following commands:
```bash
wget https://github.com/aquasecurity/trivy/releases/download/v0.18.3/trivy_0.18.3_Linux-64bit.tar.gz
tar zxvf trivy_0.18.3_Linux-64bit.tar.gz
sudo mv trivy /usr/local/bin/
vim .bashrc
export PATH=$PATH:/usr/local/bin/
source .bashrc  
```

## Install Docker on your machine. You can install it using the following commands:
```bash
yum install docker -y
```
Give permission to docker to build using the pipeline
```bash
chmod 777 ///var/run/docker.sock
```

### Setup KOPS Cluster

Follow the steps to create and configure a Kubernetes cluster using **KOPS** on AWS.

[kops cluster](docs/docs/kops-setup.md)






