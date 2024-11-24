# Transcribe Translate (Kubernetes Version)
This is the **Kubernetes version** of the Transcribe Translate project, a web application for transcription and translation services. It uses pre-built Docker images managed by workflows in the [original repository](https://github.com/NotYuSheng/Transcribe-Translate).

<a href="#"><img alt="last-commit" src="https://img.shields.io/github/last-commit/NotYuSheng/Transcribe-Translate_Kubernetes?color=red"></a>

> [!WARNING]  
> This project is incomplete and still a work in progress

## Features
- **Accurate Transcriptions**: Powered by Whisper models for high-quality audio transcription.
- **Language Translation**: Seamless translation of transcribed content.
- **Kubernetes-Optimized Architecture**: Designed for deployment on Kubernetes clusters, offering scalability and resource management.

## Docker Images
This version relies on the Docker images created and managed via GitHub workflows in the original repository. Switch between the `backend-deployment.cpu.yaml` and `backend-deployment.cuda.yaml` accordingly.

| Component      | Image URL                                                 |
| -------------- | --------------------------------------------------------- |
| Backend CPU    | `ghcr.io/notyusheng/transcribe-translate-backend:cpu`     |
| Backend CUDA   | `ghcr.io/notyusheng/transcribe-translate-backend:cuda`    |
| Frontend       | `ghcr.io/notyusheng/transcribe-translate-frontend:latest` |
| Nginx          | `ghcr.io/notyusheng/transcribe-translate-nginx:latest`    |

## Getting Started
The following instructions are for Ubuntu
1. Install kubectl 
```
sudo apt install -y curl
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
kubectl version --client
```
2. Install Minikube
```
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube
minikube version
```

## Deployment Steps
1. Clone and navigate to folder
```
git clone https://github.com/NotYuSheng/Transcribe-Translate_Kubernetes.git
cd Transcribe-Translate_Kubernetes
```

2. Start Minikube
Set up a single-node Kubernetes cluster
```
minikube start --driver=docker
```

3. Verify that the cluster is running
```
kubectl get nodes
```

4. Apply Kubernetes Manifests
Deploy the app using the Kubernetes manifests in the k8s/ directory:
```
kubectl apply -f k8s/backend-deployment.cuda.yaml
kubectl apply -f k8s/backend-service.yaml
kubectl apply -f k8s/frontend-deployment.yaml
kubectl apply -f k8s/frontend-service.yaml
kubectl apply -f k8s/nginx-deployment.yaml
kubectl apply -f k8s/nginx-service.yaml
```
> [!NOTE]
> Switch between the backend `cuda` and `cpu` version accordingly.

5. Check Deployments and Services
- View Pods to check the containers are running
```
kubectl get pods
```
- Check services (to see exposed ports):

```
kubectl get services
```

6. Access the Application
Use Minikube to access the Nginx service:
```
minikube service nginx
```

## Useful Commands
1. View logs
```
kubectl logs <pod-name>
```

2. Restart Pods
```
kubectl delete pod <pod-name>
```
