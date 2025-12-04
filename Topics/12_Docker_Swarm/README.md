# 🐳 Docker Swarm — Container Orchestration Made Simple

Docker Swarm is Docker’s native **container orchestration tool**.  
It allows you to manage a cluster of Docker nodes as a **single virtual system**.

---

## 📌 Why Docker Swarm?

- Built-in Docker orchestration  
- Easy to set up compared to Kubernetes  
- High availability  
- Load balancing  
- Rolling updates  
- Scales services automatically  

---

## 🏗 Key Concepts

### 🔹 Node  
A machine in the Swarm cluster.  
**Manager Node** → Controls cluster  
**Worker Node** → Runs tasks

### 🔹 Service  
Definition of a task (like an app). Runs across multiple nodes.

### 🔹 Task  
Container instance in Swarm.

### 🔹 Stack  
Group of services defined using `docker-stack.yml`.

---

## 🚀 Initialize a Swarm Cluster

```
docker swarm init
```

To add workers:
```
docker swarm join-token worker
```

---

## 📦 Deploy a Service

```
docker service create --name web -p 80:80 nginx
```

List services:
```
docker service ls
```

Check service details:
```
docker service ps web
```

---

## 🔄 Scale a Service

Increase replicas:
```
docker service scale web=5
```

---

## 🔁 Update a Service (Rolling Update)

```
docker service update --image nginx:latest web
```

---

## 🛑 Remove a Service

```
docker service rm web
```

---

## 🌐 Deploy a Stack

Create `docker-stack.yml`:

```
version: "3.9"
services:
  web:
    image: nginx
    ports:
      - "8080:80"
    deploy:
      replicas: 3
```

Deploy:
```
docker stack deploy -c docker-stack.yml mystack
```

List all stacks:
```
docker stack ls
```

Remove stack:
```
docker stack rm mystack
```

---

## 🕸 Networking in Swarm

Swarm uses **overlay networks**:

```
docker network create -d overlay mynet
```

---

## 🏆 Best Use Cases

- Lightweight orchestration  
- Small to medium clusters  
- Simple microservices setup  
- Demo or learning environment  
- Edge computing  

---

## 🤝 Contribute  
Your contributions are always welcome! Add examples, diagrams, or production tips.

---

## 👨‍💻 Author  
**Aditya Jadhav**  
Beginner Cloud & DevOps Learner  

📧 **adijadhav8446@gmail.com**  
🌐 **GitHub Profile:** https://github.com/AdiJadhav1608  
🔗 **LinkedIn:** https://www.linkedin.com/in/aditya-jadhav-718087339/  

⭐ *If you found this helpful, give it a star and keep learning Docker!*  
