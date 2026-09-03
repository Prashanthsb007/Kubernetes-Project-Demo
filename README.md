# Kubernetes-Project-Demo
Kubernetes-Project-Demo

## Install Docker

```
sudo apt update -
sudo apt install -y docker.io
sudo systemctl start docker
sudo systemctl enable docker
sudo usermod -aG docker ubuntu
newgrp docker
docker --version

sudo systemctl status docker
```

```
aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 865189140490.dkr.ecr.us-east-1.amazonaws.com

```
