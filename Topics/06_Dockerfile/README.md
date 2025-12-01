# 🐳 Dockerfile — Complete Beginner Guide

A **Dockerfile** is a text file that contains instructions to build a Docker image.  
It automates the image creation process so you can package applications consistently.

---

## 📌 What is a Dockerfile?

A Dockerfile tells Docker **how to build an image** step-by-step.

Each instruction creates a new layer in the image.

Example:
```
FROM ubuntu:latest
RUN apt-get update
CMD ["echo", "Hello from Dockerfile"]
```

---

## 📚 Common Dockerfile Instructions

### 1️⃣ **FROM**
Sets the base image.
```
FROM python:3.10
```

### 2️⃣ **WORKDIR**
Sets the working directory inside the container.
```
WORKDIR /app
```

### 3️⃣ **COPY**
Copies files from your machine to the image.
```
COPY . /app
```

### 4️⃣ **RUN**
Executes commands during build.
```
RUN pip install -r requirements.txt
```

### 5️⃣ **CMD**
Runs a command when the container starts.
```
CMD ["python", "app.py"]
```

### 6️⃣ **EXPOSE**
Defines the port your container listens on.
```
EXPOSE 8080
```

### 7️⃣ **ENV**
Defines environment variables.
```
ENV APP_ENV=production
```

---

## 📦 Example: Python App Dockerfile

```
FROM python:3.10-slim
WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt
COPY . .
EXPOSE 5000
CMD ["python", "app.py"]
```

---

## 🚀 Build & Run

### Build image
```
docker build -t myapp .
```

### Run container
```
docker run -p 5000:5000 myapp
```

---

## 🤝 Contribute  
Feel free to **contribute**, improve examples, or submit meaningful PRs.

---

## 👨‍💻 Author  
**Aditya Jadhav**  
Beginner Cloud & DevOps Learner  

📧 **adijadhav8446@gmail.com**  
🌐 **GitHub Profile:** https://github.com/AdiJadhav1608
🔗 **LinkedIn:** https://www.linkedin.com/in/aditya-jadhav-718087339/

---

⭐ *If you found this helpful, give it a star and keep learning Docker!*  
