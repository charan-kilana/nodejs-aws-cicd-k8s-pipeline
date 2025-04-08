### ✅ Prerequisites

Ensure the following tools are installed and configured on your system:

- **kubectl** – Command-line tool for interacting with Kubernetes clusters.
   ```bash
  curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
  chmod +x kubectl
  mv kubectl /usr/local/bin/kubectl
  ```
  Installation guide: [Install kubectl](https://docs.aws.amazon.com/eks/latest/userguide/install-kubectl.html)

- **KOPS** – Command-line tool to easily create and manage EKS clusters.
  ```bash
  curl -Lo kops https://github.com/kubernetes/kops/releases/download/$(curl -s https://api.github.com/repos/kubernetes/kops/releases/latest | grep tag_name | cut -d '"' -f 4)/kops-linux-amd64
  chmod +x kops
  sudo mv kops /usr/local/bin/kops
  ```
  Installation guide: [Install kops](https://kops.sigs.k8s.io/getting_started/install/)

- **AWS CLI** – Command-line tool for working with AWS services.
  ```bash
  curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
  unzip awscliv2.zip
  sudo ./aws/install
  /usr/local/bin/aws --version
  vim .bashrc
  export PATH=$PATH:/usr/local/bin/
  source .bashrc
  ```
Installation guide: [Install AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-install.html)

After installing the AWS CLI, configure it using the following command:  
CREATE IAM USER WITH ADMIN PERMISSIONS AND CONFIGURE IT IN ANY REGION WITH TABLE FORMAT
```bash
aws configure
```
