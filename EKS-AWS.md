# EKS AWS

**1. Create EKS Role In IAM**

*Create 2 Role: eksClusterRoleb and AmazonEKSNodeRole* 

![Create EKS Role](/assets/eks-role-created.PNG "Create EKS Role")

![eksClusterRole](/assets/eksClusterRole.PNG "eksClusterRole")

![AmazonEKSNodeRole](/assets/AmazonEKSNodeRole.PNG "AmazonEKSNodeRole")

**2. Create EKS**

![Create EKS](/assets/eks-created.PNG "Create EKS")

*Step 1* 

![Step 1](/assets/eks-created-cluster-1.PNG "Step 1")

*Step 2*
Choose Security groups default > Next

*Step 3*
Next

*Step 4*
Create

**3. Create Cluster Group Node**

![Group Node Step 1](/assets/eks-created-node-group.PNG "Group Node Step 1")

![Group Node Step 2](/assets/eks-configure-node-group.PNG "Group Node Step 2")

*Next and Create*

**4. Connect Cluster Local**

*4.1. Install and configure your toolchain*

AWS CLI

https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html

kubectl 

https://kubernetes.io/docs/tasks/tools/

aws-iam-authenticator

https://docs.aws.amazon.com/eks/latest/userguide/install-aws-iam-authenticator.html

*4.2. Access aws account*

![Get IAM Key](/assets/iam-access-key.PNG "Get IAM Key")

```js
aws configure

AWS Access Key ID [None]: accesskey
AWS Secret Access Key [None]: secretkey
Default region name [None]: ap-southeast-1
Default output format [None]: json
```

Create or update the kubeconfig file for your cluster:

```js
aws eks --region region update-kubeconfig --name cluster_name
```
Note: Replace region with your AWS Region. Replace cluster_name with your cluster name.

```js
kubectl cluster-info

kubectl get pods

kubectl get svc

kubectl get deployments

kubectl apply -f test.yaml

kubectl scale deployments nginx --replicas=5

kubectl expose deployments/nginx --type=LoadBalancer --port=80
```
