# CodeAlpha DevOps Project

## Project Overview
This project demonstrates the containerization, deployment, networking, monitoring, health checking, and troubleshooting of a full-stack web application using modern DevOps tools and practices.
The existing G-Lab full-stack application was used as the application workload and containerized as part of the CodeAlpha DevOps project.

## Application Components 

* **Frontend:** React / Vite
* **Backend:** Node.js / Express
* **Web Server:** Nginx
* **Containerization:** Docker
* **Orchestration:** Docker Compose
* **Networking:** Docker bridge network
* **Health Monitoring:** Docker health checks
* **Source Control:** Git/GitHub

---

## Project Architecture

```text
                    Browser
                       │
                       ▼
                ┌─────────────┐
                │    Nginx    │  
                │  Frontend   │  
                │ Docker Image│
                └──────┬──────┘
                       │
                       │ Proxy
                       ▼
                ┌─────────────┐
                │   Backend   │
                │ Node / API  │
                │ Docker Image│
                └──────┬──────┘
                       │
                       ▼
                  Application
                   Services
```

---
* The frontend is built as a production application and served through Nginx.
* The backend runs as a separate Node.js container.
* Docker Compose is used to run and manage both services together.

---

# Docker Implementation

## 1. Nginx Running on localhost

Nginx was configured and verified as a local web server for serving the application.

![Nginx Running on localhost](docs/screenshots/01-nginx-localhost.png)

---

## 2. Nginx Running Inside Docker

Nginx was configured to serve the production frontend inside a Docker container.

![Nginx Docker](docs/screenshots/02-nginx-docker.png)

---

## 3. Backend Dockerfile Build

The Node.js backend was containerized using a dedicated Dockerfile to provide a reproducible runtime environment.

![Backend Docker Build](docs/screenshots/03-backend-docker-build.png)

---

## 4. Frontend Dockerfile Build

The React/Vite frontend was built into a production-ready Docker image using Nginx.

![Frontend Docker Build](docs/screenshots/04-frontend-docker-build.png)

---

## 5. Docker Images

Separate Docker images were created for the frontend and backend services.

![Docker Images](docs/screenshots/05-docker-images.png)

---

## 6. Running Frontend and Backend Containers

The frontend and backend containers were started independently and verified through Docker.

![Containers Running](docs/screenshots/06-containers-running.png)

---

## 7. Dockerized Application on localhost

The containerized web application was successfully accessed through localhost.

![Dockerized Application](docs/screenshots/07-dockerized-app-localhost.png)

---

# Container Lifecycle

## 8. Container Stop and Restart

Docker container lifecycle operations were tested by stopping and restarting application containers.

![Container Lifecycle](docs/screenshots/08-container-lifecycle.png)

---

## 9. Container Recreation

The application containers were recreated from the defined Docker configuration, demonstrating reproducibility.

![Container Recreation](docs/screenshots/09-container-recreation.png)

---

# Docker Compose

## 10. Docker Compose Running

Docker Compose was used to define and start the frontend and backend services together.

![Docker Compose](docs/screenshots/10-docker-compose.png)

---

## 11. Docker Compose Full Application

After starting the services using Docker Compose, the complete application was verified through the browser.

![Compose Application](docs/screenshots/11-docker-compose-full-application.png)

---

## 12. Docker Compose Lifecycle Management

The operational lifecycle of the multi-container stack was tested using compose commands (stop, start, restart).

![Compose Lifecycle](docs/screenshots/12-compose-lifecycle.png)

---

# Monitoring and Troubleshooting

## 13. Container State

Docker container states and resource metrics were inspected using docker stats.

![Container State](docs/screenshots/13-container-state.png)

---

## 14. Backend Logs

Backend container logs were inspected to monitor server activity and identify runtime issues.

![Backend Logs](docs/screenshots/14-backend-logs.png)

---

## 15. Frontend Nginx Logs

Nginx logs were reviewed to monitor frontend requests and investigate web-server issues.

![Frontend Nginx Logs](docs/screenshots/15-frontend-nginx-logs.png)

---

## 16. Docker Inspect

Docker Inspect was used to examine container configuration, networking, runtime settings, and metadata.

![Docker Inspect](docs/screenshots/16-docker-inspect.png)

---

## 17. Container Health

Docker health checks were used to verify the operational status of the application services.

![Container Health](docs/screenshots/17-container-health.png)

---

## 18. Container Health Details

Detailed container health checks and telemetry were inspected using Docker inspect.

![Container Health Details](docs/screenshots/18-container-health-details.png)

---

## 19. Nginx Reverse Proxy Configuration

Nginx was configured as a reverse proxy for the frontend, backend API, and WebSockets.

![Nginx Configuration](docs/screenshots/19-nginx-configuration.png)

---

## 20. Nginx Proxy Pass Troubleshooting

The Nginx proxy configuration was modified during troubleshooting to investigate communication between the frontend and backend services.

![Proxy Pass Troubleshooting](docs/screenshots/20-proxy-pass-troubleshooting.png)

---

## 21. Failure Simulation

A configuration change was intentionally introduced to simulate a frontend failure and observe the resulting behavior.

![Failure Simulation](docs/screenshots/21-frontend-failure.png)

---

## 22. Error Log Analysis

Nginx error logs were analyzed to identify the cause of the frontend failure.

![Error Log](docs/screenshots/22-error-log.png)

---

# Docker Best Practices

## 23. Backend Dockerfile Best Practices

The backend Dockerfile was structured using best practices including non-root user execution, dependency caching, and health checks.

![Backend Dockerfile Best Practices](docs/screenshots/23-backend-dockerfile-best-practices.png)

---

## 24. Frontend Multi-Stage Dockerfile

The frontend uses a multi-stage Docker build.

The build process separates:

1. Node.js build environment
2. Production Nginx environment

This helps keep the final production image smaller and focused on serving the built application.

![Frontend Multi Stage Dockerfile](docs/screenshots/24-frontend-multistage.png)

---

## `.dockerignore`

`.dockerignore` files were used for both frontend and backend services to prevent unnecessary files from being included in the Docker build context.

### Backend

![Backend Dockerignore](docs/screenshots/25-backend-dockerignore.png)

### Frontend

![Frontend Dockerignore](docs/screenshots/26-frontend-dockerignore.png)

---

## Docker Compose Restart Policy

A restart policy was configured in Docker Compose to control service behavior when containers stop or encounter failures.

![Restart Policy](docs/screenshots/27-restart-policy.png)

---

# Docker Networking

## Frontend and Backend Network

The frontend and backend services communicate through a Docker network.

This allows containers to communicate using Docker's internal networking instead of relying on external host networking.

![Docker Network](docs/screenshots/28-docker-network.png)

---

## Docker Network Inspect

Docker network inspection was used to verify connected containers and examine the network configuration.

![Network Inspect](docs/screenshots/29-network-inspect.png)

---

# Health Monitoring

Both frontend and backend services were configured with health monitoring.

The final Compose status confirmed the services were running and healthy.

```text
codealpha-backend    Up    (healthy)
codealpha-frontend   Up    (healthy)
```

![Container Health](docs/screenshots/17-container-health.png)


---

# Final Dockerized Application

The final application was successfully containerized and executed using Docker Compose.

The application consists of:

* React/Vite frontend
* Nginx production server
* Node.js backend
* Docker containers
* Docker Compose
* Docker networking
* Health checks
* Restart policies

![Final Dockerized Application](docs/screenshots/30-final-application-storefront.png)

---

## Container Resource Stats

Continuous monitoring verifies that all running containers maintain a lean memory footprint and minimal CPU usage.

![Container Resource Stats](docs/screenshots/31-container-resource-stats.png)

---

# Technologies Used

| Technology         | Purpose                       |
| ------------------ | ----------------------------- |
| React              | Frontend application          |
| Vite               | Frontend build tool           |
| Node.js            | Backend runtime               |
| Express            | Backend API framework         |
| Docker             | Application containerization  |
| Docker Compose     | Multi-container orchestration |
| Nginx              | Web server / reverse proxy    |
| Docker Network     | Container communication       |
| Docker Healthcheck | Service health monitoring     |
| Git & GitHub       | Source code management        |

---

# DevOps Concepts Demonstrated

This project demonstrates practical experience with:

* Containerization
* Dockerfiles
* Multi-stage Docker builds
* Docker images
* Docker containers
* Container lifecycle
* Docker Compose
* Docker networking
* Network inspection
* Container health checks
* Restart policies
* Nginx configuration
* Reverse proxy configuration
* Application logs
* Error log analysis
* Docker Inspect
* Troubleshooting
* `.dockerignore`
* Production-oriented container configuration

---

# Project Structure

```text
CodeAlpha_DevOps_Project/
│
├── G-Lab-backend/
│   ├── Dockerfile
│   ├── .dockerignore
│   ├── package.json
│   ├── server.js
│   ├── Controllers/
│   ├── Middleware/
│   ├── models/
│   ├── routers/
│   ├── services/
│   ├── utils/
│   └── ...
│
├── G-Lab-frontend/
│   ├── Dockerfile
│   ├── .dockerignore
│   ├── nginx.conf
│   ├── package.json
│   ├── index.html
│   ├── public/
│   ├── src/
│   └── ...
│
├── docs/
│   └── screenshots/
│       ├── 01-nginx-localhost.png
│       ├── 02-nginx-docker.png
│       ├── 03-backend-docker-build.png
│       ├── 04-frontend-docker-build.png
│       ├── 05-docker-images.png
│       ├── 06-containers-running.png
│       ├── 07-dockerized-app-localhost.png
│       ├── 08-container-lifecycle.png
│       ├── 09-container-recreation.png
│       ├── 10-docker-compose.png
│       ├── 11-docker-compose-full-application.png
│       ├── 12-compose-lifecycle.png
│       ├── 13-container-state.png
│       ├── 14-backend-logs.png
│       ├── 15-frontend-nginx-logs.png
│       ├── 16-docker-inspect.png
│       ├── 17-container-health.png
│       ├── 18-container-health-details.png
│       ├── 19-nginx-configuration.png
│       ├── 20-proxy-pass-troubleshooting.png
│       ├── 21-frontend-failure.png
│       ├── 22-error-log.png
│       ├── 23-backend-dockerfile-best-practices.png
│       ├── 24-frontend-multistage.png
│       ├── 25-backend-dockerignore.png
│       ├── 26-frontend-dockerignore.png
│       ├── 27-restart-policy.png
│       ├── 28-docker-network.png
│       ├── 29-network-inspect.png
│       ├── 30-final-application-storefront.png
│       └── 31-container-resource-stats.png
│
├── compose.yaml
├── .gitignore
└── README.md
```

---

# Running the Project

Clone the repository and navigate to the project directory.

```bash
git clone https://github.com/kavindugeethshan/CodeAlpha_DevOps_Project.git

cd CodeAlpha_DevOps_Project
```

Start the application using Docker Compose:

```bash
docker compose up -d
```

Check the running services:

```bash
docker compose ps
```

View backend logs:

```bash
docker compose logs backend
```

View frontend logs:

```bash
docker compose logs frontend
```

Stop the application:

```bash
docker compose down
```

---

# Final Verification

The final Docker Compose deployment was verified with both application services running successfully.

```text
codealpha-backend    Running (healthy)
codealpha-frontend   Running (healthy)
```
The project demonstrates a complete DevOps workflow from an existing full-stack application to containerized deployment, service orchestration, networking, health monitoring, logging, troubleshooting, and final verification.

# Project Outcome

This CodeAlpha DevOps project demonstrates how a full-stack web application can be transformed into a reproducible containerized environment using Docker.

The project covers the complete workflow:

```text
 Application Source Code 
    │ 
    ▼
 Dockerfiles 
    │ 
    ▼ 
 Docker Images 
    │ 
    ▼ 
 Docker Containers 
    │ 
    ▼ 
 Nginx + Backend 
    │ 
    ▼ 
 Docker Networking 
    │ 
    ▼ Docker Compose 
    │ 
    ▼ 
 Health Monitoring 
    │ 
    ▼ 
 Logs & Troubleshooting 
    │ 
    ▼ 
Final Dockerized Application

```

---

# Author

**Kavindu Geethshan Subasingha**

**CodeAlpha DevOps Internship Project**


## Thank You for Viewing This Project