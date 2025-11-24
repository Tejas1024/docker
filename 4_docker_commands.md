# 4_docker_commands.md

# 🐳 Basic Docker Commands

---

## 1️⃣ Pull an image from Docker Hub
docker pull <image-name>

Example:
docker pull nginx

 

---

## 2️⃣ Create a container from image

docker run <image-name>

 
- Runs a new container.
- Docker will pull image if missing locally.

**Interactive mode:**  
docker run -it ubuntu

 
- `-i` keeps input open.
- `-t` allocates a terminal.

**Detached mode:**  
docker run -d --name nginx-con1 nginx

 
- `-d` = detached (background)
- `--name` sets container name

---

## 3️⃣ List images

docker images

 

---

## 4️⃣ List running containers

docker ps

 

## 5️⃣ List all containers (running + stopped)

docker ps -a

 

---

## 6️⃣ Start a stopped container

docker start <container-name>

 

---

## 7️⃣ Stop a running container

docker stop <container-name>

 

---

## 8️⃣ Delete stopped containers

docker rm <container-name>

 
*Must be stopped before deleting*

---

## 9️⃣ Delete images

docker rmi <image-name>

 *All related containers must be deleted first.*

---

## 🧩 Bulk Operations (Shortcuts)

- **Stop all running containers:**
docker stop $(docker ps -a -q)

 
- **Remove all stopped containers:**
docker rm $(docker ps -aq)

 
- **Remove all images:**
docker rmi $(docker images -q)

 

---

## 🚨 Final Notes

- Docker Desktop or Docker Engine must be running!
- Stopped containers must be deleted before image removal.

---

## ✅ Quick Revision Table

| Task                   | Command                      |
|------------------------|------------------------------|
| Pull image             | docker pull <image>          |
| Run container          | docker run <image>           |
| Run interactively      | docker run -it <image>       |
| Run detached           | docker run -d <image>        |
| List images            | docker images                |
| List running containers| docker ps                    |
| List all containers    | docker ps -a                 |
| Start a container      | docker start <name>          |
| Stop a container       | docker stop <name>           |
| Delete stopped container| docker rm <name>            |
| Delete image           | docker rmi <image>           |