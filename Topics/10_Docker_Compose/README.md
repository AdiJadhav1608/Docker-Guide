# 🐳 Docker Compose — Multi-Container Management

Docker Compose is a tool that allows you to **define and run multi-container applications** using a single YAML file.  
It simplifies managing services like databases, backend, frontend, and more.

---

## 📌 Why Use Docker Compose?

- Manage **multiple containers** easily  
- Define complete app setup in **docker-compose.yml**  
- Start everything with **one command**  
- Simplify development environment setup  
- Share configuration across team members  

---

## 📁 docker-compose.yml Example (Basic)

```
version: "3.9"
services:
  web:
    image: nginx
    ports:
      - "8080:80"
```

Run:
```
docker compose up -d
```

---

## 🏗 Common Docker Compose Commands

### ▶️ Start services
```
docker compose up
```

### ▶️ Start in background
```
docker compose up -d
```

### ⛔ Stop services
```
docker compose down
```

### 🧱 List running containers
```
docker compose ps
```

### 🔄 Rebuild images
```
docker compose build
```

---

## 🌐 Multi-Service Example (Web + Database)

```
version: "3.9"
services:
  app:
    build: .
    ports:
      - "5000:5000"
    depends_on:
      - db

  db:
    image: mysql:8
    environment:
      MYSQL_ROOT_PASSWORD: root
    volumes:
      - dbdata:/var/lib/mysql

volumes:
  dbdata:
```

Run everything:
```
docker compose up -d
```

---

## 🧪 Check Logs

```
docker compose logs -f
```

---

## 📦 Remove Containers, Images, Volumes

```
docker compose down --rmi all --volumes
```

---

## 🔧 Useful Features

### Environment Variables
```
env_file:
  - .env
```

### Named Volumes
```
volumes:
  data:
```

### Networks
```
networks:
  mynet:
    driver: bridge
```

---

## 🏆 Best Practices

- Keep services small and modular  
- Use `.env` files for secrets  
- Avoid hardcoding passwords  
- Use named volumes for data persistence  
- Keep one app per Compose file for clarity  

---

## 🤝 Contribute  
Contributions are welcome! Add examples, improve explanations, or enhance structure.

---

## 👨‍💻 Author  
**Aditya Jadhav**  
Beginner Cloud & DevOps Learner  

📧 **adijadhav8446@gmail.com**  
🌐 **GitHub Profile:** https://github.com/AdiJadhav1608  
🔗 **LinkedIn:** https://www.linkedin.com/in/aditya-jadhav-718087339/  

⭐ *If you found this helpful, give it a star and keep learning Docker!*  
