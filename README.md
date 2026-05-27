# Blue-Green Deployment using Docker & Nginx 🚀

A DevOps project demonstrating Blue-Green deployment strategy using Docker containers, Nginx reverse proxy, and AWS EC2.

This project simulates zero-downtime deployments by maintaining two isolated environments — **Blue** and **Green** — and dynamically switching traffic between application versions using Nginx.

---

## 📌 Project Overview

Blue-Green deployment is a modern release management strategy used to reduce downtime and deployment risks.

In this project:

* Two separate application environments are maintained:

  * **Blue Environment** → Current production version
  * **Green Environment** → New deployment version

* Nginx acts as a reverse proxy and routes traffic to the active environment.

* Traffic can be switched between environments without stopping the application.

---

## 🛠️ Technologies Used

* AWS EC2
* Docker
* Docker Compose
* Nginx
* Linux
* Git & GitHub

---

## 🏗️ Architecture

```text id="a1y0mp"
                User Request
                      │
                      ▼
              Nginx Reverse Proxy
                 /            \
                /              \
               ▼                ▼
       Blue Container     Green Container
        (Version 1)        (Version 2)
```

---

## 📂 Project Structure

```bash id="q7e2na"
blue-green-deployment/
│
├── blue/
│   └── index.html
│
├── green/
│   └── index.html
│
├── nginx/
│   └── default.conf
│
└── docker-compose.yml
```

---

## ⚙️ Deployment Workflow

### Step 1 — Start Containers

```bash id="r3xwq1"
docker-compose up -d
```

### Step 2 — Verify Running Containers

```bash id="n9vk7a"
docker ps
```

### Step 3 — Access Application

```text id="k8mw1c"
http://<EC2-PUBLIC-IP>:8080
```

---

## 🔄 Traffic Switching

Initially, Nginx routes traffic to:

```nginx id="v4jh2m"
proxy_pass http://blue;
```

To switch deployment traffic to Green environment:

```nginx id="e6tx9f"
proxy_pass http://green;
```

Restart Nginx container:

```bash id="g1yb6w"
docker restart nginx-proxy
```

This simulates a zero-downtime deployment strategy.

---

## 📊 Features

* ✅ Blue-Green deployment strategy
* ✅ Docker container orchestration
* ✅ Nginx reverse proxy configuration
* ✅ Zero-downtime deployment simulation
* ✅ Traffic switching between environments
* ✅ AWS EC2 deployment
* ✅ Docker networking

---

## ☁️ AWS Deployment Environment

This project was deployed and tested on:

* AWS EC2
* Amazon Linux
* Docker-enabled environment

---

## 🚀 Future Improvements

* Automate deployment switching using GitHub Actions
* Add health-check validation before traffic switching
* Implement automatic rollback mechanism
* Add monitoring and logging
* Integrate CI/CD pipeline
* Use Load Balancer for scalability

---

## 📚 Learning Outcomes

Through this project, I learned:

* Blue-Green deployment concepts
* Docker networking
* Nginx reverse proxy configuration
* Deployment traffic routing
* Linux infrastructure management
* Zero-downtime deployment strategies
* AWS EC2 deployment workflows

---

## 👨‍💻 Author

### Vidyasri Nekuri

Aspiring DevOps Engineer focused on:

* AWS
* Docker
* Linux
* Automation
* CI/CD

### GitHub

https://github.com/Vidyasri-Nekuri
