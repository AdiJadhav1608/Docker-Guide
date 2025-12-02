# 🐳 Docker Volumes — Persistent Storage Guide

Docker **volumes** allow containers to store data **persistently**, even after the container stops or gets deleted.

---

## 📌 Why Use Volumes?

Volumes help you:
- Keep data safe when containers are removed
- Share data between multiple containers
- Improve performance compared to bind mounts
- Avoid storing data inside containers

---

## 📚 Types of Docker Storage

### 1️⃣ **Volumes (Recommended)**
Managed by Docker in `/var/lib/docker/volumes/`.

```
docker volume create mydata
```

### 2️⃣ **Bind Mounts**
Maps local directory to the container.

```
docker run -v /host/path:/container/path image
```

### 3️⃣ **Tmpfs Mounts (Linux only)**
Stores data in RAM.

```
docker run --tmpfs /app/cache image
```

---

## 🛠️ Volume Commands

### Create a volume
```
docker volume create myvol
```

### List volumes
```
docker volume ls
```

### Inspect a volume
```
docker volume inspect myvol
```

### Remove volume
```
docker volume rm myvol
```

---

## 📦 Use Volume in a Container

### Example:
```
docker run -d \
 -v mydata:/var/lib/mysql \
 --name mysql-db \
 mysql:latest
```

This ensures **MySQL data persists** even if container stops.

---

## 🔄 Share Volume Between Multiple Containers

```
docker run -v sharedvol:/data container1
docker run -v sharedvol:/data container2
```

Both containers access the same data.

---

## 🚀 Using Volumes in Docker Compose

```
version: "3.9"
services:
  app:
    image: nginx
    volumes:
      - webdata:/usr/share/nginx/html

volumes:
  webdata:
```

Run:
```
docker compose up -d
```

---

## 🤝 Contribute  
Feel free to contribute improvements, fixes, or new examples!

---

## 👨‍💻 Author  
**Aditya Jadhav**  
Beginner Cloud & DevOps Learner  

📧 **adijadhav8446@gmail.com**  
🌐 **GitHub Profile:** https://github.com/AdiJadhav1608  
🔗 **LinkedIn:** https://www.linkedin.com/in/aditya-jadhav-718087339/  

⭐ *If you found this helpful, give it a star and keep learning Docker!*  
