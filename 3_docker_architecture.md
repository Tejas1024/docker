# 3_docker_architecture.md

# 🐳 Docker – Part 3: Introduction & Architecture

---

## 🔹 What is Docker?

Docker is an open-source platform to **build, ship, and run applications in lightweight containers**.  
Ensures applications run the same everywhere (local, test, cloud).

---

## 🕓 History of Docker

| Year    | Event                                                  |
|---------|--------------------------------------------------------|
| 2013    | Docker launched as open-source by Solomon Hykes        |
| 2014    | Renamed Docker Inc.; rapidly gained popularity         |
| 2015–17 | Became essential for DevOps pipelines                  |
| Now     | Standard on AWS, Azure, GCP, etc.                      |

---

## ⚙️ Features of Docker

- 🧳 Portability
- ⚡ Lightweight (shares host OS kernel)
- 📦 Image-based deployment
- 🔁 Reusability
- 🔍 Version control (tags)
- 🔄 Isolation (runs independently)
- 🛠️ Free and open-source

---

## 🧱 Docker Architecture Overview

**Follows client-server model:**

+----------------------+
| Docker Client | (CLI / Docker Desktop)
+----------------------+
|
v
+----------------------+
| Docker Daemon | (Server/Engine)
+----------------------+
|
v
+----------------------+
| Docker Registry | (e.g., Docker Hub)
+----------------------+

 

---

## 🧩 Main Components

### 1️⃣ Docker Client (CLI)
- Interact with Docker via commands
- Sends commands to Docker Daemon
- Example:  
  - `docker build .`
  - `docker run -it ubuntu`
  - `docker ps`

### 2️⃣ Docker Daemon (Engine)
- Core service that builds, runs, and manages containers/images/networks
- Handles requests from Docker Client

### 3️⃣ Docker Registry
- **Public:** Docker Hub
- **Private:** for internal images
- **Push:** `docker push imagename`
- **Pull:** `docker pull imagename`

---

## 🧠 Docker Images and Container Flow

1. Write a **Dockerfile** → defines build steps
2. Build image: `docker build -t appname .`
3. Run container: `docker run appname`
4. **Lifecycle:**  
   Dockerfile → Docker Image → Docker Container

---

## 🏗️ Types of Images

- **Pre-built:** From Docker Hub (`docker pull nginx`)
- **Customized:** Via your own Dockerfile

---

## ⚙️ Summary Table

| Component           | Description                 | Example             |
|---------------------|----------------------------|---------------------|
| Docker Client (CLI) | Interface for commands      | docker build, run   |
| Docker Daemon       | Core server/service         | Runs containers     |
| Docker Registry     | Image storage               | Docker Hub          |
| Docker Image        | Template/blueprint          | nginx, myapp:v1     |
| Docker Container    | Running instance            | Actual app running  |

---

## ✅ In short:  
Developer builds image → pushes to registry → pulls & runs as container anywhere