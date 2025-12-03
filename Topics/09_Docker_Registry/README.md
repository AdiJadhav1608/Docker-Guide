# 🐳 Docker Registry — Complete Guide

A **Docker registry** is a storage and distribution system for Docker images.  
It allows you to **push, pull, store, and share** your images publicly or privately.

---

## 📌 What is a Docker Registry?

A registry is where Docker images live.  
Examples:

- **Docker Hub** (public registry)
- **GitHub Container Registry**
- **AWS ECR**
- **Google Container Registry**
- **Azure Container Registry**
- Self-hosted **Private Registry**

---

## 🏛 Registry Components

### 1️⃣ Registry  
Stores images.

### 2️⃣ Repository  
A collection of image versions (tags).  
Example:  
`nginx:latest`, `nginx:1.25`, `nginx:alpine`

### 3️⃣ Tag  
Version label for an image.

---

## 🔧 Using Docker Hub

### 🔐 Login to Docker Hub
```
docker login
```

### 🏷 Tag your image
```
docker tag myapp username/myapp:v1
```

### 📤 Push image
```
docker push username/myapp:v1
```

### 📥 Pull image
```
docker pull username/myapp:v1
```

---

## 🏢 Private Docker Registry Setup (Self-Hosted)

Run your own registry:
```
docker run -d -p 5000:5000 --name registry registry:2
```

Push an image to your private registry:
```
docker tag myapp localhost:5000/myapp
docker push localhost:5000/myapp
```

Pull from private registry:
```
docker pull localhost:5000/myapp
```

---

## 🏗 Using AWS ECR (Example)

### 1️⃣ Create repository  
In AWS Console → ECR.

### 2️⃣ Authenticate Docker
```
aws ecr get-login-password --region ap-south-1 | docker login --username AWS --password-stdin <aws_account_id>.dkr.ecr.ap-south-1.amazonaws.com
```

### 3️⃣ Tag image
```
docker tag myapp:latest <aws_repo_url>:latest
```

### 4️⃣ Push image
```
docker push <aws_repo_url>:latest
```

---

## 📝 Best Practices

- Use **semantic versioning** tags  
- Avoid using only `latest`  
- Clean unused images to save space  
- Use **private registries** for internal apps  
- Enable registry authentication & access control  

---

## 🤝 Contribute  
Feel free to contribute improvements or additional registry examples.

---

## 👨‍💻 Author  
**Aditya Jadhav**  
Beginner Cloud & DevOps Learner  

📧 **adijadhav8446@gmail.com**  
🌐 **GitHub Profile:** https://github.com/AdiJadhav1608  
🔗 **LinkedIn:** https://www.linkedin.com/in/aditya-jadhav-718087339/  

⭐ *If you found this helpful, give it a star and keep learning Docker!*  
