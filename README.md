# 🚀 Tutorial Interativo de Kubernetes

Este é um tutorial prático para aprender Kubernetes, onde você pode executar os comandos diretamente em um ambiente local ou online.

## 📌 Passo 1: Configurar o Ambiente

1️⃣ **Instale o Minikube**:
```sh
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube
```

 2️⃣ **Inicie um cluster local**:
```sh 
minikube start
kubectl get nodes
```


## 📌 Passo 2: Criar um Deployment no Kubernetes
Crie um arquivo `nginx-deployment.yaml`:

```sh
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:latest
        ports:
        - containerPort: 80
```

Agora, aplique o Deployment:

```sh
kubectl apply -f nginx-deployment.yaml
kubectl get pods
```

## 📌 Passo 3: Criar um Service
Crie o arquivo `nginx-service.yaml`:

```sh
apiVersion: v1
kind: Service
metadata:
  name: nginx-service
spec:
  selector:
    app: nginx
  ports:
    - protocol: TCP
      port: 80
      targetPort: 80
  type: LoadBalancer
```

Agora aplique o Service:

```sh
kubectl apply -f nginx-service.yaml
kubectl get svc

```

🚀 Agora sua aplicação está rodando! Para acessar no Minikube:

```sh
minikube service nginx-service
```
