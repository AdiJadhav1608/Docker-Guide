# 20_Docker_Secrets

## 📌 Introduction  
**Docker Secrets** allow you to store **sensitive data** such as passwords, API keys, certificates, and tokens securely.  
Secrets are encrypted **at rest and in transit**, and only available to services that explicitly request them.

---

## 🔐 Why Use Docker Secrets?
✔ Prevent exposing passwords in images  
✔ Secure storage & encrypted transport  
✔ Access control (only assigned services can read)  
✔ Not stored in environment variables  
✔ Suitable for production Swarm environments  

---

## 📌 Creating a Secret  
### From a file:
```
echo "mypassword" > db_pass.txt
docker secret create db_password db_pass.txt
```

### From direct input:
```
printf "mypassword" | docker secret create db_password -
```

List secrets:
```
docker secret ls
```

---

## 📌 Using Secrets in a Service
Add secrets under `deploy:` or directly in Swarm services.

### Example:
```yaml
version: "3.9"

services:
  db:
    image: mysql:latest
    environment:
      MYSQL_ROOT_PASSWORD_FILE: /run/secrets/db_password
    secrets:
      - db_password

secrets:
  db_password:
    external: true
```

Deploy:
```
docker stack deploy -c docker-compose.yml secureapp
```

---

## 📌 Accessing Secrets Inside Containers
Secrets are mounted at:
```
/run/secrets/<secret_name>
```

Example:
```
cat /run/secrets/db_password
```

---

## 📌 Removing a Secret
```
docker secret rm db_password
```

⚠ Cannot remove secrets currently used by a stack.

---

## 🏆 Best Practices
- Never store secrets in environment variables  
- Create secrets on the manager node only  
- Limit access: attach secrets **only to required services**  
- Rotate secrets regularly  
- Use separate secrets for dev, test, and prod  

---

## 🤝 Contribute  
Add more secure examples, secret-handling tips, or real-world use cases.

---

## 👨‍💻 Author  
**Aditya Jadhav**  
Beginner Cloud & DevOps Learner  

📧 **adijadhav8446@gmail.com**  
🌐 **GitHub Profile:** https://github.com/AdiJadhav1608  
🔗 **LinkedIn:** https://www.linkedin.com/in/aditya-jadhav-718087339/

⭐ *If you found this helpful, give it a star and keep learning Docker!*
