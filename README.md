# Udagram Microservices
> Udacity Cloud Developer Nanodegree


## Getting Started
### Prerequisites
[Docker](https://docs.docker.com/docker-for-windows/install/)  
[AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/install-linux.html)  
[Eksctl](https://docs.aws.amazon.com/eks/latest/userguide/getting-started-eksctl.html)  
[AWS-iam-authenticator](https://docs.aws.amazon.com/eks/latest/userguide/install-aws-iam-authenticator.html)  
[Kubectl](https://docs.aws.amazon.com/eks/latest/userguide/install-kubectl.html)  

### Installation
`docker --version`  
`aws --version`  
`eksctl version`  
`kubectl version --short --client`  
`aws-iam-authenticator version`  

![SetupInstalltion](screenshots/SetupInstalltion.png)  

### Setup Environment Variables
open your bash profile to store your application variables at OS level to use them within and across applications: 
```
open ~/.profile
```

copy and paste the bash scripts bellow with your values:
```
export POSTGRESS_USERNAME=your postgress username;
export POSTGRESS_PASSWORD=your postgress password;
export POSTGRESS_DB=your postgress database;
export POSTGRESS_HOST=your postgress host;
export AWS_REGION=your aws region;
export AWS_PROFILE=your aws profile;
export AWS_BUCKET=your aws bucket name;
export JWT_SECRET=your jwt secret;
```
source your .profile to execute your bash scripts automatically whenever a new interactive shell is started:
```
source ~/.profile
```  

### Setup docker enviroment
Build the images: 
`docker-compose -f docker-compose-build.yaml build --parallel`  

![SetupInstalltion](screenshots/BuildImages.png)  
  
List your docker images to check if they have been built:
`docker images`  

![SetupInstalltion](screenshots/ListImages.png)  

Run your docker containers: 
`docker-compose up`  

![SetupInstalltion](screenshots/RunContainers.png)  

To exit run `control + C`


Push your docker images:
 `dcoker-compose -f docker-compose-build.yaml push`  

![SetupInstalltion](screenshots/PushImages.png)  

Check your Docker Hub, if the images reach on there:

![SetupInstalltion](screenshots/DockerHub.png)  


### Create a Kubernetes cluster on Amazon EKS with eksctl
copy and paste the bash scripts bellow with your cluster name and configration variables:

```
eksctl create cluster \ 
--name "ClusterName" \
--version 1.14 \
--nodegroup-name standard-workers \
--node-type t3.medium \
--nodes 3 \
--nodes-min 1 \
--nodes-max 4 \
--node-ami auto
```

![SetupInstalltion](screenshots/ClusterCreation.png) 
 
 ### Create Kubernetes components (configmaps and secrets)

 Encrypt your database username and password using base64 using the following commands:
- `echo POSTGRESS_PASSWORD | base64`
- `echo POSTGRESS_USERNAME | base64`
Encrypt your aws file using base64 using the following commands:
- `cat ~/.aws/credentials | base64`
Add these values in the appropriate places in your `env-secret.yaml`, `aws-secret.yaml`, and `env-configmap.yaml`.

 ### Setup Kubernetes Environment
 Load secret files:
- `kubectl apply -f aws-secret.yaml
- `kubectl apply -f env-secret.yaml`
- `kubectl apply -f env-configmap.yaml`
Apply all other yaml files:
- `kubectl apply -f .`

![SetupInstalltion](screenshots/SetupKubernetesComponents.png) 

### Check your pods status

`kubectl get all`  

![PodsStatus](screenshots/PodsStatus.png) 





