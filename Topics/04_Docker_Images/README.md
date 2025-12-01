# 🖼️ Docker Images

A **Docker image** is a lightweight, standalone, and executable package that contains everything needed to run a piece of software — code, libraries, dependencies, configurations, and system tools.

---

## 🔹 What Is a Docker Image?

- A **template** used to create containers  
- Built using a **Dockerfile**  
- Stored in Docker Hub or private registries  
- Read-only layers (containers add a writable layer)

---

## 🧱 Image Layers

Docker images are made of **multiple layers**.

Example:
```
Base OS → Runtime → Dependencies → App Code → Config
```

Each instruction in a Dockerfile creates a new layer.

### ✔ Benefits of layered images:
- Faster builds  
- Efficient caching  
- Smaller updates  
- Lightweight  

---

## 📥 Common Image Commands

### 🔹 Pull an image
```bash
docker pull ubuntu
```

### 🔹 List downloaded images
```bash
docker images
```

### 🔹 Remove an image
```bash
docker rmi image_name
```

### 🔹 Remove unused images
```bash
docker image prune
```

---

## 🔍 Inspect an Image
Check detailed information:

```bash
docker inspect image_name
```

---

## 📦 Image Tagging

Tags help identify versions.

```bash
docker pull nginx:latest
docker pull nginx:1.25
```

Create your own tag:

```bash
docker tag myapp:latest myrepo/myapp:v1
```

---

## 🏷️ Search Images on Docker Hub

```bash
docker search mysql
```

---

## 🧪 Run a Container from an Image
```bash
docker run ubuntu
```

---

## 🤝 Contribute

Have suggestions or want to improve something?  
Feel free to open an **issue** or submit a **pull request**.

---

## 👨‍💻 Author

**Aditya Jadhav**  
Beginner Cloud & DevOps Learner  

📧 **adijadhav8446@gmail.com**  
🌐 **GitHub Profile:** https://github.com/AdiJadhav1608
🔗 **LinkedIn:** https://www.linkedin.com/in/aditya-jadhav-718087339/

---

⭐ *If you found this helpful, give it a star and keep learning Docker like a pro!*  
