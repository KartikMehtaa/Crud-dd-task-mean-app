CRUD-DD-TASK-MEAN-APP Deployment Instructions

1️⃣ Project Setup

Download and Unzip

Download the project folder from the source.

Unzip it to a local workspace.

Organize Folder Structure

Keep separate folders for backend, frontend, and nginx.

Ensure a docker-compose.yml file exists at the root.

Place the Nginx configuration in nginx/default.conf.

2️⃣ Push to GitHub

Initialize a Git repository in the project folder.

Add all files and commit the changes.

Push the repository to GitHub.

3️⃣ Prepare Docker Images

Write Dockerfile for backend and frontend.

Ensure the frontend build folder path in Dockerfile matches Angular’s dist/ folder.

Build Docker images locally to verify.

Push the images to Docker Hub.

4️⃣ Launch EC2 Instance

Go to AWS EC2 console and launch a new Ubuntu instance.

Attach a security group that allows ports 22, 80, and 3000 (for backend if needed).

Download the .pem key file for SSH access.

5️⃣ Connect to EC2

Use SSH to connect to the instance using the .pem key.

Update the system and install necessary dependencies (Docker, Docker Compose).

6️⃣ Jenkins Setup

Install Jenkins on the EC2 instance.

Configure Jenkins to pull your GitHub repository.

Add Docker credentials to Jenkins for accessing Docker Hub.

Write a Jenkins pipeline to:

Fetch the latest code from GitHub.

Pull the Docker images from Docker Hub.

Launch containers using docker-compose.

7️⃣ Configure Nginx

Create default.conf for Nginx to serve the frontend.

Setup a reverse proxy so that /api/ requests go to the backend container.

Mount the Nginx config in the Docker container using volumes.

8️⃣ Deploy the Application

Use docker-compose to start all containers: MongoDB, backend, frontend, and Nginx.

Make sure containers are running without errors.

Check the logs of Nginx and other containers for any issues.

9️⃣ Verify the Application

Open a browser and navigate to the EC2 public ip.

The Angular frontend should be live.

API requests should be correctly routed to the backend.

Check connectivity to MongoDB if required.
app live http://13.204.84.180

