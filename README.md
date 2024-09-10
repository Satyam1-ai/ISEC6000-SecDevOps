
# Microservices E-Commerce Application Deployment

This project involves building, deploying, and securing a microservices-based e-commerce application using the Saleor platform. The project was completed as part of the ISEC6000 – Secure DevOps course at Curtin University.

## Project Overview

This application is built using a microservices architecture deployed on Google Kubernetes Engine (GKE), with separate services for the API, storefront, and dashboard. It includes security measures like container security and vulnerability scanning, alongside a well-defined architecture diagram.

## Tasks Breakdown

### Task 1: Set Up Initial Infrastructure
1. **Kubernetes Cluster Setup:**
   - Logged into Google Cloud Console and had connected to my terminal using commands(Screenshots provided in the pdf)

2. **Install and Configure `kubectl`:**
   - Configured the local environment to use `kubectl` to manage the GKE cluster.
   - Set up a connection between the local machine and the cluster.

3. **Set Up Git Repository:**
   - Forked and cloned the required repositories:
     - [Saleor API](https://github.com/saleor/saleor)
     - [Saleor Storefront](https://github.com/saleor/react-storefront)
     - [Saleor Dashboard](https://github.com/saleor/saleor-dashboard)
     - [Saleor Platform](https://github.com/saleor/saleor-platform)

### Task 2: Microservices Architecture and Deployment
1. **Container Deployment:**
   - Created the deployment file (`kubernetes.yaml`) for setting up containers.
   - Ran migrations for the database using python migrate for our databases .
   - Run the webpage on port 8000(which is the default)

2. **React/storefront Setup:**
   - Cloned the Saleor Storefront repository, installed dependencies with `npm install`, and ran the application on localhost port 3000.

3. **Dashboard Setup:**
   - Installed dependencies and ran the Saleor Dashboard on localhost port 9002(for optimization ) and port 9000 regular.
   - Created a superuser (`admin@email.com` and password `admin`).

### Task 3: Security Measures Implementation
1. **Container Security:**
   - Used non-root users for running containers.
   - Applied memory constraints to limit resource usage.

2. **Vulnerability Scanning:**
   - Used **Trivy** to scan for vulnerabilities in the API, Postgres, and Redis containers.
   - Addressed critical vulnerabilities based on the scan results.

### Task 4: Architecture Diagram Visualization
The architecture of this e-commerce application is based on a microservices design. The key components are:
1. **Frontend Application:** Handles user interaction and communicates with backend services via HTTP/HTTPS.
2. **Nginx Load Balancer:** Distributes incoming requests across backend services.
3. **Saleor API (GraphQL Server):** Manages communication for products, users, and orders.
4. **Django Application:** Implements business logic.
5. **Saleor Microservices:** Manages services for products, orders, users, and payments.
6. **Database:** Stores login and superuser data.
7. **Cloud and Gateway:** Uses GKE for the cloud platform, with a gateway directing traffic.

---

## Issues Faced

- Exceeded Google Cloud quota during deployment, leading to billing charges. Disabled billing upon completion of the project.

---

## Author
**Satyam Binayak Dash**  
Student ID: 21756630  
ISEC6000 – Secure DevOps, Curtin University
