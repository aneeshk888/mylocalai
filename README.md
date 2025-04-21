
# 🧠 Ollama AI + Ubuntu + Docker Setup Guide

Welcome to the complete guide for setting up the **Ollama AI environment** using **Ubuntu on WSL (Windows Subsystem for Linux)** with **Docker and Open Web UI**. This setup allows you to run powerful AI models like LLaMA locally with ease.

---

## 🔧 Step 1: Install Ubuntu on WSL

```bash
wsl --install
```

✅ Installs a full Ubuntu environment on Windows using WSL (Windows Subsystem for Linux).

---

## 🚀 Step 2: Install Ollama

```bash
curl -fsSL https://ollama.com/install.sh | sh
```

✅ Installs **Ollama**, a tool to run open-source LLMs like LLaMA2 locally.

---

## 🖥️ Step 3: Manage Your WSL Distros

```bash
wsl --list
wsl -d Ubuntu
```

✅ List and switch to Ubuntu from PowerShell or Windows Terminal.

---

## 🤖 Step 4: Run Ollama Models

```bash
ollama pull llama2
ollama run llama2
```

🛑 Exit with:
```
/bye
```

✅ This pulls and runs the **LLaMA2 model** directly on your system. It works offline after the first download.

---

## 📈 Step 5: Monitor GPU/CPU Usage (Optional for GPU Users)

```bash
watch -n 0.5 nvidia-smi
```

✅ Displays real-time GPU resource usage. Very useful for performance tuning.

---

## 🌐 Step 6: Install Docker & Setup Securely

### 1. Install Docker (Securely)

```bash
sudo apt-get update
sudo apt-get install ca-certificates curl gnupg
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
```

### 2. Add Docker’s Repo (Hidden Key Info)

```bash
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] \
https://download.docker.com/linux/ubuntu \
$(. /etc/os-release && echo "$VERSION_CODENAME") stable" \
| sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

✅ **Note:** Keys and repositories are pulled securely using signed keys.

---

## 🐳 Step 7: Run Web UI for Ollama (Private Host Info Masked)

```bash
sudo docker run -d --network=host \
  -v open-webui:/app/backend/data \
  -e OLLAMA_BASE_URL=http://localhost:**** \
  --name open-webui \
  --restart always \
  ghcr.io/open-webui/open-webui:main
```

✅ **Environment variables and IPs are hidden** for security. Replace `localhost:****` with your actual internal URL only if you’re self-hosting.

🛑 To stop:
```bash
sudo docker stop open-webui
```

---

## 🛠️ Optional: Developer Essentials (Security-Clean)

```bash
sudo apt install -y make build-essential libssl-dev zliblg-dev \
libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm \
libncurses5-dev libncursesw5-dev xz-utils tk-dev libffi-dev \
liblzma-dev python-openssl git
```

✅ Provides the libraries needed for compiling Python tools and other packages.

---

## 💡 Tips & Shortcuts

- 📋 Copy/Paste in Linux Terminal: `Ctrl + Shift + C / V`
- 🧠 Use GitHub Copilot for AI coding assistance
- 🧼 Clean and secure your package list:
  ```bash
  sudo apt-get clean
  sudo rm -rf /var/lib/apt/lists/*
  sudo apt-get update
  ```

---

## 📸 Screenshots

📁 Save all screenshots inside a folder called `screenshots/`

| Action | Screenshot |
|--------|------------|
| 🖥️ Ubuntu on WSL | ![Ubuntu on WSL](https://github.com/user-attachments/assets/7b333d7b-7d22-4c6d-b8d0-dfc9a2b3addd) |
| 🤖 Ollama Model Running | ![Ollama Model Running](https://github.com/user-attachments/assets/7bce30b1-370d-4fd5-a789-0fa4344a1c4b) |
| 🌐 Web UI Interface | ![Web UI Interface](https://github.com/user-attachments/assets/f290b298-eba6-4b94-b2fa-e86d956d75b5) |
| 📈 GPU Monitoring (Optional) | ![GPU Monitoring](https://github.com/user-attachments/assets/8b0c90c1-aaf6-4f72-abe9-903d0d166719) |

*Tip: Blur or hide local IP addresses and hostnames in screenshots before sharing.*

---

## ✅ Final Notes

🎉 You now have a private, secure, and local AI-powered development environment with Ollama + Docker + Open Web UI.

Keep your URLs, ports, and volume names confidential when sharing this guide in public spaces.
