# 🚀 Docker CI/CD Integration  
A complete guide explaining how to integrate **Docker with CI/CD pipelines** using Jenkins, GitHub Actions, and GitLab CI.  
This README gives you **real-world workflows**, **YAML examples**, and **production best practices**.

---

# 📂 Project Structure

```
29_Docker_CI_CD_Integration/
├── app/
│   ├── Dockerfile
│   ├── src/
│   └── requirements.txt
├── jenkins/
│   └── Jenkinsfile
├── github-actions/
│   └── docker-ci.yml
├── gitlab-ci/
│   └── .gitlab-ci.yml
└── README.md
```

---

# 🔥 1. Overview

CI/CD + Docker is the backbone of modern DevOps.  
Using CI/CD, you can automatically:

- Build Docker images  
- Run tests inside containers  
- Push images to container registry (Docker Hub / ECR / GitHub Container Registry)  
- Deploy to servers (EC2, Kubernetes, or Docker Swarm)

This README explains **three real CI/CD setups**:

1️⃣ Using **Jenkins**  
2️⃣ Using **GitHub Actions**  
3️⃣ Using **GitLab CI/CD**

---

# 🐳 2. Dockerfile Example (Used Across All Pipelines)

```dockerfile
FROM python:3.11-slim

WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt

COPY . .

CMD ["python", "src/app.py"]
```

---

# ⚙️ 3. Jenkins CI/CD Pipeline

## Jenkinsfile (Full Production-Style Pipeline)

```groovy
pipeline {
    agent any

    environment {
        DOCKERHUB_USER = "your-username"
        IMAGE_NAME = "your-image"
    }

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/your/repo.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $DOCKERHUB_USER/$IMAGE_NAME:latest .'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'docker run $DOCKERHUB_USER/$IMAGE_NAME:latest pytest'
            }
        }

        stage('Login to DockerHub') {
            steps {
                withCredentials([string(credentialsId: 'dockerhub_pass', variable: 'DOCKERHUB_PASS')]) {
                    sh 'echo $DOCKERHUB_PASS | docker login -u $DOCKERHUB_USER --password-stdin'
                }
            }
        }

        stage('Push Image') {
            steps {
                sh 'docker push $DOCKERHUB_USER/$IMAGE_NAME:latest'
            }
        }

        stage('Deploy to Server') {
            steps {
                sh """
                ssh ubuntu@your-server-ip \
                'docker pull $DOCKERHUB_USER/$IMAGE_NAME:latest && docker restart app'
                """
            }
        }
    }
}
```

### What this pipeline does:
- Checks out code  
- Builds Docker image  
- Runs tests inside container  
- Pushes image to DockerHub  
- Deploys updated image to server (EC2, DigitalOcean, etc.)  

---

# 🌐 4. GitHub Actions CI/CD

## `.github/workflows/docker-ci.yml`

```yaml
name: Docker CI/CD

on:
  push:
    branches: ["main"]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout Code
      uses: actions/checkout@v3

    - name: Login to DockerHub
      uses: docker/login-action@v2
      with:
        username: ${{ secrets.DOCKER_USERNAME }}
        password: ${{ secrets.DOCKER_PASSWORD }}

    - name: Build Docker Image
      run: docker build -t ${{ secrets.DOCKER_USERNAME }}/myapp:latest .

    - name: Push Image
      run: docker push ${{ secrets.DOCKER_USERNAME }}/myapp:latest

    - name: Deploy to Server (EC2/VM)
      uses: appleboy/ssh-action@v1
      with:
        host: ${{ secrets.SERVER_IP }}
        username: ubuntu
        key: ${{ secrets.SERVER_SSH_KEY }}
        script: |
          docker pull ${{ secrets.DOCKER_USERNAME }}/myapp:latest
          docker compose down
          docker compose up -d
```

### This workflow:
- Builds Docker image on every push  
- Pushes it to DockerHub  
- SSH deploys to your server  

---

# 🏗️ 5. GitLab CI/CD

## `.gitlab-ci.yml`

```yaml
stages:
  - build
  - test
  - push
  - deploy

variables:
  IMAGE_NAME: registry.gitlab.com/youruser/yourproject/myapp

build:
  stage: build
  script:
    - docker build -t $IMAGE_NAME .

test:
  stage: test
  script:
    - docker run $IMAGE_NAME pytest

push:
  stage: push
  script:
    - docker login -u $CI_REGISTRY_USER -p $CI_REGISTRY_PASSWORD $CI_REGISTRY
    - docker push $IMAGE_NAME

deploy:
  stage: deploy
  script:
    - ssh root@your-server "docker pull $IMAGE_NAME && docker compose up -d"
```

---

# 🛠️ 6. How Deployment Works

### Your CI/CD pipeline:
1. Builds Docker image  
2. Pushes it to registry  
3. Tells server to pull new image  
4. Restarts service (Compose / Swarm / Kubernetes)

This is exactly how most companies deploy production apps.

---

# 🧪 7. Local Testing Commands

### Build image
```bash
docker build -t myapp .
```

### Run container
```bash
docker run -p 5000:5000 myapp
```

### Test API
```bash
curl http://localhost:5000/health
```

---

# 🏆 Best Practices

- Use **multi-stage Dockerfiles**  
- Always scan images for vulnerabilities  
- Store secrets in **GitHub secrets / Jenkins credentials**  
- Tag images as  
  - `v1.0.0`  
  - `prod`  
  - `staging`  
- Automate deployment to cloud servers  
- Use registries like **DockerHub, GitHub Container Registry, AWS ECR**  
- Add rollback strategy using tags  

---

# 🤝 Contribute  
Feel free to contribute more CI/CD examples (Bitbucket, Azure DevOps, ArgoCD, Tekton).

---

# 👨‍💻 Author  
**Aditya Jadhav**  
Beginner Cloud & DevOps Learner  

📧 **adijadhav8446@gmail.com**  
🌐 **GitHub Profile:** https://github.com/AdiJadhav1608  
🔗 **LinkedIn:** https://www.linkedin.com/in/aditya-jadhav-718087339/  

⭐ *If this CI/CD guide helped you, give it a star and keep learning DevOps!*  
