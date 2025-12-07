# 18_Docker_Swarm_Services

## 📌 Introduction
Docker Swarm **Services** are the core unit of work in a Swarm cluster.  
A *service* defines **what** to run (image), **how many replicas**, and **how it should run** across the swarm nodes.

---

## 📌 Types of Services
### **1. Replicated Service**
Runs a defined number of replicas across nodes.
```
docker service create --name web --replicas 3 nginx
```

### **2. Global Service**
Runs **one container per node**.
```
docker service create --name monitoring --mode global node-exporter
```

---

## 📌 Key Concepts

### **Service Task**
A single running container instance created by a service.

### **Service Update**
Modify configuration without downtime.
```
docker service update --image nginx:latest web
```

### **Service Rollback**
Revert to previous version.
```
docker service rollback web
```

### **Scaling Services**
```
docker service scale web=5
```

---

## 📌 Service Discovery
Every service gets:
- DNS name inside the swarm  
- VIP (Virtual IP) for load balancing  
- Optional DNSRR (DNS round robin)

---

## 📌 Service Placement Constraints
Control where services run.
```
docker service create \
  --name db \
  --constraint 'node.role==manager' \
  mysql
```

---

## 📌 Publishing Ports
Expose service ports externally.
```
docker service create \
  --name web \
  --publish published=80,target=80 \
  nginx
```

---

## 📌 Checking Service Status
```
docker service ls
docker service ps web
docker service inspect web
```

---

## 📌 Remove a Service
```
docker service rm web
```

---

## 📌 Summary
Docker Swarm Services enable:
- Scaling  
- Rolling updates  
- Load balancing  
- High availability  
- Automatic restarts  

They form the backbone of any Swarm-based distributed application.

---

## 🏆 Best Practices

- Use K8s for large/complex microservices architecture  
- Use Docker Swarm for lightweight, fast setups  
- Always enable health checks  
- Externalize configurations  
- Enable logging and monitoring tools  

---

## 🤝 Contribute  
Add your own orchestration diagrams, notes, or real-world setups to help others.

---

## 👨‍💻 Author  
**Aditya Jadhav**  
Beginner Cloud & DevOps Learner  

📧 **adijadhav8446@gmail.com**  
🌐 **GitHub Profile:** https://github.com/AdiJadhav1608  
🔗 **LinkedIn:** https://www.linkedin.com/in/aditya-jadhav-718087339/  

⭐ *If you found this helpful, give it a star and keep learning Docker!*
