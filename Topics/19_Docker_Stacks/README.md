# 19_Docker_Stacks

## 📌 Introduction
**Docker Stacks** allow you to deploy **multi-service applications** in a Docker Swarm using a single `docker-compose.yml` file.  
Stacks are the Swarm-level equivalent of running `docker compose up`, but with **scaling**, **load balancing**, **service discovery**, and **rolling updates** included.

---

## 📁 What Is a Stack?
A **stack** = a collection of **services**, **networks**, and **volumes** defined inside a Compose file and deployed to a Swarm.

Example folder:
```
myapp/
 ├── docker-compose.yml
```

Deploy:
```
docker stack deploy -c docker-compose.yml myapp
```

---

## 📌 Key Features of Docker Stacks
✔ Deploy full applications with one command  
✔ Automatically creates services, networks, and volumes  
✔ Built-in load balancing between replicas  
✔ Rolling updates supported  
✔ Self-healing (Swarm replaces failed tasks)

---

## 📌 Example Stack File (docker-compose.yml)
```yaml
version: "3.9"

services:
  web:
    image: nginx:latest
    ports:
      - "80:80"
    deploy:
      replicas: 3
      restart_policy:
        condition: on-failure
      update_config:
        parallelism: 1
        delay: 5s

  app:
    image: myapp:latest
    deploy:
      replicas: 2

  redis:
    image: redis:alpine
    deploy:
      mode: global

networks:
  default:
    driver: overlay
```

---

## 📌 Deploying a Stack
```
docker stack deploy -c docker-compose.yml mystack
```

List stacks:
```
docker stack ls
```

List services in a stack:
```
docker stack services mystack
```

Check tasks:
```
docker stack ps mystack
```

---

## 📌 Updating a Stack
Modify `docker-compose.yml` and run:
```
docker stack deploy -c docker-compose.yml mystack
```
Swarm performs **rolling updates** automatically.

---

## 📌 Removing a Stack
```
docker stack rm mystack
```

---

## 📌 Stack Networking
Stacks use **overlay networks**, enabling:
- Multi-node communication  
- Internal DNS  
- Encrypted traffic (optional)

---

## 📌 Stacks vs Docker Compose
| Feature | Docker Compose | Docker Stacks |
|--------|----------------|----------------|
| Runs on | Single machine | Swarm cluster |
| Scalability | Manual | Automatic |
| Load balancing | ❌ | ✔ |
| High availability | ❌ | ✔ |
| Rolling updates | ❌ | ✔ |
| Service discovery | Basic | Advanced |

---

## 🏆 Best Practices
- Use version **3.8+** Compose files for stacks  
- Include resource limits under `deploy:`  
- Always define overlay networks for multi-service apps  
- Use secrets/configs for sensitive and environment data  
- Keep images lightweight for faster updates  

---

## 🤝 Contribute  
Add your stack examples, real-world deployments, or learning notes to help others.

---

## 👨‍💻 Author  
**Aditya Jadhav**  
Beginner Cloud & DevOps Learner  

📧 **adijadhav8446@gmail.com**  
🌐 **GitHub Profile:** https://github.com/AdiJadhav1608  
🔗 **LinkedIn:** https://www.linkedin.com/in/aditya-jadhav-718087339/

⭐ *If you found this helpful, give it a star and keep learning Docker!*
