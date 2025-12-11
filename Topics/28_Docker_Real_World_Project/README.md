# 🚀 Real-World Docker Project – Full Stack Application Deployment

This project demonstrates how to **containerize and deploy a real-world full-stack application** using Docker.  
The stack includes:

- **Frontend** (React / HTML / Vue / Angular)
- **Backend** (Node.js / Python / Java / Go)
- **Database** (MySQL / MongoDB / PostgreSQL)
- **Reverse Proxy** (Nginx)
- **Docker Compose for Orchestration**

It is designed to help beginners understand how real companies use Docker in production.

---

# 📂 Project Structure

```
28_Docker_Real_World_Project/
├── docker-compose.yml
├── frontend/
│   ├── Dockerfile
│   ├── src/
│   └── package.json
├── backend/
│   ├── Dockerfile
│   ├── app/
│   └── requirements.txt
├── nginx/
│   └── nginx.conf
├── db/
│   └── init.sql
└── README.md
```

---

# 🧱 **1. Overview**

This project simulates a real production-level environment:

- **Frontend** served using NGINX  
- **Backend API** containerized and accessible via environment vars  
- **Database** with persistent volume  
- **Reverse Proxy** for routing traffic  
- **Docker Compose** to start everything together  
- **Networking** through custom Docker networks  

---

# ⚙️ **2. Services Explanation**

### ✅ **Frontend (React Example)**
- Built using a multi-stage Dockerfile  
- First stage builds the frontend  
- Second stage serves it using **NGINX**

### ✅ **Backend (Flask / Node example)**
- API container  
- Communicates with database through internal Docker network  
- Environment variables for DB host, user, password

### ✅ **Database (MySQL Example)**
- Uses a Docker volume  
- Initializes tables automatically using `init.sql`

### ✅ **Nginx Reverse Proxy**
- Routes incoming traffic → frontend → backend  
- Used in 90% of real projects for load balancing, caching, SSL termination

---

# 🛠️ **3. How to Run the Project**

### Step 1 — Clone the repository  
```bash
git clone https://github.com/AdiJadhav1608/28_Docker_Real_World_Project.git
cd 28_Docker_Real_World_Project
```

### Step 2 — Start all services  
```bash
docker compose up --build
```

### Step 3 — Access application  
- Frontend → http://localhost  
- Backend API → http://localhost/api  
- Database → internal-only container service

### Step 4 — Stop  
```bash
docker compose down
```

---

# 🧪 **4. Testing API**

Example:
```bash
curl http://localhost/api/health
```

---

# 📦 **5. Docker Compose Example**

```yaml
version: '3.9'

services:
  frontend:
    build: ./frontend
    ports:
      - "80:80"
    depends_on:
      - backend

  backend:
    build: ./backend
    environment:
      DB_HOST: db
      DB_USER: root
      DB_PASS: password
    ports:
      - "5000:5000"
    depends_on:
      - db

  db:
    image: mysql:8
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: password
    volumes:
      - db_data:/var/lib/mysql
      - ./db/init.sql:/docker-entrypoint-initdb.d/init.sql

volumes:
  db_data:
```

---

# 🔐 **6. Real-World Features You Can Add**
- JWT authentication  
- HTTPS reverse proxy  
- Logging with EFK stack  
- Prometheus + Grafana monitoring  
- CI/CD using GitHub Actions  

---

# 🏆 Best Practices

- Use multi-stage builds to reduce image size  
- Store secrets using env files / secret managers  
- Use volume for database persistence  
- Implement healthchecks for all services  
- Tag images with version numbers (NOT latest)  

---

# 🤝 Contribute  
Feel free to improve this project by adding more services, production setups, monitoring, or better folder structure.

---

# 👨‍💻 Author  
**Aditya Jadhav**  
Beginner Cloud & DevOps Learner  

📧 **adijadhav8446@gmail.com**  
🌐 **GitHub Profile:** https://github.com/AdiJadhav1608  
🔗 **LinkedIn:** https://www.linkedin.com/in/aditya-jadhav-718087339/  

⭐ *If you found this helpful, don't forget to give it a star!*
