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
1️⃣ Deployment YAML — ECR Image

```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-demo
  labels:
    app: nginx-demo
spec:
  replicas: 2
  selector:
    matchLabels:
      app: nginx-demo
  template:
    metadata:
      labels:
        app: nginx-demo
    spec:
      containers:
        - name: nginx-demo
          image: 865189140490.dkr.ecr.us-east-1.amazonaws.com/demo/hiqode:v1
          imagePullPolicy: Always
          ports:
            - containerPort: 80

```
2️⃣ LoadBalancer Service YAML
```
apiVersion: v1
kind: Service
metadata:
  name: nginx-demo-service
spec:
  type: LoadBalancer
  selector:
    app: nginx-demo
  ports:
    - port: 80
      targetPort: 80
      protocol: TCP

```
What’s Happening Internally

```
Pod → Pull image from ECR

Service → Creates AWS LoadBalancer (ELB / NLB)

ELB → Routes traffic to Pods

```

