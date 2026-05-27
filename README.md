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




