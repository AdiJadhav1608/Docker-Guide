# 22_Docker_Healthchecks

## 📌 Introduction  
Docker **Healthchecks** allow you to monitor whether a container is *healthy*, *unhealthy*, or *starting*.  
This helps Docker automatically restart failing containers and ensures reliable deployments.

---

## 🎯 Why Use Healthchecks?
✔ Detect crashed or frozen applications  
✔ Auto-restart unhealthy containers  
✔ Improve reliability in production  
✔ Ensure services respond before traffic goes to them  
✔ Helpful in orchestration (Compose, Swarm, Kubernetes)  

---

## 📌 Adding a Healthcheck in Dockerfile
```
HEALTHCHECK --interval=30s --timeout=5s --retries=3 \
  CMD curl -f http://localhost:8080/ || exit 1
```

**Explanation:**  
- `interval` → How often to check  
- `timeout` → Max allowed time per check  
- `retries` → Number of failures before marking unhealthy  
- `CMD` → The command to check health  

---

## 📌 Healthcheck in Docker Compose
```yaml
version: "3.9"

services:
  web:
    image: nginx
    healthcheck:
      test: ["CMD", "curl", "-f", "http://localhost"]
      interval: 20s
      timeout: 5s
      retries: 3
```

---

## 📌 Checking Container Health Status
```
docker ps
docker inspect --format='{{json .State.Health}}' container_name
```

Output may show:
- `"Status": "healthy"`
- `"Status": "unhealthy"`
- `"Status": "starting"`

---

## 📌 Creating Custom Healthchecks
### Check if a file exists:
```
HEALTHCHECK CMD test -f /tmp/ready || exit 1
```

### Check a database connection:
```
HEALTHCHECK CMD mysqladmin ping -h localhost || exit 1
```

---

## 📌 Removing a Healthcheck
```
HEALTHCHECK NONE
```

---

## 🏆 Best Practices
- Use lightweight healthcheck commands  
- Avoid heavy scripts (CPU/memory costly)  
- Keep interval short enough for reliability  
- Always add healthchecks for APIs, DBs, and microservices  
- Combine with restart policies  

---

## 🤝 Contribute  
Add more healthcheck scripts or real-world use cases to improve this guide.

---

## 👨‍💻 Author  
**Aditya Jadhav**  
Beginner Cloud & DevOps Learner  

📧 **adijadhav8446@gmail.com**  
🌐 **GitHub Profile:** https://github.com/AdiJadhav1608  
🔗 **LinkedIn:** https://www.linkedin.com/in/aditya-jadhav-718087339/

⭐ *If you found this helpful, give it a star and keep learning Docker!*
