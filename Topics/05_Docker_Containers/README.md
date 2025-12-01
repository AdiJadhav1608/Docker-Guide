# 📦 Docker Containers

A **Docker container** is a running instance of a Docker image.  
Containers are lightweight, portable, isolated, and include everything an application needs to run.

---

## 🔹 What Is a Container?

A container is:
- A runnable instance of an image  
- Isolated from the host  
- Faster and lighter than virtual machines  
- Starts in milliseconds  
- Uses a writable layer on top of the image  

---

## 🆚 Containers vs Virtual Machines

| Feature | Containers | Virtual Machines |
|--------|------------|------------------|
| Speed | Very fast | Slow |
| Size | MBs | GBs |
| Boot Time | Seconds / ms | Minutes |
| Isolation | Process-level | Full OS-level |
| Resource Usage | Low | High |

---

## 🚀 Basic Container Commands

### 🔹 Run a container
```bash
docker run ubuntu
```

Run interactively:
```bash
docker run -it ubuntu bash
```

Run in background:
```bash
docker run -d nginx
```

---

## 📋 List Containers

Running containers:
```bash
docker ps
```

All containers:
```bash
docker ps -a
```

---

## 🛑 Stop & Remove Containers

Stop a running container:
```bash
docker stop container_id
```

Remove a container:
```bash
docker rm container_id
```

Remove all stopped containers:
```bash
docker container prune
```

---

## 🧭 Inspect a Container

```bash
docker inspect container_id
```

---

## 📤 Copy Files Between Host and Container

Copy from host → container:
```bash
docker cp file.txt container_id:/path/
```

Copy container → host:
```bash
docker cp container_id:/path/file.txt .
```

---

## 🧪 Execute Commands Inside a Running Container

```bash
docker exec -it container_id bash
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
