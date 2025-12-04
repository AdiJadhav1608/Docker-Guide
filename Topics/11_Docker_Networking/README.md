# 🐳 Docker Networking — Complete Guide

Docker networking allows containers to **communicate with each other**, with the host machine, and with external networks.

---

## 📌 Why Docker Networking?

- Connect multiple containers  
- Isolate applications  
- Control traffic flow  
- Expose services to users  
- Enable microservices architecture  

---

## 🌐 Types of Docker Networks

### 1️⃣ **Bridge (Default)**
Used for container-to-container communication on the same host.

```
docker network create mybridge
docker run -d --network mybridge nginx
```

---

### 2️⃣ **Host**
Container shares the host’s network stack.

```
docker run --network host nginx
```

Use case: High-performance apps.

---

### 3️⃣ **None**
No networking at all.

```
docker run --network none busybox
```

---

### 4️⃣ **Overlay (Swarm Mode)**
Connects containers across multiple hosts.

```
docker network create -d overlay myoverlay
```

---

### 5️⃣ **Macvlan**
Assigns a container its own MAC address.

```
docker network create -d macvlan mymacvlan
```

---

## 🛠️ Common Networking Commands

### 📋 List networks
```
docker network ls
```

### 🔍 Inspect network
```
docker network inspect mynetwork
```

### ➕ Create network
```
docker network create mynetwork
```

### ➕ Connect container to network
```
docker network connect mynetwork container_name
```

### ➖ Disconnect container
```
docker network disconnect mynetwork container_name
```

### 🗑 Delete network
```
docker network rm mynetwork
```

---

## 🔄 Communication Between Containers

### Example:

```
docker run -d --name backend --network mynet busybox sleep 1000
docker run -it --name frontend --network mynet busybox sh
```

From `frontend`:
```
ping backend
```

---

## 🌍 Exposing Ports

Expose container port to host:
```
docker run -p 8080:80 nginx
```

---

## 🧪 DNS-Based Discovery

Docker provides automatic DNS resolution:
- Containers can reach each other by **name**
- No IP needed

---

## 🏗 Networking in Docker Compose

```
version: "3.9"
services:
  app:
    image: nginx
    networks:
      - webnet

  db:
    image: mysql
    networks:
      - webnet

networks:
  webnet:
```

---

## 🏆 Best Practices

- Use separate networks per environment  
- Prefer bridge networks for local dev  
- Avoid exposing ports unless required  
- Use overlay networks for distributed systems  
- Use meaningful network names  

---

## 🤝 Contribute  
Contributions are welcome! Improve examples, add cases, or explain deeper networking concepts.

---

## 👨‍💻 Author  
**Aditya Jadhav**  
Beginner Cloud & DevOps Learner  

📧 **adijadhav8446@gmail.com**  
🌐 **GitHub Profile:** https://github.com/AdiJadhav1608  
🔗 **LinkedIn:** https://www.linkedin.com/in/aditya-jadhav-718087339/  

⭐ *If you found this helpful, give it a star and keep learning Docker!*  
