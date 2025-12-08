# 21_Docker_Config

## 📌 Introduction  
Docker **Config** is used to store and manage **non-sensitive configuration data** such as app settings, config files, environment config, and templates.  
Similar to secrets, but **for non-sensitive information**.

---

## 🎯 Why Use Docker Configs?
✔ Prevents baking config into images  
✔ Keeps config centralized and versioned  
✔ Easy updates without rebuilding images  
✔ Secure distribution through Swarm  
✔ Mounted as read-only inside containers  

---

## 📌 Creating a Config  
### From a file:
```
echo "APP_ENV=prod" > app.env
docker config create app_config app.env
```

List all configs:
```
docker config ls
```

---

## 📌 Using Configs in a Service
You can mount configs inside Swarm services.

### Example:
```yaml
version: "3.9"

services:
  web:
    image: nginx
    configs:
      - source: app_config
        target: /etc/app/app.env

configs:
  app_config:
    external: true
```

Deploy:
```
docker stack deploy -c docker-compose.yml configdemo
```

---

## 📌 Accessing Configs Inside a Container
Configs mount at:
```
/run/configs/<config_name>
```

Example:
```
cat /etc/app/app.env
```

---

## 📌 Updating a Config  
Configs **cannot be updated directly**.  
You must:

1. Create a new config  
2. Update service or stack to use the new one  
3. Remove the old config  

---

## 📌 Removing a Config
```
docker config rm app_config
```

⚠ Cannot remove configs that are currently in use.

---

## 🏆 Best Practices
- Store non-sensitive configs only  
- Keep configs small and modular  
- Use separate configs per environment  
- Do not hardcode config paths inside the app  
- Use configs + secrets together for secure apps  

---

## 🤝 Contribute  
Add examples of complex configs, template-driven configs, or real-world setups.

---

## 👨‍💻 Author  
**Aditya Jadhav**  
Beginner Cloud & DevOps Learner  

📧 **adijadhav8446@gmail.com**  
🌐 **GitHub Profile:** https://github.com/AdiJadhav1608  
🔗 **LinkedIn:** https://www.linkedin.com/in/aditya-jadhav-718087339/

⭐ *If you found this helpful, give it a star and keep learning Docker!*
