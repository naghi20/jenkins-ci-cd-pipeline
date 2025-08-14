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
| ![Pipeline](screenshots/pipeline.png) | ![App](screenshots/app.png) |  

## 🔗 Links  
- [Jenkins Official Docs](https://www.jenkins.io/doc/)  
