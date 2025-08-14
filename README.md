# Jenkins CI/CD Pipeline Project  
Automated deployment pipeline using Jenkins, Docker, and GitHub.  

## 🚀 Features  
- Pulls code from GitHub on commit.  
- Builds a Docker image and pushes it to DockerHub.  
- Deploys the containerized app.  

## ⚙️ Prerequisites  
- Jenkins server (with Docker and Git plugins installed).  
- DockerHub account (for storing images).  
- GitHub repository (this repo).  

## 🛠️ Setup  
1. **Jenkins Configuration**:  
   - Install plugins: Git, Docker Pipeline, Credentials.  
   - Add DockerHub credentials in Jenkins (`dockerhub-creds`).  

2. **Run the Pipeline**:  
   - Create a new Jenkins pipeline job.  
   - Point it to this repository’s `Jenkinsfile`.  

## 📸 Screenshots  
| Pipeline Success | Deployed App |  
|------------------|--------------|  

## 🔗 Links  
- [Jenkins Official Docs](https://www.jenkins.io/doc/)  


# 🚀 Jenkins CI/CD Pipeline: Automated Dockerized Deployment


## 📌 Overview
This project demonstrates a **fully automated CI/CD pipeline** using Jenkins to:
1. Pull code from a GitHub repository.
2. Build a Docker container for a Python Flask app.
3. Push the image to DockerHub.
4. Deploy the container to a server.  

**Tools Used**: Jenkins, Docker, GitHub, Bash.

---

## 🌟 Key Features
| Feature               | Description                                                                 |
|-----------------------|-----------------------------------------------------------------------------|
| **GitHub Integration** | Webhook triggers Jenkins on `git push`.                                     |
| **Docker Automation**  | Builds, tags, and pushes images to DockerHub.                               |
| **Declarative Pipeline** | Uses Jenkinsfile for reproducible pipeline-as-code.                        |
| **Credentials Security** | Securely stores DockerHub credentials using Jenkins Secrets.              |

---

## 🛠️ Prerequisites
1. **Jenkins Server**  
   - Install Jenkins on a Linux VM (Ubuntu) or locally via Docker:  
     ```bash
     docker run -d --name jenkins -p 8080:8080 -p 50000:50000 jenkins/jenkins:lts
     ```
2. **Tools**  
   - Docker:  
     ```bash
     sudo apt install docker.io
     ```
   - Git:  
     ```bash
     sudo apt install git
     ```
3. **Accounts**  
   - GitHub repository (this project).  
   - DockerHub account for image storage.

---

## 🏗️ Pipeline Architecture
```mermaid
graph LR
    A[GitHub] -->|Webhook| B(Jenkins)
    B --> C[Build Docker Image]
    C --> D[Push to DockerHub]
    D --> E[Deploy Container]

🔧 Setup Instructions
1. Configure Jenkins
Install Plugins:
Navigate to Manage Jenkins > Plugins and install:

Docker Pipeline

GitHub Integration

Credentials Binding

Add DockerHub Credentials:

Go to Manage Jenkins > Credentials > System > Global Credentials.

Add username/password with ID dockerhub-creds.

2. Set Up the Pipeline
Create a New Pipeline Job:

Select New Item > Pipeline.

Under Pipeline, choose Pipeline script from SCM.

Set SCM to Git and enter this repository’s URL.

Configure Webhooks:

In GitHub repo settings, add a webhook:

URL: http://<jenkins-ip>:8080/github-webhook/
Content-Type: application/json

Repository Structure

jenkins-ci-cd-pipeline/
 app/
   app.py               # Python Flask application
  requirements.txt      # Dependencies
 Dockerfile               # Container configuration
Jenkinsfile              # Pipeline definition
screenshots/             # Pipeline/output visuals

🚦 Running the Pipeline
Manual Trigger:
Click Build Now in Jenkins.

Automatic Trigger:
Push a commit to GitHub:

bash
git add . && git commit -m "Update app" && git push origin main
Verify Deployment:
Access the app at http://<server-ip>:5000:

🐛 Troubleshooting
Issue	Solution
Permission Denied	Ensure Jenkins user is in the docker group: sudo usermod -aG docker jenkins
Webhook Fails	Check Jenkins URL in GitHub and verify network connectivity.
Docker Push Fails	Verify credentials ID in Jenkinsfile matches Jenkins credentials store.
📈 Enhancements (Optional)
Add Testing Stage:
Integrate pytest/unit tests in the pipeline.

Multi-Environment Deployments:
Use Jenkins parameters to deploy to Dev/Prod.

Kubernetes Deployment:
Replace docker run with kubectl apply in the pipeline.

📚 Resources
Jenkins Official Documentation

Docker Best Practices
