# ⚙️ Installing Docker

Docker can be installed on **Windows**, **Linux**, and **macOS**.  
Below are the simplest and most widely used installation steps for all platforms.

---

## 🪟 Install Docker on Windows

### ✔ Requirements
- Windows 10/11 (64-bit)
- WSL 2 enabled

### ✔ Steps
1. Download Docker Desktop:  
   https://www.docker.com/products/docker-desktop
2. Install the application.
3. Enable **WSL 2 backend** during installation.
4. Start Docker Desktop.
5. Run the command to verify installation:
   ```bash
   docker --version
   ```

---

## 🐧 Install Docker on Linux (Ubuntu)

### ✔ Commands
```bash
sudo apt update
sudo apt install ca-certificates curl gnupg

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker.gpg

echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker.gpg] \
  https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" \
  | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io
```

### ✔ Verify
```bash
docker --version
```

---

## 🍎 Install Docker on macOS

### ✔ Steps
1. Download Docker Desktop for macOS:  
   https://www.docker.com/products/docker-desktop
2. Install using `.dmg` file.
3. Start Docker Desktop.
4. Verify installation:
   ```bash
   docker --version
   ```

---

## 🧪 Test Your Docker Installation

Run your first container:

```bash
docker run hello-world
```

If you see a success message → Docker is installed correctly.

---

## 🤝 Contribute

Have suggestions or want to improve something?  
Feel free to open an **issue** or submit a **pull request**.

---

## 👨‍💻 Author

**Aditya Jadhav**  
Beginner Cloud & DevOps Learner  

📧 **adijadhav8446@gmail.com**  
🌐 **GitHub Profile:** https://github.com/AdiJadhav1608
🔗 **LinkedIn:** https://www.linkedin.com/in/aditya-jadhav-718087339/

---

⭐ *If you found this helpful, give it a star and keep learning Docker like a pro!*  
