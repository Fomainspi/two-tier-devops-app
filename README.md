# Building a Two-Tier Application with Docker, GitHub, Jenkins, and CI/CD

## Table of Contents
1.	Project Introduction
2.	Environment Setup
3.	Project Structure
4.	Git and GitHub Workflow
5.	Backend Development
6.	Frontend Development
7.	Docker and Docker Compose
8.	CI/CD Pipeline with Jenkins
9.	Troubleshooting Guide
10.	Commands Reference
11.	Best Practices
12.	Real-World DevOps Concepts
13.	Final Deployment Flow
14.	Conclusion

# 1. Project Introduction
## 1.1 Project Goal
The purpose of this project is to build and deploy a complete two-tier application using modern DevOps tools and practices.
This project simulates a real-world software deployment workflow used by companies today.
The project contains:
•	Frontend application
•	Backend API
•	Docker containers
•	Docker Compose orchestration
•	GitHub repository
•	Jenkins CI/CD pipeline
•	Automated deployment process
The project demonstrates how a developer writes code, pushes it to GitHub, and automatically deploys the application using Jenkins and Docker.

## 1.2 What is a Two-Tier Application?
A two-tier architecture separates an application into two main layers:
### Tier 1 — Frontend
The frontend is the user interface.
Responsibilities:
•	Display information
•	Interact with users
•	Send requests to backend
•	Show responses from backend
In this project:
•	React.js frontend
•	Runs inside Docker container

### Tier 2 — Backend
The backend contains the business logic.
Responsibilities:
•	Process requests
•	Return data
•	Manage APIs
•	Handle application logic
In this project:
•	Node.js backend
•	Express.js API
•	Runs inside Docker container

## 1.3 Project Architecture
The architecture used in this project:
User Browser
      ↓
Frontend Container (React)
      ↓
Backend Container (Node.js API)
Deployment architecture:
Developer
   ↓
GitHub Repository
   ↓
Jenkins CI/CD Pipeline
   ↓
Docker Build
   ↓
Docker Compose Deployment

## 1.4 Technologies Used

<img width="615" height="320" alt="image" src="https://github.com/user-attachments/assets/e8cb2f69-82e0-4b7b-ad81-80bf584a3004" />

## 1.5 Why These Technologies Were Chosen

### Linux
Linux is the standard operating system used in cloud and DevOps environments.
Most production servers use Linux.

### Git and GitHub
Git allows developers to:
•	track changes
•	collaborate
•	rollback code
•	manage versions
GitHub hosts repositories online.

### Node.js
Node.js allows JavaScript to run on the server side.
Benefits:
•	lightweight
•	fast
•	large ecosystem
•	easy API development

### React.js
React is a frontend JavaScript framework.
Benefits:
•	reusable components
•	fast rendering
•	modern frontend architecture

### Docker
Docker packages applications into containers.
Benefits:
•	consistency
•	portability
•	isolation
•	reproducibility

### Docker Compose
Docker Compose manages multiple containers together.
Benefits:
•	easier deployments
•	simplified networking
•	centralized configuration

### Jenkins
Jenkins automates:
•	building
•	testing
•	deployment
•	CI/CD pipelines
Benefits:
•	automation
•	repeatability
•	reduced manual work

# 2. Environment Setup
2.1 Linux Setup
This project was developed using Linux.
Linux is highly preferred in DevOps because:
•	lightweight
•	powerful CLI
•	cloud compatibility
•	automation friendly
Ubuntu or WSL Ubuntu can be used.

## 2.2 Updating Linux Packages
Always update packages before installations.
Command:
sudo apt update && sudo apt upgrade -y


Explanation:

<img width="540" height="156" alt="image" src="https://github.com/user-attachments/assets/1195e4c7-00ee-41de-af22-10aeafd2228d" />


## 2.3 Installing Git
Install Git:
sudo apt install git -y
Verify installation:
git --version

## 2.4 Git Configuration
Configure Git identity:
git config --global user.name "Your Name"
git config --global user.email "your@email.com"
Verify:
git config --list

## 2.5 Installing Docker
Install Docker:
sudo apt install docker.io -y
Start Docker:
sudo systemctl start docker
Enable Docker at startup:
sudo systemctl enable docker
Verify:
docker --version

## 2.6 Docker Permissions
Allow current user to run Docker without sudo:
sudo usermod -aG docker $USER
Apply changes:
newgrp docker

## 2.7 Installing Docker Compose
Modern Docker Compose uses:
docker compose
Verify:
docker compose version

## 2.8 Installing Node.js
Install Node.js:
sudo apt install nodejs npm -y
Verify:
node -v
npm -v

## 2.9 Installing Maven
Install Maven:
sudo apt install maven -y
Verify:
mvn -version
Although Maven was not fully used in this project, it is commonly used in Java DevOps pipelines.

## 2.10 Installing Jenkins Using Docker
Create Jenkins persistent volume:
docker volume create jenkins_home
Run Jenkins container:
docker run -d \
  --name jenkins \
  -u root \
  -p 9090:8080 \
  -p 50000:50000 \
  -v jenkins_home:/var/jenkins_home \
  -v /var/run/docker.sock:/var/run/docker.sock \
  jenkins/jenkins:lts

## 2.11 Explanation of Jenkins Docker Command
Option	Meaning
-d	Detached mode
–name	Container name
-u root	Run as root user
-p 9090:8080	Port mapping
-v	Volume mounting
docker.sock	Docker daemon access

## 2.12 Accessing Jenkins
Open browser:
http://localhost:9090
Retrieve admin password:
docker exec jenkins cat /var/jenkins_home/secrets/initialAdminPassword


# 3. Project Structure
## 3.1 Root Project Structure

<img width="244" height="254" alt="image" src="https://github.com/user-attachments/assets/b831659f-476a-4941-89b0-14bdeba8fb04" />

two-tier-app/
│
├── backend/
├── frontend/
├── docker-compose.yml
├── Jenkinsfile
└── .gitignore


## 3.2 Backend Structure
backend/
│
├── Dockerfile
├── package.json
├── package-lock.json
└── server.js

## 3.3 Frontend Structure
frontend/
│
├── Dockerfile
├── package.json
├── public/
├── src/
└── .gitignore

## 3.4 Important Files
### server.js
Main backend API file.

### package.json
Contains:
•	project metadata
•	dependencies
•	scripts

### Dockerfile
Defines Docker image instructions.

### docker-compose.yml
Defines multi-container deployment.

### Jenkinsfile
Defines CI/CD pipeline stages.

# 4. Git and GitHub Workflow
## 4.1 Creating Repository
Create repository on GitHub.
Example:
two-tier-app

## 4.2 Initialize Git
Inside project:
git init

## 4.3 Add Remote Repository
git remote add origin <repository-url>

## 4.4 Git Add
Track files:
git add .

## 4.5 Git Commit
Save changes:
git commit -m "Initial commit"

## 4.6 Push to GitHub
git push -u origin main

## 4.7 Pull Changes
git pull origin main

## 4.8 Branching Strategy
This is not the strategy i used but I would recommend this one:
main
feature/frontend
feature/backend

## 4.9 Merge Conflicts
Conflicts occur when two versions modify the same file.
Resolve manually then commit.

## 4.10 Git Best Practices
•	commit often
•	write meaningful commit messages
•	avoid pushing secrets
•	use branches
•	pull before push

# 5. Backend Development
## 5.1 Creating Backend
Create backend folder:
mkdir backend
cd backend
Initialize npm:

## 5.2 Install Dependencies
npm init -y
npm install express cors

## 5.3 Backend server.js

const express = require('express');
const cors = require('cors');

const app = express();

app.use(cors());

app.get('/', (req, res) => {
    res.send('Backend is running successfully!');
});

app.listen(5000, () => {
    console.log('Server running on port 5000');
});

## 5.4 Backend Explanation
## Code	         Purpose
express()	      Create server
cors()	      Allow frontend requests
app.get()	      Create API endpoint
app.listen()	Start server

## 5.5 Run Backend Locally
node server.js
Test:
http://localhost:5000

## 5.6 Backend Dockerfile
FROM node:18

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

EXPOSE 5000

CMD ["node", "server.js"]

## 5.7 Backend Dockerfile Explanation
Instruction	Purpose
FROM	Base image
WORKDIR	Working directory
COPY	Copy files
RUN	Execute command
EXPOSE	Open port
CMD	Startup command

# 6. Frontend Development
## 6.1 Create Frontend
npx create-react-app frontend

## 6.2 Frontend API Connection
Correct Docker networking:
fetch("http://backend:5000")
NOT:
fetch("http://localhost:5000")

## 6.3 Why localhost Fails Inside Containers
Inside containers:
localhost = current container
Containers communicate using service names.

## 6.4 Frontend Dockerfile

FROM node:18

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

EXPOSE 3000

CMD ["npm", "start"]

## 6.5 Frontend Dockerfile Explanation

<img width="540" height="218" alt="image" src="https://github.com/user-attachments/assets/d5ad3008-7b51-406c-9a39-2bedd37b18f2" />

# 7. Docker and Docker Compose
## 7.1 What is Docker?
Docker is a containerization platform.
It packages applications with:
•	code
•	dependencies
•	runtime
•	libraries

## 7.2 Images vs Containers
Images	Containers
Blueprint	Running instance
Static	Dynamic
Build artifact	Execution environment

## 7.3 Docker Build
docker build -t backend-app .

## 7.4 Docker Run
docker run -p 5000:5000 backend-app

## 7.5 Docker Networks
Docker networks allow containers to communicate.
Docker Compose automatically creates networks.

## 7.6 Docker Volumes
Volumes store persistent data.

docker volume create jenkins_home

## 7.7 Docker Compose File
services:
  backend:
    build: ./backend
    ports:
      - "5000:5000"

  frontend:
    build: ./frontend
    ports:
      - "3001:3000"
    depends_on:
      - backend

## 7.8 Docker Compose Explanation
## Section	       Purpose
services	    Define containers
build	Build     context
ports	          Port mapping
depends_on	    Service dependency

## 7.9 Port Mapping Explanation
Example:
3001:3000
Means:
Host	Container
3001	3000

## 7.10 Build and Start Containers
docker compose up --build
Detached mode:
docker compose up -d


# 8. CI/CD Pipeline
## 8.1 What is CI/CD?
CI/CD means:
Term	Meaning
CI	Continuous Integration
CD	Continuous Delivery/Deployment

## 8.2 Jenkins Pipeline Overview
### Pipeline stages:
GitHub
 ↓
Clone Repository
 ↓
Build Containers
 ↓
Deploy Application

## 8.3 Jenkinsfile
pipeline {
    agent any

    stages {

        stage('Clone Repository') {
            steps {
                echo 'Cloning repository from GitHub...'
            }
        }

        stage('Build Application') {
            steps {
                echo 'Building Docker Compose services...'
                sh 'docker compose build'
            }
        }

        stage('Deploy Application') {
            steps {
                sh 'docker compose down || true'
                sh 'docker compose up -d'
            }
        }

    }
}

## 8.4 Jenkinsfile Explanation
### pipeline
Defines CI/CD pipeline.

### agent any
Run on any Jenkins agent.

### stage
Defines pipeline phase.

### steps
Commands executed in stage.

### sh
Execute Linux shell commands.

## 8.5 Jenkins Pipeline Setup
1.	Create new pipeline job
2.	Select Pipeline
3.	Use Pipeline script from SCM
4.	Select Git
5.	Add GitHub repository
6.	Use Jenkinsfile
7.	Save
8.	Build Now

# 9. Troubleshooting Guide
## 9.1 Port Conflict Errors
### Error
port is already allocated

### Cause
Another container already used the port.

### Diagnosis
docker ps

### Solution
Remove conflicting container or use another port.

### Best Practice
Use cleanup stage:
docker compose down

## 9.2 Frontend Cannot Connect to Backend
### Error
Failed to connect to backend

### Cause
Frontend used localhost.

### Wrong
http://localhost:5000

### Correct
http://backend:5000

### Best Practice
Use Docker service names.

## 9.3 Docker Compose Command Not Found
### Error
docker compose: command not found

### Cause
Docker Compose plugin missing.

### Solution
Install Docker Compose plugin.
sudo apt update
sudo apt install docker-compose-plugin

## 9.4 Docker Permission Denied
### Error
permission denied while trying to connect to docker.sock

### Cause
Jenkins lacked Docker socket permission.

### Solution
Run Jenkins with:
-u root
or use Docker group permissions.

## 9.5 Jenkins Container Name Conflict
### Error
container name already in use

### Cause
Fixed container names caused conflicts.

### Solution
Remove:
container_name
from compose file.

## 9.6 Frontend Dockerfile Missing
### Error
failed to read Dockerfile

### Cause
Dockerfile ignored by Git.

### Solution
Force add file:
git add -f frontend/Dockerfile

## 9.7 Git Submodule Problems
### Error
Pathspec is in submodule

### Cause
Frontend initialized as nested Git repository.

### Solution
rm -rf frontend/.git
git rm --cached frontend
Re-add folder normally.

## 10. Commands Reference

<img width="910" height="457" alt="image" src="https://github.com/user-attachments/assets/db47b4c6-ebb0-4a6d-b336-14badf344b9f" />


## 11. Best Practices
### Docker Best Practices
•	avoid hardcoded container names
•	use environment variables
•	keep images lightweight
•	use .dockerignore
•	separate services properly
________________________________________
Git Best Practices
•	commit frequently
•	use meaningful commit messages
•	avoid committing secrets
•	use branches
________________________________________
CI/CD Best Practices
•	automate deployments
•	use cleanup stages
•	separate build and deploy stages
•	avoid manual deployments
________________________________________
Security Best Practices
•	avoid root containers in production
•	protect secrets
•	avoid exposing unnecessary ports
•	use least privilege
________________________________________
12. Real-World DevOps Concepts
This project reflects real company workflows.
Real companies use:
•	GitHub
•	Jenkins
•	Docker
•	CI/CD pipelines
•	automated deployments
•	container orchestration
This project simulates:
Developer pushes code
       ↓
CI/CD pipeline starts
       ↓
Containers build automatically
       ↓
Application deploys automatically
________________________________________
13. Final Deployment Flow
Developer
   ↓
Git Commit
   ↓
Git Push
   ↓
GitHub Repository
   ↓
Jenkins Pipeline Trigger
   ↓
Clone Repository
   ↓
Docker Compose Build
   ↓
Docker Compose Deployment
   ↓
Frontend Container
   ↓
Backend Container
   ↓
Application Available
________________________________________
14. Conclusion
This project covered a complete beginner-to-intermediate DevOps workflow.
Key concepts learned:
•	Linux administration
•	Git and GitHub
•	Node.js backend development
•	React frontend development
•	Docker containerization
•	Docker Compose orchestration
•	Jenkins CI/CD pipelines
•	Pipeline troubleshooting
•	Container networking
•	Port management
•	CI/CD automation
•	Infrastructure debugging
This project reflects real-world DevOps engineering practices used in modern companies.
By completing this project, the learner gains hands-on experience with:
•	application deployment
•	automation
•	container management
•	CI/CD workflows
•	DevOps troubleshooting
•	infrastructure concepts
This forms a strong foundation for advanced DevOps topics such as:
•	Kubernetes
•	Terraform
•	AWS deployment
•	Monitoring
•	Infrastructure as Code
•	Advanced CI/CD pipelines
•	Cloud-native architectures


































