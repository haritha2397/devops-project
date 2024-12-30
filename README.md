terraform-eks
A sample repository to create EKS on AWS using Terraform.

Install AWS CLI
As the first step, you need to install AWS CLI as we will use the AWS CLI (aws configure) command to connect Terraform with AWS in the next steps.

Follow the below link to Install AWS CLI.

https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html
Install Terraform
Next, Install Terraform using the below link.

https://developer.hashicorp.com/terraform/tutorials/aws-get-started/install-cli
Connect Terraform with AWS
Its very easy to connect Terraform with AWS. Run aws configure command and provide the AWS Security credentials as shown in the video.

Initialize Terraform
Clone the repository and Run terraform init. This will intialize the terraform environment for you and download the modules, providers and other configuration required.

Optionally review the terraform configuration
Run terraform plan to see the configuration it creates when executed.

Finally, Apply terraform configuation to create EKS cluster with VPC
terraform apply


Setup Kubernetes Cluster on Amazon EKS:
----------------------------------------
https://medium.com/@mudasirhaji/setup-kubernetes-cluster-on-amazon-eks-56cbbadace04

kops and kubectl:
--------------------------
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install

TO CHECK VERSION:
-----------------
/usr/local/bin/aws --version

TO SET PATH:
---------------
vim .bashrc
export PATH=$PATH:/usr/local/bin/
source .bashrc
aws --version

STEP-3: INSTALL KOPS & KUBECTL:
-------------------------------------
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
wget https://github.com/kubernetes/kops/releases/download/v1.24.1/kops-linux-amd64

PERMISSIONS:
-----------
chmod +x kops-linux-amd64 kubectl
MOVE FILES:
mv kubectl /usr/local/bin/kubectl
MOVE FILES:
mv kops-linux-amd64 /usr/local/bin/kops
TO SEE VERSION:
kubectl version && kops version
STEP-4: CREATE IAM USER WITH ADMIN PERMISSIONS AND CONFIGURE IT IN ANY REGION WITH TABLE FORMAT
STEP-5: CREATE INFRA SETUP
TO CREATE BUCKET:
aws s3api create-bucket --bucket mustafask.k8s.local --region us-east-1
TO ENABLE VERSION:
aws s3api put-bucket-versioning --bucket mustafask.k8s.local --region us-east-1 --versioning-confi guration Status=Enabled
EXPORT CLUSTER DATA INTO BUCKET:
export KOPS_STATE_STORE=s3://mustafask.k8s.local
GENERATE-KEY:
ssh-keygen
TO CREATE CLUSTER:
kops create cluster --name musta.k8s.local --zones us-east-1a --master-size t2.medium --node-size t2.micro
TO SEE THE CLUSTER:
kops get cluster
IF YOU WANT TO EDIT THE CLUSTER:
kops edit cluster cluster_name
TO RUN THE CLUSTER:
kops update cluster --name musta.k8s.local --yes --admin
TO DELETE THE CLUSTER:
Kops delete cluster --name musta.k8s.local --yes
vim .bashrc
export PATH=$PATH:/usr/local/bin/
source .bashrc
aws --version






