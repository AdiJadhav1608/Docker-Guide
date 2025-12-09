# 23_Docker_Resource_Management (CPU, Memory Limits)

## 📌 Introduction
Docker allows you to **limit CPU, memory, and other resources** to prevent containers from consuming too much system capacity.  
This ensures fair usage, stability, and better performance.

---

## 🧠 Memory Limits
### Set max memory:
```
docker run -m 512m nginx
```

### Prevent swapping:
```
docker run -m 512m --memory-swap=512m nginx
```

---

## ⚙ CPU Limits  
### Limit CPU usage:
```
docker run --cpus="1.5" nginx
```

### Assign CPU shares (relative priority):
```
docker run --cpu-shares=512 nginx
```

### Assign specific CPU cores:
```
docker run --cpuset-cpus="0,2" nginx
```

---

## 📌 In Docker Compose
```yaml
services:
  app:
    image: myapp
    deploy:
      resources:
        limits:
          cpus: "1.0"
          memory: "512M"
```

---

## 🧪 Check Resource Usage
```
docker stats
```

---

## 🏆 Best Practices
- Always set limits for production workloads  
- Prevent memory leaks using strict memory limits  
- Use `docker stats` for monitoring  
- Use CPU sets for performance-critical apps  
- Avoid over-allocating CPU on small machines  

---

## 🤝 Contribute
Add real-world resource tuning examples or optimization tips.

---

## 👨‍💻 Author  
**Aditya Jadhav**  
Beginner Cloud & DevOps Learner  

📧 **adijadhav8446@gmail.com**  
🌐 **GitHub Profile:** https://github.com/AdiJadhav1608  
🔗 **LinkedIn:** https://www.linkedin.com/in/aditya-jadhav-718087339/

⭐ *If you found this helpful, give it a star and keep learning Docker!*
