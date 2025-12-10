# 26_Docker_Build_Strategies (Multi-stage Builds)

## 📌 Introduction
Docker build strategies help optimize image size, performance, and security.  
The most powerful approach is **Multi-stage Builds**, which reduce unnecessary files and dependencies in the final image.

---

## 🧱 What Are Multi-Stage Builds?
Multi-stage builds allow you to use **multiple FROM statements** in a single Dockerfile, copying only what’s needed into the final image.

✔ Reduces image size  
✔ Removes build tools from final image  
✔ Improves security  
✔ Faster deployments  

---

## 🎯 Example: Multi-stage Build (Node.js)
```
# Stage 1: Build
FROM node:18 AS build
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

# Stage 2: Production
FROM nginx:latest
COPY --from=build /app/dist /usr/share/nginx/html
```

**Output:**  
Only the compiled app is included — no Node.js or npm in final image!

---

## 🎯 Multi-stage Build (Go Application)
```
FROM golang:1.20 AS builder
WORKDIR /src
COPY . .
RUN go build -o app

FROM alpine:latest
COPY --from=builder /src/app /app
CMD ["/app"]
```

Image size becomes **10MB instead of 900MB**.

---

## 🧰 Build Arguments for Flexibility
```
ARG NODE_VERSION=18
FROM node:${NODE_VERSION}
```

Build with:
```
docker build --build-arg NODE_VERSION=20 .
```

---

## 🚀 Using .dockerignore
Improve build performance by excluding unnecessary files:

```
node_modules
.git
*.log
.env
dist
```

---

## 📦 Caching Strategies
### 1. Install dependencies before copying source:
```
COPY package*.json ./
RUN npm install
COPY . .
```

### 2. Use BuildKit for fast caching:
```
DOCKER_BUILDKIT=1 docker build .
```

---

## 📊 Build Stages Naming
```
FROM python:3.10 AS deps
FROM python:3.10 AS runtime
```

Helps readability and debugging.

---

## 🏆 Best Practices
- Always use multi-stage builds for production  
- Use minimal base images (Alpine, Distroless)  
- Add `.dockerignore` to speed up builds  
- Use BuildKit to optimize caching  
- Never store secrets in Docker images  

---

## 🤝 Contribute  
Add more build examples or optimized Dockerfiles for real-world applications.

---

## 👨‍💻 Author  
**Aditya Jadhav**  
Beginner Cloud & DevOps Learner  

📧 **adijadhav8446@gmail.com**  
🌐 **GitHub Profile:** https://github.com/AdiJadhav1608  
🔗 **LinkedIn:** https://www.linkedin.com/in/aditya-jadhav-718087339/

⭐ *If you found this helpful, give it a star and keep learning Docker!*
