# Udagram Microservices
> Udacity Cloud Developer Nanodegree

`docker --version`  
`aws --version`  
`eksctl version`  
`kubectl version --short --client`  
`aws-iam-authenticator version`  

`code ~/.profile`  

```
export POSTGRESS_USERNAME=udagramdatabase;
export POSTGRESS_PASSWORD=M123456789;
export POSTGRESS_DB=udagramdatabase;
export POSTGRESS_HOST=udagramdatabase.cgremtq7zbcl.eu-west-3.rds.amazonaws.com;
export AWS_REGION=eu-west-3;
export AWS_PROFILE=default;
export AWS_BUCKET=udagram-s3-p4;
export JWT_SECRET=YouAreAwesome;
```

`source ~/.profile`  


Build the images: 
`docker-compose -f docker-compose-build.yaml build --parallel`  
`docker images`  

Run the containers: 
`docker-compose up`  to exit --> `control + C`   

Push the images:
 `dcoker-compose -f docker-compose-build.yaml push`  

 