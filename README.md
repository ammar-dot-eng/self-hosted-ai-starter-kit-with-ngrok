# 🚀 Self-Hosted AI Starter Kit (with Ngrok)

*A beginner-friendly fork of the excellent original project.*

> **Forked from:** [https://github.com/DevilUpperCase/self-hosted-ai-starter-kit-with-ngrok](https://github.com/DevilUpperCase/self-hosted-ai-starter-kit-with-ngrok)
> This version includes **beginner-friendly setup instructions** and simplifies the entire process of self-hosting AI tools using Docker + Ngrok, And adds some code fixes that worked for myself. 

---

<p align="center">
  <img src="https://img.shields.io/badge/Status-Stable-brightgreen?style=for-the-badge">
  <img src="https://img.shields.io/badge/Docker-Ready-blue?style=for-the-badge&logo=docker">
  <img src="https://img.shields.io/badge/n8n-Automation-orange?style=for-the-badge&logo=n8n">
  <img src="https://img.shields.io/badge/Ngrok-Tunneling-purple?style=for-the-badge&logo=ngrok">
</p>

---

# 📦 What You Get

* 🌐 Publicly accessible **n8n automation service** via Ngrok
* ⚡ GPU-accelerated support for AMD & NVIDIA
* 🐳 Fully containerized setup using Docker
* 🧠 Integrated Qdrant vector database
* 🧩 Zero manual server configuration
* 🎯 Perfect for LLM workflows, agents, pipelines, automations

---

# 🛠 1. Install Docker Desktop

## **Option A — Install Docker on the `D:` drive (advanced users)**

1. Create a new folder anywhere on your `D:` drive.
2. Download **Docker Desktop Installer.exe** from:
   [https://www.docker.com/products/docker-desktop/](https://www.docker.com/products/docker-desktop/)
   Place it in that folder.
3. Copy the folder path.
4. Open **Command Prompt as Administrator**.
5. Run:

```cmd
cd your-folder-path
```

Then run the installer:

```cmd
start /w "" "Docker Desktop Installer.exe" install -accept-license --installation-dir="D:\Docker\Docker" --wsl-default-data-root="D:\Docker\wsl" --windows-containers-default-data-root="D:\\Docker"
```

✔ Docker will now install entirely on `D:\`
✔ Shortcut will appear on your desktop

---

## **Option B — Install normally on `C:` (recommended for beginners)**

Just download **Docker Desktop Installer.exe**, run it, and follow the prompts.

---

# 🌍 2. Create an Ngrok Account

Go to **[https://ngrok.com/](https://ngrok.com/)** and make an account.
You'll need your **static domain** and **authtoken** later.

---

# 📥 3. Clone or Download the Repository

## **Option A — If you have Git installed**

Right-click your desktop → **Open Command Prompt**
Then run:

```bash
git clone https://github.com/ammar-dot-eng/self-hosted-ai-starter-kit-with-ngrok.git
```

---

## **Option B — No Git?**

Just download the ZIP from GitHub → extract it → place the folder anywhere you like (Desktop recommended).

---

# 🔐 4. Configure Environment Variables (`.env`)

1. Go to your Ngrok dashboard → **Domains**
2. Copy your static domain
3. Open the `.env` file in Notepad

Find the section below:

```env
# n8n Webhook Configuration
N8N_WEBHOOK_URL=https://your-ngrok-host
N8N_PROTOCOL=https
N8N_HOST=your-ngrok-host

# It should be just the hostname without any scheme.
N8N_WEBHOOK_HOST=your-ngrok-host
```

Replace **every occurrence** of `your-ngrok-host` with your actual Ngrok domain.

💾 Save the file.

---

# 🛡 5. Configure Ngrok (`ngrok.yml`)

Open `ngrok.yml` in Notepad.

Find:

```yaml
tunnels:
  custom-domain-tunnel:
    proto: http
    addr: n8n:5678  
    hostname: your-ngrok-domain.ngrok-free.app
```

Replace `your-ngrok-domain.ngrok-free.app` with your static domain.

Next, get your **Ngrok authtoken**:
Ngrok Dashboard → **Your Authtoken**

Replace in the file:

```yaml
authtoken: your-ngrok-authtoken
```

✔ Keep exactly **one space** after the colon.
💾 Save the file.

---

# 🧰 6. Start the System Using Docker Compose

Open the repo folder → right-click an empty area → **Open in Terminal**.

Choose ONE of the following:

---

### 🟥 **A) AMD GPU Users**

```bash
docker compose --profile gpu-amd up
```

---

### 🟦 **B) NVIDIA GPU Users**

```bash
docker compose --profile gpu-nvidia up
```

---

### 🟩 **C) CPU-only Users**

```bash
docker compose --profile cpu up
```

Let everything run until all services are fully up.

---

# 🌐 7. Access Your Services

| Service               | URL                                                                                  |
| --------------------- | ------------------------------------------------------------------------------------ |
| **n8n Automation UI** | [http://localhost:5678/](http://localhost:5678/)                                     |
| **Qdrant Vector DB**  | [http://localhost:6333/dashboard#/welcome](http://localhost:6333/dashboard#/welcome) |

You can also open Docker Desktop to monitor your containers.

---

# 🎉 You're Done!

Your self-hosted AI workflow environment is now live and publicly accessible through Ngrok.
You can now begin building automations, agent pipelines, or AI workflows in n8n.

---