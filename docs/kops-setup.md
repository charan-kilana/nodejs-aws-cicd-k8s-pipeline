### ✅ Prerequisites

**Kops setup referece:**
[Install kops](https://github.com/charan-surya-kilana/all-setups/blob/master/kops.sh)

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
- **Create Infra Setup** –

## TO CREATE BUCKET:
```bash
aws s3api create-bucket --bucket charan.k8s.local --region us-east-1
 ```
## TO ENABLE VERSION:
Go into AWS console and enable versioning for your bucket

## EXPORT CLUSTER DATA INTO BUCKET:
```bash
export KOPS_STATE_STORE=s3://charan.k8s.local
```

## GENERATE-KEY:
```bash
ssh-keygen
```

## TO CREATE CLUSTER:
```bash
kops create cluster --name charan.k8s.local --zones us-east-1a --master-size t2.medium --node-size t2.medium
```

## View the cluster:
```bash
kops get cluster
```

## TO RUN THE CLUSTER
```bash
kops update cluster --name charan.k8s.local --yes --admin
```
## Note: To create cluster it usually takes upto 10-15 minutes.
> ### 📝 Note:
> Useful `kops` commands for managing your Kubernetes cluster:
>
> - List clusters:  
>   `kops get cluster`
>
> - Edit cluster config:  
>   `kops edit cluster charan.k8s.local`
>
> - Edit **node** instance group:  
>   `kops edit ig --name=charan.k8s.local nodes-us-east-1a`
>
> - Edit **master** instance group:  
>   `kops edit ig --name=charan.k8s.local master-us-east-1a`
>
> - Delete the cluster:  
>   `kops delete cluster --name cluster-name --yes`








  
