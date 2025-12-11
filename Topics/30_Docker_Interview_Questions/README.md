# 🎯 Docker Interview Questions  
A complete set of **beginner, intermediate, advanced, and scenario-based Docker interview questions** ideal for DevOps, Cloud, and SRE interviews.

---

# 🟢 1. Beginner Level Questions

### 1. What is Docker?
Docker is a platform that allows you to package applications into containers.

### 2. What is a container?
A lightweight, isolated runtime environment.

### 3. What is a Docker image?
A read-only blueprint used to create containers.

### 4. What is Docker Hub?
Docker’s public Docker image registry.

### 5. Difference between Virtual Machines and Docker containers?
- VM = Heavy, includes OS  
- Docker = Lightweight, shares host OS kernel

### 6. What is a Dockerfile?
A file with instructions for building Docker images.

### 7. What is `docker run` used for?
To start a new container.

### 8. What is `docker pull`?
Downloads an image from Docker Hub.

### 9. What is `docker ps`?
Lists running containers.

### 10. What is `docker exec`?
Executes commands inside a running container.

---

# 🟡 2. Intermediate Level Questions

### 11. What is the difference between ENTRYPOINT and CMD?
- `CMD` can be overridden
- `ENTRYPOINT` always runs

### 12. What is Docker Compose?
Used to run multi-container applications using a YAML file.

### 13. What are Docker volumes?
Persistent storage managed by Docker.

### 14. Difference between bind mounts and volumes?
- **Volume:** Docker-managed  
- **Bind mount:** Host directory mapped directly

### 15. What is a Docker registry?
A storage system for Docker images (e.g., Docker Hub, AWS ECR)

### 16. How do you remove all stopped containers?
```bash
docker container prune
```

### 17. How do you check logs of a container?
```bash
docker logs <container-id>
```

### 18. How do you inspect a container?
```bash
docker inspect <id>
```

### 19. What is a multi-stage build?
A technique to reduce image size by using multiple `FROM` statements.

### 20. Explain container networking types.
- Bridge  
- Host  
- None  
- Overlay (Swarm/K8s)

---

# 🔴 3. Advanced Level Questions

### 21. How do you optimize Docker image size?
- Multi-stage builds  
- Use smaller base images (Alpine)  
- Avoid unnecessary packages  
- Clean caches

### 22. What is Docker Swarm?
Docker’s native container orchestration tool.

### 23. How does service scaling work in Docker Swarm?
```bash
docker service scale myservice=5
```

### 24. What is an overlay network?
A multi-host network used in Swarm or Kubernetes.

### 25. What are Docker secrets?
Secure storage of sensitive data (passwords, tokens).

### 26. What are Docker configs?
Stores non-sensitive configuration files.

### 27. How does Docker handle resource limits?
Using `--cpus` and `--memory`.

### 28. What is the difference between Docker compose and Docker swarm?
- Compose → Multi-container apps  
- Swarm → Orchestration

### 29. How does Docker ensure isolation?
Using Linux kernel features: namespaces + cgroups.

### 30. What is a dangling image?
An unused image without a tag.

---

# 🧠 4. Scenario-Based Questions (Most asked in interviews)

### 31. App runs locally but fails inside Docker — how do you debug?
- Check logs  
- Attach interactive shell  
- Compare environment  
- Check Dockerfile base image

### 32. Container restarts repeatedly — what do you check?
- Entry command  
- Crash logs  
- Healthchecks  
- Resource limits

### 33. Your image size is 2GB — how do you reduce it?
- Use Alpine  
- Multi-stage builds  
- Remove caches  
- `.dockerignore` file

### 34. Container cannot access the internet — what’s wrong?
- DNS issue  
- Wrong network mode  
- Firewall rules

### 35. Two containers need to communicate — how?
- Create user-defined bridge network  
```bash
docker network create mynet
```

### 36. How to persist database data in Docker?
Use volumes  
```bash
docker volume create dbdata
```

### 37. Container is using high CPU — what do you do?
- Use `docker stats`  
- Apply limits (`--cpus`, `--memory`)  

### 38. Deployment should not stop during update — how?
- Use rolling updates  
- Use Swarm/K8s  
- Tag images properly

### 39. API works on localhost but not from browser?
- Expose ports  
- Use `-p` flag  
- Check firewall

### 40. How do you secure a Docker environment?
- Use non-root user  
- Scan images  
- Limit capabilities  
- Enable secrets

---

# 🧩 5. Commands You MUST Know

```
docker build -t app .
docker run -p 8080:80 app
docker logs <id>
docker exec -it <id> sh
docker inspect <id>
docker ps -a
docker stats
docker system prune
docker network create
docker volume ls
docker compose up -d
```

---

# 📘 6. HR + Managerial Questions

### 41. Explain a Docker project you’ve worked on.  
### 42. How do you use Docker in your CI/CD pipelines?  
### 43. What’s the biggest challenge you faced with Docker?  
### 44. What monitoring tools have you used with Docker?  
### 45. Why do companies use Docker instead of VMs?

---

# 🏆 Best Practices

- Always use `.dockerignore`  
- Use small base images  
- Enable healthchecks  
- Avoid running containers as root  
- Use multi-stage builds  
- Store secrets securely  
- Regularly prune unused resources  
- Use private registries for production images  

---

# 🤝 Contribute  
You can contribute more interview questions based on real interview experience.

---

# 👨‍💻 Author  
**Aditya Jadhav**  
Beginner Cloud & DevOps Learner  

📧 **adijadhav8446@gmail.com**  
🌐 **GitHub Profile:** https://github.com/AdiJadhav1608  
🔗 **LinkedIn:** https://www.linkedin.com/in/aditya-jadhav-718087339/  

⭐ *If these interview questions helped you, give it a star and keep preparing!*  
