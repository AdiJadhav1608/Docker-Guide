# 🐳 Docker Containers — Complete Guide

A **Docker container** is a running instance of a Docker image.  
It packages your application and runs it in an isolated environment.

---

## 📌 What is a Container?

A container is:
- **Lightweight**
- **Isolated**
- **Fast to start**
- **Portable across any environment**
- Created from a **Docker image**

---

## 🚀 Container Lifecycle

1. **Create** a container  
2. **Start** it  
3. **Run** your application  
4. **Stop** or **Restart** it  
5. **Delete** it

---

## 🛠️ Essential Docker Container Commands

### ▶️ Run a container
```
docker run image_name
```

### ▶️ Run container in background (detached)
```
docker run -d image_name
```

### ▶️ Run with port mapping
```
docker run -p 8080:80 nginx
```

### ▶️ Run with custom name
```
docker run --name mycontainer ubuntu
```

### ▶️ Run with volume
```
docker run -v mydata:/data ubuntu
```

### 📋 List running containers
```
docker ps
```

### 📋 List all containers
```
docker ps -a
```

### ⛔ Stop container
```
docker stop container_name
```

### 🔄 Restart container
```
docker restart container_name
```

### 🗑️ Remove container
```
docker rm container_name
```

---

## 📦 Execute Commands Inside Container

### Open shell inside container
```
docker exec -it container_name bash
```

### Run a command inside container
```
docker exec container_name ls /
```

---

## 🔍 Inspect a Container
```
docker inspect container_name
```

---

## 🧱 Container Logs
```
docker logs container_name
```

---

## 📌 Detached vs Interactive Containers

### Detached Mode
```
docker run -d nginx
```
Runs in background.

### Interactive Mode
```
docker run -it ubuntu bash
```
Gives you a terminal inside the container.

---

## 💡 Real-World Use Case Example

Run a Node.js app:
```
docker run -d -p 3000:3000 --name nodeapp node:18
```

---

## 🤝 Contribute  
Feel free to contribute enhancements or examples.

---

## 👨‍💻 Author  
**Aditya Jadhav**  
Beginner Cloud & DevOps Learner  

📧 **adijadhav8446@gmail.com**  
🌐 **GitHub Profile:** https://github.com/AdiJadhav1608  
🔗 **LinkedIn:** https://www.linkedin.com/in/aditya-jadhav-718087339/  

⭐ *If you found this helpful, give it a star and keep learning Docker!*  
