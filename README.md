⚠️ Deprecated — This repository has been retired. The AI apps now run separately in the new repository: metet/blackwell-comfy-docker. For migration notes and continuing development please see that repo.

# 🚀 Docker AI Stack: Ollama + Open WebUI + ComfyUI (RTX 5080 / Ubuntu)

A Docker-based AI stack that runs **Ollama**, **Open WebUI**, and **ComfyUI** together with full NVIDIA GPU acceleration.

This setup is optimized for **Ubuntu** and **NVIDIA GeForce RTX 5080 (sm_120)** using CUDA-enabled PyTorch nightly builds.

Repository:
https://github.com/metet/ComfyUI_Ollama_OpenWebUI_Geforce_5080

---

## 🧠 Overview

This project provides a local, self-hosted AI environment using Docker Compose:

- **Ollama** – Local LLM runtime and model server  
- **Open WebUI** – Web interface for chatting with Ollama models  
- **ComfyUI** – Node-based Stable Diffusion / image generation workflow UI  

Each service runs in its own container but is networked together.

---

## 🧩 Architecture

```

ComfyUI_Ollama_OpenWebUI_Geforce_5080/
├── docker-compose.yml
├── comfyui/
│   └── Dockerfile
├── ollama/
│   └── Dockerfile
└── README.md

````

---

## 🛠 Prerequisites

You must have the following installed on the host system:

- Docker Engine
- Docker Compose v2
- NVIDIA GPU drivers
- NVIDIA Container Toolkit

Verify GPU access:

```bash
nvidia-smi
docker run --rm --gpus all nvidia/cuda:12.6.3-base-ubuntu22.04 nvidia-smi
````

---

## 🚀 Running the Stack

Start all services:

```bash
docker compose up -d
```

---

## 🌐 Service Endpoints

| Service    | URL                                              | Description                |
| ---------- | ------------------------------------------------ | -------------------------- |
| Open WebUI | [http://localhost:3000](http://localhost:3000)   | LLM chat interface         |
| Ollama API | [http://localhost:11434](http://localhost:11434) | LLM inference server       |
| ComfyUI    | [http://localhost:8188](http://localhost:8188)   | Image generation workflows |

Ports can be changed in `docker-compose.yml`.

---

## 📁 Persistent Storage

Recommended directories on the host:

```bash
mkdir -p \
  ~/docker-data/ollama \
  ~/docker-data/open-webui \
  ~/docker-data/comfyui/models \
  ~/docker-data/comfyui/output \
  ~/docker-data/comfyui/input \
  ~/docker-data/comfyui/custom_nodes
```

These paths are mounted as Docker volumes to persist models, outputs, and configuration.

---

## 🎮 GPU Notes (RTX 50xx)

GeForce RTX 50xx GPUs require:

* Recent NVIDIA drivers
* CUDA 12.6+
* PyTorch nightly builds compiled for `sm_120`

This repository already includes the correct CUDA/PyTorch setup inside the Docker images.

---

## 🧩 Included Services

### Ollama

* Runs local LLM models
* Serves inference API on port `11434`

### Open WebUI

* Browser-based UI for Ollama
* Supports multi-model chats and tools

### ComfyUI

* Node-based image generation
* GPU accelerated
* Supports custom nodes and workflows

---

## 🔄 Updating / Rebuilding

After modifying Dockerfiles or configuration:

```bash
docker compose build
docker compose up -d
```

---

## 🧪 Customization Ideas

* Add custom ComfyUI nodes
* Mount additional model directories
* Extend the stack with other AI services
* Adjust GPU or memory limits per container

---

## 📜 License

This repository aggregates multiple open-source projects.
Please refer to each individual project for licensing details.

---

## ❤️ Contributions

Pull requests and issues are welcome.

If you adapt this setup for other GPUs, drivers, or operating systems, please consider contributing back.


