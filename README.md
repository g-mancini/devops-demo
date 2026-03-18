# DevOps Demo – AWS & Docker

This project demonstrates a basic DevOps workflow by deploying a containerized web application on an AWS EC2 instance using Docker.

---

## Project Overview

- Static web page served with Nginx
- Containerized using Docker
- Orchestrated with docker-compose
- Deployed on AWS EC2 (Ubuntu)
- Access exposed via Security Group (port 8080)

---

## Project Structure

```bash
.
├── Dockerfile
├── docker-compose.yml
└── index.html
```

---

## Run Locally

### Build and start the container

```bash
docker-compose up --build
```

### Access the application

http://localhost:8080

---

## AWS EC2 Deployment

### 1. Connect to the instance

```bash
ssh ubuntu@<EC2-PUBLIC-IP>
```

### 2. Install Docker

```bash
sudo apt update
sudo apt install docker.io docker-compose -y
sudo systemctl enable --now docker
sudo usermod -aG docker ubuntu
```

Log out and log back in to apply group changes.

---

### 3. Clone the repository

```bash
git clone https://github.com/g-mancini/devops-demo.git
cd devops-demo
```

---

### 4. Run the application

```bash
docker-compose up -d
```

---

### 5. Verify containers

```bash
docker ps
```

Expected output should include:

```bash
0.0.0.0:8080->80
```

---

## Network Configuration (AWS)

Configure the EC2 Security Group:

```text
Type: Custom TCP
Port: 8080
Source: 0.0.0.0/0
```

---

## Access the Application

http://<EC2-PUBLIC-IP>:8080

---


## Learning Goals

- Docker containerization
- Basic service orchestration
- Cloud deployment on AWS
- SSH-based remote management
- Git-based workflow

---

## Future Improvements

- Add CI/CD pipeline (GitHub Actions)
- Automate deployment
- Use a reverse proxy
- Introduce Infrastructure as Code (Terraform)

---

## Author

g-mancini
