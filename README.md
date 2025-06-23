# Enterprise-grade-chatgpt
This is a repo for Entireprise grade local llm model in combination with openwebui for a chatgpt like experience.
# 🧠 OpenWebUI + Ollama Setup Script (Windows + Docker)

This repository contains a simple PowerShell script to install and run **OpenWebUI** with **Ollama** locally on a **Windows PC** using Docker.

> ✅ No cloud required  
> ✅ No API keys  
> ✅ 100% local AI chatbot with LLaMA3 (or your model of choice)

---

## 🚀 What You Get

- **Ollama** – a local backend that runs open-source LLMs like LLaMA3, Mistral, Gemma, etc.
- **OpenWebUI** – a beautiful, ChatGPT-style frontend to chat with your models
- **Docker Compose setup** – zero manual config needed

---

## 📂 Files Included

- `setup-openwebui-ollama.ps1` – PowerShell script that:
  - Creates the project folder
  - Writes a Docker Compose file
  - Pulls and runs containers
  - Downloads and runs LLaMA3 model
- `docker-compose.yml` – created automatically by the script

---

## 🧰 Prerequisites

- [Docker Desktop](https://www.docker.com/products/docker-desktop/) installed and running
- Windows 10/11 with PowerShell
- Git (optional, for cloning this repo)

---

## 🛠️ How to Use

### Option 1: Run Script from Git Clone

```powershell
git clone https://github.com/YOUR-USERNAME/openwebui-ollama-setup.git
cd openwebui-ollama-setup
.\setup-openwebui-ollama.ps1
