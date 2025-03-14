RPC Monitoring System - README
Overview
This project is an RPC Monitoring System designed to monitor backend services, track performance metrics, visualize data, and enable debugging via a frontend dashboard. The system uses gRPC, Prometheus, WebSocket for real-time updates, and SonarQube for code quality checks. The frontend is a modern React-based dashboard that visualizes real-time metrics and error rates.

Table of Contents
Project Setup
Backend Setup
Frontend Setup
Running the Application Locally
Backend
Frontend
CI/CD Pipeline
GitHub Actions Setup
SonarQube Integration
Deployment
Backend Deployment (Docker + Kubernetes)
Frontend Deployment (Vercel)
API Endpoints
Architecture
Troubleshooting
1. Project Setup <a name="setup"></a>
Backend Setup
To set up the backend, follow these steps:

Clone the repository:

bash
Copy
git clone https://github.com/your-repository-name
cd rpc-monitoring-system/backend
Install dependencies:

bash
Copy
npm install
Run the backend service:

bash
Copy
npm start
This will run the gRPC service on localhost:50051 and expose Prometheus metrics.

Frontend Setup
To set up the frontend, follow these steps:

Navigate to the frontend folder:

bash
Copy
cd rpc-monitoring-system/frontend
Install dependencies:

bash
Copy
npm install
Run the frontend:

bash
Copy
npm start
This will run the frontend React application on localhost:3000 with real-time updates through WebSocket.

2. Running the Application Locally <a name="running-locally"></a>
Backend
Ensure that you have Node.js installed. You can verify this with:

bash
Copy
node -v
Run the backend service:

bash
Copy
npm start
Verify the backend is running at http://localhost:50051.

Frontend
Ensure that you have Node.js installed.

Navigate to the frontend directory and run:

bash
Copy
npm start
Verify the frontend is running at http://localhost:3000.

3. CI/CD Pipeline <a name="cicd-pipeline"></a>
The CI/CD pipeline is set up using GitHub Actions.

GitHub Actions Setup
The ci.yml file is located in the .github/workflows folder. It automates:

Code quality analysis using SonarCloud
Building and testing of the backend and frontend
Docker image building
The SonarQube integration is set up using your SonarCloud token. Make sure you have added the SONAR_TOKEN secret in your GitHub repository settings.

SonarQube Integration
Make sure you have a SonarCloud account.
Generate a SonarQube token from SonarCloud.
Add the SONAR_TOKEN in your GitHub repository’s secrets.
The GitHub Actions workflow will automatically run code quality checks via SonarCloud every time you push changes to the repository.

4. Deployment <a name="deployment"></a>
Backend Deployment (Docker + Kubernetes)
Docker Setup:

The backend is Dockerized. The Dockerfile in the backend/ directory builds the backend service image.
Run the following command to build the Docker image for the backend:
bash
Copy
docker build -t myapp-backend ./backend
Docker Compose:

To run both the backend and frontend locally using Docker Compose, use the docker-compose.yml file provided in the root directory.
Start both services:
bash
Copy
docker-compose up --build
Kubernetes (Optional):

Set up Kubernetes for deployment using Helm charts or kubectl.
The Kubernetes configuration can be adjusted based on your cloud provider (AWS, GCP, etc.).
Frontend Deployment (Vercel)
Vercel Deployment:

Create a Vercel account and link your GitHub repository.
Vercel will automatically detect your React app and deploy it with minimal configuration.
Push your frontend code to GitHub and connect it to Vercel for automatic deployment.

5. API Endpoints <a name="api-endpoints"></a>
gRPC API (Backend)
Endpoint: /metrics
Method: GET
Description: Fetches real-time performance metrics of the backend service.
Response: JSON object containing status, response_time_ms, and timestamp.
Prometheus Metrics
The backend exposes Prometheus metrics at http://localhost:50051/metrics (or similar URL depending on the deployment).
6. Architecture <a name="architecture"></a>
The architecture consists of:

Backend: The backend service uses gRPC to handle requests, exposed as an API for Prometheus metrics.
Frontend: A React-based dashboard that connects to the backend via WebSockets to visualize performance metrics in real-time.
Prometheus: Used for collecting and storing metrics.
SonarCloud: Performs code quality checks as part of the CI/CD pipeline.
Docker + Kubernetes: Backend and frontend are containerized and deployed in scalable environments using Kubernetes or Docker Compose.
7. Troubleshooting <a name="troubleshooting"></a>
Backend Service Not Running:

Ensure that Node.js is installed.
Check if the backend server is running on the correct port (default: 50051).
Ensure all required dependencies are installed using npm install.
Frontend Not Connecting to Backend:

Check WebSocket URL in the frontend code to ensure it’s pointing to the correct backend URL.
Check that both services are running and can communicate.
SonarCloud Issues:

Ensure the SONAR_TOKEN secret is added to GitHub.
Verify that the SonarCloud token has the correct permissions for your repository.
Docker Issues:

Make sure Docker is installed and running.
Verify that your Dockerfile is correctly configured.

![Screenshot 2025-03-14 151805](https://github.com/user-attachments/assets/79348d3c-f9bc-45d3-829e-5d260c12263f)
![Screenshot 2025-03-14 171541](https://github.com/user-attachments/assets/de41eb8e-9d40-434e-851f-8771ccf6dc4b)


