# 🌐 Docker Network Types — Bridge, Host & Overlay

Docker provides multiple network types to control how containers communicate with each other, the host, and external systems.

---

## 📌 Overview of Docker Networking

Docker networking enables:
- Container-to-container communication  
- Isolated application environments  
- Load balancing across services  
- Secure communication within distributed systems  

---

# 🔵 1️⃣ Bridge Network (Default)

Bridge networks are the **default** and most commonly used.

### ✔ Best for:
- Running containers on a **single host**
- Local development and testing

### Create a bridge network:
```
docker network create mybridge
```

### Run container inside it:
```
docker run -d --network mybridge nginx
```

---

# 🔴 2️⃣ Host Network

The container shares the **host’s network stack**.

### ✔ Best for:
- High network performance  
- Applications needing host-level networking  
- Services listening on multiple ports

### Run container with host network:
```
docker run --network host nginx
```

### ⚠️ Limitations:
- No port mapping  
- Less isolation  
- Security risk if misconfigured

---

# 🟣 3️⃣ Overlay Network

Used in **Docker Swarm** for multi-host networking.

### ✔ Best for:
- Distributed applications  
- Multi-container and multi-node systems  
- Microservices in Swarm cluster

### Create overlay network:
```
docker network create -d overlay myoverlay
```

### Deploy with Docker Swarm:
```
docker service create --network myoverlay nginx
```

---

# 📊 Comparison Table

| Network Type | Scope | Use Case | Isolation | Performance |
|--------------|--------|----------|-----------|-------------|
| Bridge       | Single host | Local containers | High | Good |
| Host         | Single host | High-speed apps | Low | Excellent |
| Overlay      | Multi-host | Swarm services | High | Good |

---

## 🛠 Useful Commands

### List networks:
```
docker network ls
```

### Inspect a network:
```
docker network inspect mynetwork
```

### Remove a network:
```
docker network rm mynetwork
```

---

## 🏗 Best Practices

- Use **bridge networks** for single-host deployment  
- Use **host mode** only when required  
- Use **overlay networks** for Swarm & microservices  
- Avoid connecting all containers to default bridge  
- Keep network names meaningful  

---

## 🤝 Contribute  
Feel free to add overlays examples, multi-host demos, or real-world networking use cases.

---

## 👨‍💻 Author  
**Aditya Jadhav**  
Beginner Cloud & DevOps Learner  

📧 **adijadhav8446@gmail.com**  
🌐 **GitHub Profile:** https://github.com/AdiJadhav1608  
🔗 **LinkedIn:** https://www.linkedin.com/in/aditya-jadhav-718087339/  

⭐ *If you found this helpful, give it a star and keep learning Docker!*  
