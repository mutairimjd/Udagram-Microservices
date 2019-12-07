# Udagram Microservices
> Udacity Cloud Developer Nanodegree

## Get Started
[Docker](https://docs.docker.com/docker-for-windows/install/)  
[AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/install-linux.html)  
[Eksctl](https://docs.aws.amazon.com/eks/latest/userguide/getting-started-eksctl.html)  
[AWS-iam-authenticator](https://docs.aws.amazon.com/eks/latest/userguide/install-aws-iam-authenticator.html)  
[Kubectl](https://docs.aws.amazon.com/eks/latest/userguide/install-kubectl.html)  

### Requirements
`docker --version`  
`aws --version`  
`eksctl version`  
`kubectl version --short --client`  
`aws-iam-authenticator version`  

![SetupInstalltion](screenshots/SetupInstalltion.png)

### Setup Environment Variables
open 
`open ~/.profile` 

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

`source ~/.profile`  


Build the images: 
`docker-compose -f docker-compose-build.yaml build --parallel`  
`docker images`  

Run the containers: 
`docker-compose up`  to exit --> `control + C`   

Push the images:
 `dcoker-compose -f docker-compose-build.yaml push`  

 