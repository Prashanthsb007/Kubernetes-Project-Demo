# Kubernetes-Project-Demo
Kubernetes-Project-Demo

## Install Docker

```
sudo yum update -y
sudo yum install -y docker
sudo service docker start
sudo usermod -aG docker ec2-user
newgrp docker
docker --version
```

```
aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 865189140490.dkr.ecr.us-east-1.amazonaws.com

```
