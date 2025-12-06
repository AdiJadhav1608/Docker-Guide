# 🔗 Docker Bind Mounts — Complete Guide

Docker **bind mounts** allow you to mount a **host machine directory** into a container.  
This provides real-time access to files and directories between host and container.

---

## 📌 Why Use Bind Mounts?

- Share code between host and container  
- Persist data outside container  
- Useful for development & testing  
- Immediate reflection of file changes in container  

---

## 🛠️ Using Bind Mounts

### Syntax:
```
docker run -v /host/path:/container/path image_name
```

### Example:
```
docker run -d \
  -v /home/user/project:/app \
  --name myapp \
  nginx
```
- `/home/user/project` → Host directory  
- `/app` → Container directory  

---

## 🔹 Differences Between Volumes and Bind Mounts

| Feature             | Volume                  | Bind Mount             |
|--------------------|------------------------|-----------------------|
| Location            | Docker managed         | Host managed          |
| Performance         | Better in most cases   | Depends on host       |
| Portability         | High                   | Low                   |
| Use case            | Production             | Development           |

---

## 🧰 Common Commands

### List containers
```
docker ps
```

### Inspect container mount
```
docker inspect container_name
```

### Remove container
```
docker rm -f container_name
```

---

## 🏗 Docker Compose Example (Bind Mount)
```
version: "3.9"
services:
  app:
    image: nginx
    volumes:
      - ./project:/usr/share/nginx/html
    ports:
      - "8080:80"
```

Run:
```
docker compose up -d
```

---

## 🤝 Contribute  
Feel free to improve examples, add use cases, or share tips for bind mounts.

---

## 👨‍💻 Author  
**Aditya Jadhav**  
Beginner Cloud & DevOps Learner  

📧 **adijadhav8446@gmail.com**  
🌐 **GitHub Profile:** https://github.com/AdiJadhav1608  
🔗 **LinkedIn:** https://www.linkedin.com/in/aditya-jadhav-718087339/  

⭐ *If you found this helpful, give it a star and keep learning Docker!*  
