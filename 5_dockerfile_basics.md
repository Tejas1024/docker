# 5_dockerfile_basics.md

# 🐳 Dockerfile — The Blueprint of a Docker Image

A Dockerfile is a text file containing **instructions to build a Docker image automatically**.  
It works like a recipe:
- Ingredients: base image, dependencies
- Steps: commands/configs
- Output: custom Docker image

**By default, file name = Dockerfile**

---

## 🧱 Basic Dockerfile Structure

FROM ubuntu
RUN apt-get install nginx -y
RUN service nginx start

 

- `FROM`: Base image.
- `RUN`: Execute commands during build.

---

## ⚙️ Common Dockerfile Instructions

1️⃣ **FROM**  
Set base image  
FROM ubuntu

 

2️⃣ **WORKDIR**  
Set working directory inside the image  
WORKDIR /app

 

3️⃣ **COPY**  
Copy files into the image  
COPY . /usr/src/app

 

4️⃣ **RUN**  
Execute commands at build time  
RUN apt-get update && apt-get install -y python3

 

5️⃣ **CMD**  
Default command to run container  
CMD ["echo", "Hello world"]

 
*Only one CMD per Dockerfile; last takes effect*

6️⃣ **ENTRYPOINT**  
Main executable to run (similar to CMD, but not easily overridden)  
ENTRYPOINT ["echo", "Hello"]

 

*Combined usage:*
ENTRYPOINT ["echo"]
CMD ["World"]

Output: Hello World
 

7️⃣ **ENV**  
Set environment variables  
ENV PORT=5000

 

8️⃣ **EXPOSE**  
Document the port the container listens on  
EXPOSE 80

 

9️⃣ **VOLUME**  
Create mount point to persist data  
VOLUME ["/data"]

 

🔟 **LABEL**  
Add metadata to image  
LABEL maintainer="tejas@example.com"

 
 
---

## 📦 Build and Run Dockerfile

**Build:**  
docker build -t myimage:v1 .

 
- `-t`: Tag name (optional)
- `.`: Context directory

**Run:**  
docker run myimage:v1

 

---

## 🌍 Exposing Ports and Running Servers

Example:
FROM nginx
EXPOSE 80

 
**Build & run:**
docker build -t nginx-server .
docker run -d -p 127.0.0.1:80:80 nginx-server

 
- Browser: [http://127.0.0.1](http://127.0.0.1) → Nginx welcome page

---

## 🔥 Static Website Example

1. Create folder `/myproject` with `index.html` & `Dockerfile`:
2. Dockerfile:
FROM nginx
COPY . /usr/share/nginx/html
EXPOSE 80

 
3. Build & run:
docker build -t static-web .
docker run -d -p 8080:80 static-web

 
- Visit: http://localhost:8080

---

## 🧠 Tips
- Use `.dockerignore` to skip files/folders.
- Prefer small base images (e.g., alpine).
- Combine commands with `&&` to reduce layers.

---

## ✅ Summary Table

| Instruction | Purpose              | Example                        |
|-------------|----------------------|--------------------------------|
| FROM        | Set base image       | FROM ubuntu                    |
| WORKDIR     | Working directory    | WORKDIR /app                   |
| COPY        | Copy files           | COPY . /app                    |
| RUN         | Build-time command   | RUN apt-get ...                |
| CMD         | Default command      | CMD ["python3", "app.py"]      |
| ENTRYPOINT  | Main executable      | ENTRYPOINT ["python3"]         |
| ENV         | Env variable         | ENV PORT=80                    |
| EXPOSE      | Document port        | EXPOSE 80                      |
| VOLUME      | Persist data         | VOLUME ["/data"]               |
| LABEL       | Metadata             | LABEL maintainer="me@x.com"    |
