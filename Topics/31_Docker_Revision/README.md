# 🌀 31_Docker_Revision  
A complete **end-to-end Docker revision guide**, summarizing all concepts from basics to advanced, including images, containers, volumes, networking, Compose, Swarm, security, CI/CD, optimization, and real-world usage.

---

# 📚 1. What is Docker?

Docker is a platform used to build, ship, and run applications inside **containers** — lightweight, isolated environments that run consistently across systems.

---

# 📦 2. Docker Components Overview

```
Docker Engine
 ├── Docker CLI
 ├── Docker API
 ├── Docker Daemon
 └── Container Runtime (runc)
```

---

# 🖼️ 3. Docker Images

- Read-only templates  
- Built using Dockerfile  
- Stored in registries  
- Layers + Union FS  
- Commands:
  ```bash
  docker build -t myapp .
  docker pull nginx
  docker images
  ```

---

# 📌 4. Docker Containers

- Running instances of images  
- Lightweight + isolated  
- Commands:
  ```bash
  docker run -d -p 8080:80 nginx
  docker stop <id>
  docker rm <id>
  docker logs <id>
  docker exec -it <id> sh
  ```

---

# 🧱 5. Dockerfile Revision

Most common Dockerfile instructions:

```
FROM  
RUN  
COPY  
ADD  
WORKDIR  
EXPOSE  
ENV  
CMD  
ENTRYPOINT  
```

**Multi-stage Build Example**

```dockerfile
FROM node:16 AS builder
WORKDIR /app
COPY . .
RUN npm install && npm run build

FROM nginx
COPY --from=builder /app/dist /usr/share/nginx/html
```

---

# 🗄️ 6. Volumes & Storage

### Types:
- **Volumes** – Docker-managed  
- **Bind Mounts** – Host path  
- **tmpfs** – In-memory  

### Commands:
```bash
docker volume create data
docker volume ls
docker run -v data:/var/lib/mysql mysql
```

---

# 🌐 7. Networking Revision

### Types:
- bridge  
- host  
- none  
- overlay  

### Commands:
```bash
docker network create mynet
docker network ls
docker network inspect mynet
```

---

# 🧩 8. Docker Compose

**Compose YAML Example**
```yaml
version: "3"
services:
  web:
    image: nginx
    ports:
      - "8080:80"
  db:
    image: mysql
    environment:
      MYSQL_ROOT_PASSWORD: root
```

Commands:

```bash
docker compose up -d
docker compose down
docker compose logs
docker compose ps
```

---

# 🐳 9. Docker Swarm Revision

### Key Features  
- Multi-host orchestration  
- Services instead of containers  
- Overlay networking  
- Scaling  

Commands:
```bash
docker swarm init
docker service create --name web -p 80:80 nginx
docker service scale web=5
docker stack deploy -c stack.yml mystack
```

---

# 🔐 10. Docker Security

- Use **non-root** users  
- Scan images for vulnerabilities  
- Use Docker Secrets  
- Limit capabilities  
- Apply resource limits  

---

# 🚦 11. Healthchecks

```dockerfile
HEALTHCHECK CMD curl -f http://localhost/ || exit 1
```

Check status:

```bash
docker inspect --format='{{.State.Health.Status}}' <id>
```

---

# 📊 12. Monitoring Tools

- **cAdvisor**  
- **Prometheus**  
- **Grafana**  
- `docker stats`  

---

# ⚙️ 13. CI/CD With Docker

### Steps:
1. Build image  
2. Tag image  
3. Push to registry  
4. Deploy using Compose/Swarm/K8s  

Example:
```bash
docker build -t myapp:v1 .
docker tag myapp:v1 myrepo/myapp:v1
docker push myrepo/myapp:v1
```

---

# 🚀 14. Image Optimization Revision

- Use multi-stage builds  
- Use .dockerignore  
- Smaller base images  
- Combine RUN commands  
- Use BuildKit  
- Cache dependency layers  

---

# 🧠 15. Most Important Commands (Must Remember)

```
docker ps -a
docker images
docker run -d -p 8080:80 nginx
docker stop/start/restart
docker exec -it <id> bash
docker logs <id>
docker rm -f <id>
docker rmi <image>
docker network create
docker volume ls
docker compose up
docker system prune
```

---

# 🏁 Quick Revision Checklist

| Topic | Completed |
|-------|-----------|
| Docker Basics | ✅ |
| Images | ✅ |
| Containers | ✅ |
| Dockerfile | ✅ |
| Volumes | ✅ |
| Networks | ✅ |
| Compose | ✅ |
| Swarm | ✅ |
| Security | ✅ |
| Healthchecks | ✅ |
| Monitoring | ✅ |
| CI/CD | ✅ |
| Optimization | ✅ |
| Interview Prep | ✅ |
| Real-World Usage | ✅ |

---

# 🤝 Contribute  
Add more commands, diagrams, or revision notes to help learners revise Docker faster.

---

# 👨‍💻 Author  
**Aditya Jadhav**  
Beginner Cloud & DevOps Learner  

📧 **adijadhav8446@gmail.com**  
🌐 **GitHub Profile:** https://github.com/AdiJadhav1608  
🔗 **LinkedIn:** https://www.linkedin.com/in/aditya-jadhav-718087339/  

⭐ *If you found this helpful, give it a star and keep learning Docker!*
