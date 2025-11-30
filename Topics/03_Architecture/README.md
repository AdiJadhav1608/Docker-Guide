# 🏗️ Docker Architecture

Docker has a **client-server architecture** that makes containerization lightweight, efficient, and portable.

---

## 🔹 Components of Docker

### 1. Docker Client
- The **command-line interface (CLI)** used to interact with Docker.  
- Example commands: `docker run`, `docker build`, `docker pull`.

### 2. Docker Daemon
- Background service running on your system.  
- Manages images, containers, networks, and volumes.  
- The client communicates with the daemon via REST API.

### 3. Docker Registries
- Store and distribute Docker images.  
- **Public registry:** Docker Hub  
- **Private registry:** Self-hosted or cloud-based

---

## 🌐 How It Works

```
Docker Client  <---->  Docker Daemon  <---->  Container / Images
```

1. **Client** sends a request (`docker run`)  
2. **Daemon** processes request and manages containers  
3. **Images** are pulled from **registries** if not available locally

---

## 🐳 Docker Objects

| Object | Description |
|--------|-------------|
| Image | Read-only template to create containers |
| Container | Running instance of an image |
| Volume | Persistent storage for containers |
| Network | Connects containers together |

---

## ⚡ Benefits of Docker Architecture

- Lightweight & fast compared to VMs  
- Portable across environments  
- Isolated containers for security  
- Easy scaling & orchestration  

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

---

⭐ *If you found this helpful, give it a star and keep learning Docker like a pro!*  
