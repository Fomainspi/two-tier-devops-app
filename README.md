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
_______________________________
### Git and GitHub
Git allows developers to:
•	track changes
•	collaborate
•	rollback code
•	manage versions
GitHub hosts repositories online.
________________________________________
### Node.js
Node.js allows JavaScript to run on the server side.
Benefits:
•	lightweight
•	fast
•	large ecosystem
•	easy API development
________________________________________
### React.js
React is a frontend JavaScript framework.
Benefits:
•	reusable components
•	fast rendering
•	modern frontend architecture
________________________________________
### Docker
Docker packages applications into containers.
Benefits:
•	consistency
•	portability
•	isolation
•	reproducibility
________________________________________
### Docker Compose
Docker Compose manages multiple containers together.
Benefits:
•	easier deployments
•	simplified networking
•	centralized configuration
________________________________________
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


