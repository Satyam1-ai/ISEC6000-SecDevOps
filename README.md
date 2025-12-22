# Microservices E‑Commerce Application Deployment

This project involves building, deploying, and securing a microservices‑based e‑commerce application using the **Saleor** platform. It was completed as part of the **ISEC6000 – Secure DevOps** course at Curtin University.

## Project Overview

The application uses a **microservices architecture** deployed on **Google Kubernetes Engine (GKE)**, with separate services for the API, storefront, and dashboard. It includes security measures such as container hardening and vulnerability scanning, and is documented with a clear architecture diagram.

## Tasks Breakdown

### Task 1: Set Up Initial Infrastructure

1. **Kubernetes Cluster Setup**
   - Logged into Google Cloud Console and created a GKE cluster.
   - Connected the local terminal to the cluster using gcloud and kubectl commands.

2. **Install and Configure `kubectl`**
   - Configured the local environment to use `kubectl` to manage the GKE cluster.
   - Verified connectivity between the local machine and the cluster.

3. **Set Up Git Repositories**
   - Forked and cloned the required repositories:
     - [Saleor API](https://github.com/saleor/saleor)
     - [Saleor Storefront](https://github.com/saleor/react-storefront)
     - [Saleor Dashboard](https://github.com/saleor/saleor-dashboard)
     - [Saleor Platform](https://github.com/saleor/saleor-platform)

### Task 2: Microservices Architecture and Deployment

1. **Container Deployment**
   - Created the deployment file (`kubernetes.yaml`) for setting up containers and services.
   - Ran Django database migrations for the Saleor API.
   - Exposed the API on port **8000** (default).

2. **Storefront (React) Setup**
   - Cloned the Saleor Storefront repository.
   - Installed dependencies with `npm install`.
   - Ran the storefront on **localhost:3000**.

3. **Dashboard Setup**
   - Installed dependencies and ran the Saleor Dashboard on ports **9000** (regular) and **9002** (for optimization/testing).
   - Created an admin superuser for managing the shop.

### Task 3: Security Measures Implementation

1. **Container Security**
   - Configured containers to run as **non‑root** users.
   - Applied **memory and resource constraints** to limit resource usage and reduce risk.

2. **Vulnerability Scanning**
   - Used **Trivy** to scan for vulnerabilities in the API, Postgres, and Redis containers.
   - Reviewed and addressed critical vulnerabilities based on the scan results.

### Task 4: Architecture Diagram Visualization

The architecture of this e‑commerce application is based on a microservices design. Key components:

1. **Frontend Applications** – Storefront and Dashboard handle user interaction and communicate with backend services via HTTP/HTTPS.
2. **Nginx Load Balancer** – Distributes incoming requests across backend services.
3. **Saleor API (GraphQL Server)** – Manages communication for products, users, and orders.
4. **Django Application** – Implements the business logic behind the API.
5. **Saleor Microservices** – Handle products, orders, users, and payments.
6. **Database (Postgres)** – Stores application data, including login and superuser information.
7. **Cloud and Gateway** – Uses **GKE** as the cloud platform, with a gateway exposing the services to the internet.

---

## Issues Faced

- Exceeded Google Cloud quota during deployment, which led to unexpected billing charges. Resolved by cleaning unused resources and disabling billing after project completion.

---

## Author

**Satyam Binayak Dash**  
Student ID: 21756630  
ISEC6000 – Secure DevOps, Curtin University
