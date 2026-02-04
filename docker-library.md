# Docker 

## Docker Hub – Authentication

1. `docker login`
   Logs into Docker Hub interactively (prompts for username and password)

2. `docker login -u <username> --password-stdin`
   Secure login method using stdin (recommended for CI/CD)

3. `docker logout`
   Logs out from Docker Hub on the current machine

---

## Docker Image Build

4. `docker build -t <image-name>:<tag> .`
   Builds a Docker image from the Dockerfile in the current directory

5. `docker buildx build --platform=linux/amd64 -t <image-name>:<tag> .`
   Builds an image for a specific CPU architecture (used when building on Apple Silicon for EC2)

6. `docker buildx build --platform=linux/amd64 -t <image-name>:<tag> --push .`
   Builds and pushes an amd64 image directly to Docker Hub

---

## Docker Hub – Push & Pull

7. `docker tag <local-image>:<tag> <username>/<repo>:<tag>`
   Tags a local image so it can be pushed to Docker Hub

8. `docker push <username>/<repo>:<tag>`
   Pushes a Docker image to Docker Hub

9. `docker pull <username>/<repo>:<tag>`
   Pulls an image from Docker Hub to the local machine or EC2 instance

---

## Docker Image & Container Inspection

10. `docker images`
    Lists all Docker images available locally

11. `docker ps`
    Lists running containers

12. `docker ps -a`
    Lists all containers (running and stopped)

13. `docker logs <container-name-or-id>`
    Shows logs from a running or stopped container

14. `docker inspect <container-name-or-id>`
    Displays detailed configuration and metadata for a container

---

## Docker Run / Stop / Remove

15. `docker run -d --name <container-name> -p 8080:8080 <image>`
    Runs a container in detached mode and maps ports

16. `docker run --env-file .env -e KEY=value <image>`
    Runs a container with environment variables injected

17. `docker stop <container-name-or-id>`
    Gracefully stops a running container

18. `docker kill <container-name-or-id>`
    Force-stops a container immediately (used in labs)

19. `docker rm <container-name-or-id>`
    Removes a stopped container

20. `docker rmi <image-name>:<tag>`
    Removes a local Docker image

---

## Docker Daemon / System

21. `sudo systemctl start docker`
    Starts the Docker daemon (common on EC2)

22. `sudo systemctl enable docker`
    Ensures Docker starts automatically on reboot

23. `docker version`
    Confirms Docker client and daemon are installed and reachable

---

## curl (Testing Containers / Servers)

24. `curl http://localhost:8080`
    Tests a locally running Docker container

25. `curl http://<EC2-PUBLIC-IP>:8080`
    Tests a Docker container running on an EC2 instance

26. `curl -i http://<EC2-PUBLIC-IP>:8080`
    Shows HTTP headers and response (useful for debugging)

27. `curl -u username:password http://<EC2-PUBLIC-IP>:8080`
    Tests endpoints protected with HTTP Basic Auth

---

## Common Naming Reminder

28. `<username>/<repository>:<tag>`
    Required format for Docker Hub images (e.g., `ddugar/fragments:lab-6`)

---
