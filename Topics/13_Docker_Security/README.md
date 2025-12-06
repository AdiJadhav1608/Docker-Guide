# 🛡️ Docker Security — Best Practices & Hardening Guide

Docker Security ensures that containers, images, networks, registries, and hosts are protected from vulnerabilities, attacks, and misconfigurations.

---

## 📌 Why Docker Security Matters?

- Containers share the same OS kernel  
- Misconfigured containers expose the host  
- Insecure images may contain vulnerabilities  
- Exposed ports can be attacked  
- Production environments require strict isolation  

---

## 🧱 Security Layers in Docker

1. **Image Security**  
2. **Container Runtime Security**  
3. **Network Security**  
4. **Host Machine Security**  
5. **Registry Security**  
6. **Secrets Management**  

---

# 1️⃣ Image Security

### ✔ Use Official Images  
```
docker pull nginx
```

### ✔ Scan images for vulnerabilities  
```
docker scan image_name
```

### ✔ Avoid unnecessary packages in images  
Use minimal base images:
- `alpine`
- `scratch`

### ✔ Always pin versions  
Avoid:
```
nginx:latest
```
Use:
```
nginx:1.25
```

---

# 2️⃣ Container Runtime Security

### ✔ Run as non-root user  
In Dockerfile:
```
USER appuser
```

### ✔ Limit container capabilities  
```
docker run --cap-drop ALL nginx
```

### ✔ Restrict resource usage  
```
docker run --memory="512m" --cpus="1" nginx
```

### ✔ Read-only filesystem  
```
docker run --read-only nginx
```

---

# 3️⃣ Network Security

### ✔ Use custom bridge networks  
```
docker network create secure-net
```

### ✔ Avoid exposing unnecessary ports  
Only expose required ones.

### ✔ Use firewall rules  
Use `ufw`, iptables.

---

# 4️⃣ Host Machine Security

### ✔ Keep Docker Engine updated  
### ✔ Disable root SSH login  
### ✔ Use SELinux or AppArmor profiles  
```
docker run --security-opt apparmor=profile_name nginx
```

### ✔ Enable audit logs  

---

# 5️⃣ Registry Security

### ✔ Use Private Registries  
### ✔ Enable authentication  
### ✔ Use HTTPS  

---

# 6️⃣ Secrets Management

Never store secrets in:
- Dockerfiles  
- Compose files  
- ENV variables  

Instead use Docker secrets:
```
echo "mypassword" | docker secret create db_pass -
```

---

## 🧰 Additional Tools

- **Trivy** – Image scanning  
- **Clair** – Vulnerability scanning  
- **Falco** – Runtime security monitoring  
- **Dockle** – Best-practice linter  

---

## 🏆 Best Practices Summary

- Prefer official base images  
- Scan images regularly  
- Use least privilege principle  
- Restrict container capabilities  
- Secure Docker daemon/API  
- Use secrets instead of env vars  
- Avoid `latest` tag  
- Use CI/CD scanning tools  

---

## 🤝 Contribute  
Feel free to contribute more security tips, tools, or real-world hardening examples.

---

## 👨‍💻 Author  
**Aditya Jadhav**  
Beginner Cloud & DevOps Learner  

📧 **adijadhav8446@gmail.com**  
🌐 **GitHub Profile:** https://github.com/AdiJadhav1608  
🔗 **LinkedIn:** https://www.linkedin.com/in/aditya-jadhav-718087339/  

⭐ *If you found this helpful, give it a star and keep learning Docker!*  
