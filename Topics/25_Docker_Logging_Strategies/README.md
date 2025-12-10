# 25_Docker_Logging_Strategies

## 📌 Introduction  
Docker provides multiple logging mechanisms to capture application logs, troubleshoot issues, and integrate with centralized monitoring systems.  
Choosing the right logging strategy is essential for production environments.

---

## 📚 Types of Docker Logging Drivers

### **1. json-file (Default)**
Stores logs in JSON format on the host.
```
docker run --log-driver=json-file nginx
```

### **2. local**
More efficient than json-file; uses a custom structured format.
```
docker run --log-driver=local nginx
```

### **3. syslog**
Sends logs to a syslog server.
```
docker run --log-driver=syslog nginx
```

### **4. journald**
Integrates with systemd-journald.
```
docker run --log-driver=journald nginx
```

### **5. fluentd**
Sends logs to Fluentd for central aggregation.
```
docker run --log-driver=fluentd nginx
```

### **6. awslogs**
Sends logs to **AWS CloudWatch Logs**.
```
docker run --log-driver=awslogs nginx
```

### **7. gelf**
Sends logs to Graylog/Logstash.
```
docker run --log-driver=gelf nginx
```

---

## 🧾 Viewing Container Logs
```
docker logs container_name
docker logs -f container_name
```

---

## 🛠 Log Rotation (Avoid Disk Full Issues)
Configure `json-file` rotation:

```
{
  "log-driver": "json-file",
  "log-opts": {
    "max-size": "10m",
    "max-file": "3"
  }
}
```

Save to:
```
/etc/docker/daemon.json
```

Restart Docker:
```
systemctl restart docker
```

---

## 📊 Logging in Docker Compose
```yaml
services:
  app:
    image: myapp
    logging:
      driver: "json-file"
      options:
        max-size: "10m"
        max-file: "3"
```

---

## 🏗 Centralized Logging Tools
| Tool        | Purpose |
|-------------|---------|
| **ELK Stack (Elasticsearch + Logstash + Kibana)** | Log search & analytics |
| **Fluentd + Loki + Grafana** | Lightweight log aggregation |
| **AWS CloudWatch** | Fully managed logging |
| **Graylog** | Centralized log management |

---

## 🏆 Best Practices
- Always enable log rotation  
- Use centralized logging for production  
- Avoid storing logs inside containers  
- Use lightweight drivers like `local` for performance  
- Tag logs with container metadata  

---

## 🤝 Contribute  
Share your log aggregation pipelines or production logging architectures.

---

## 👨‍💻 Author  
**Aditya Jadhav**  
Beginner Cloud & DevOps Learner  

📧 **adijadhav8446@gmail.com**  
🌐 **GitHub Profile:** https://github.com/AdiJadhav1608  
🔗 **LinkedIn:** https://www.linkedin.com/in/aditya-jadhav-718087339/

⭐ *If you found this helpful, give it a star and keep learning Docker!*
