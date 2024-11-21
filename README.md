# Transcribe Translate (Kubernetes Version)
This is the **Kubernetes version** of the Transcribe Translate project, a web application for transcription and translation services. It uses pre-built Docker images managed by workflows in the [original repository](https://github.com/NotYuSheng/Transcribe-Translate).

> [!WARNING]  
> This project is still a work in progress

## Features
- **Accurate Transcriptions**: Powered by Whisper models for high-quality audio transcription.
- **Language Translation**: Seamless translation of transcribed content.
- **Kubernetes-Optimized Architecture**: Designed for deployment on Kubernetes clusters, offering scalability and resource management.

## Docker Images
This version relies on Docker images created and managed via GitHub workflows in the original repository:

| Component | Image URL                                                 |
| --------- | --------------------------------------------------------- |
| Backend   | `ghcr.io/notyusheng/transcribe-translate-backend:latest`  |
| Frontend  | `ghcr.io/notyusheng/transcribe-translate-frontend:latest` |
| Nginx     | `ghcr.io/notyusheng/transcribe-translate-nginx:latest`    |


## Getting Started
1. Install kubectl and Minikube for local Kubernetes deployment.
- Kubernetes Installation Guide

## Deployment Steps
1. Clone and navigate to folder
```
git clone https://github.com/NotYuSheng/Transcribe-Translate_Kubernetes.git
cd Transcribe-Translate
```

2. Apply Kubernetes Manifests
Deploy the app using the Kubernetes manifests in the k8s/ directory:
```
kubectl apply -f k8s/
```

3. Access the Application
Use Minikube to access the Nginx service:
```
minikube service nginx
```
