# 24_Docker_Monitoring (cAdvisor, Prometheus)

## 📌 Introduction
Monitoring Docker containers is essential for tracking **CPU, memory, network usage, logs, and overall performance**.  
cAdvisor and Prometheus are widely used for production-grade monitoring.

---

## 📊 What is cAdvisor?
cAdvisor (Container Advisor):
- Collects container metrics  
- Shows real-time dashboards  
- Exposes metrics to Prometheus  

### Run cAdvisor:
```
docker run \
  --name=cadvisor \
  --volume=/:/rootfs:ro \
  --volume=/var/run:/var/run:ro \
  --volume=/sys:/sys:ro \
  --volume=/var/lib/docker/:/var/lib/docker:ro \
  -p 8080:8080 \
  google/cadvisor:latest
```

Access UI:  
👉 http://localhost:8080

---

## 📈 What is Prometheus?
Prometheus:
- Scrapes metrics from cAdvisor  
- Stores time-series data  
- Allows complex alerting and dashboards  

### Prometheus config:
```yaml
global:
  scrape_interval: 5s

scrape_configs:
  - job_name: cadvisor
    static_configs:
      - targets: ["cadvisor:8080"]
```

---

## 📌 Run Prometheus with Docker:
```
docker run -p 9090:9090 \
  -v ./prometheus.yml:/etc/prometheus/prometheus.yml \
  prom/prometheus
```

UI:  
👉 http://localhost:9090

---

## 📊 Integrating Grafana
Grafana can visualize Prometheus metrics beautifully.

```
docker run -d -p 3000:3000 grafana/grafana
```

---

## 🧪 Useful Metrics
- `container_cpu_usage_seconds_total`  
- `container_memory_usage_bytes`  
- `container_network_transmit_bytes_total`  
- `container_fs_usage_bytes`  

---

## 🏆 Best Practices
- Always monitor containers in production  
- Use alerts for CPU, memory, and disk spikes  
- Keep monitoring tools in a separate network  
- Store Prometheus data in persistent volumes  
- Use Grafana dashboards for visualization  

---

## 🤝 Contribute
Add your monitoring dashboards, Prometheus rules, or real-world monitoring architectures.

---

## 👨‍💻 Author  
**Aditya Jadhav**  
Beginner Cloud & DevOps Learner  

📧 **adijadhav8446@gmail.com**  
🌐 **GitHub Profile:** https://github.com/AdiJadhav1608  
🔗 **LinkedIn:** https://www.linkedin.com/in/aditya-jadhav-718087339/

⭐ *If you found this helpful, give it a star and keep learning Docker!*
