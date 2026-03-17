 DevOps Automation Platform

##  Project Overview

This project is an DevOps automation platform that demonstrates a complete CI/CD pipeline with monitoring.

It automates the process of:

* Building applications
* Running tests
* Creating Docker images
* Deploying containers
* Monitoring application performance

---

##  Tech Stack

* **Backend:** Python (Flask)
* **CI/CD:** Jenkins
* **Containerization:** Docker
* **Monitoring:** Prometheus
* **Version Control:** Git & GitHub

---

##  Features

 ✅ Automated CI/CD pipeline using Jenkins
 ✅ Dockerized Flask application
 ✅ Automated build and deployment
 ✅ Monitoring with Prometheus
 ✅ Scalable DevOps workflow

---

##  Project Structure

```
ai-devops-platform/
│── app.py
│── requirements.txt
│── Dockerfile
│── Jenkinsfile
│── prometheus.yml
│── tests/
│── .gitignore
```

---

##  CI/CD Workflow

1. Developer pushes code to GitHub
2. Jenkins triggers pipeline automatically
3. Dependencies are installed
4. Tests are executed
5. Docker image is built
6. Application is deployed in a container
7. Prometheus monitors application metrics

---

##  How to Run the Project

### 1️⃣ Clone Repository

```bash
git clone https://github.com/GayatriKende/ai-devops-platform.git
cd ai-devops-platform
```

---

### 2️⃣ Run Application (Local)

```bash
pip install -r requirements.txt
python app.py
```

---

### 3️⃣ Run with Docker

```bash
docker build -t devops-app .
docker run -d -p 5000:5000 devops-app
```

---

### 4️⃣ Access Application

* App → http://localhost:5000
* Prometheus → http://localhost:9090

---

##  Monitoring

Prometheus is used to:

* Collect metrics from the application
* Monitor performance
* Visualize system health

---

##  Screenshots

* Jenkins Pipeline Success -![Jenkins](https://github.com/user-attachments/assets/a812857e-37a4-433e-9272-c6eca6c55c46)
  AWS EC2 Instance - ![AWS Instance](https://github.com/user-attachments/assets/dc21b316-b565-40d7-bf0e-b0f6c2768b8a)

* Application Running -![App](https://github.com/user-attachments/assets/b2378f6e-30eb-4756-ac26-43302a4993b9)

##  Key Learnings

* Implemented CI/CD using Jenkins
* Containerized applications using Docker
* Integrated monitoring using Prometheus
* Understood DevOps workflow and automation

---

##  Future Improvements

* Add Grafana dashboard for visualization
* Add AI Failure Prediction

---

## Author

**Gayatri Kende**

---

##  Conclusion

This project demonstrates practical implementation of DevOps concepts including **automation, containerization, CI/CD, and monitoring**, making it suitable for real-world applications.
