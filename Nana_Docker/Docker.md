# Docker Complete Guide - Nana Docker

## Introduction

### Course Outline

1. **What is Docker? What is a Container?**
2. **Docker vs Virtual Machine**
3. **Docker Installation**
4. **Main Commands**
5. **Debugging a Container**
6. **Volumes - Persisting Data**
7. **Developing with Containers**
8. **Docker Compose - Running Multiple Services**
9. **Dockerfile - Building Own Docker Image**
10. **Private Docker Repository (AWS)**
11. **Deploying the Containerized App**
12. **Volumes Demo**

---

## Class 1: Container Fundamentals

### 1. What is a Container?

**Definition**: A way to package application with all the necessary dependencies and configuration.

**Characteristics**:

- **Portable Artifact**: Easily shared and moved around
- **Efficiency**: Makes development and deployment more efficient

### 2. Where do Containers Live?

**Container Repositories**:

- **Public Repository**: [DockerHub](https://hub.docker.com/)
- **Private Repositories**: For proprietary applications
- **Examples**: postgres, redis, nodejs, nginx

### 3. Problems Before Containers

**Issues**:

- **Installation Process**: Different on each OS environment
- **Error Prone**: Many steps where something could go wrong
- **Binary Installation**: Had to install binaries on different machines for projects to run

### 4. Benefits After Containers

**Advantages**:

- **Isolated Environment**: Own isolated environment
- **Pre-configured**: Packaged with all needed configuration
- **One Command**: One command to install the app
- **Version Management**: Run same app with 2 different versions

**Key Points**:

- Container has configurations and start script
- Just need to know which container to find from Docker Hub
- Developers and operations work together to package applications
- No environmental configuration needed on server except Docker runtime

---

## Class 2: Container Technical Details

### What is a Container Technically?

**Structure**:

- **Layers of Images**: Mostly Alpine Linux
- **Base Image**: Mostly Linux base image (small in size)
- **Application Image**: Application image on top

### Practical Example

**Commands**:

1. **Search**: In Docker Hub search for postgresql
2. **Run**: `docker run <image name and version>`
   - If version not given, Docker downloads the latest

**Key Terms**:

- **Docker Image**: The actual package or artifact, which is movable
- **Container**: An image which has been started in a machine

**Check Running Containers**:

```bash
docker ps  # See running containers
```

---

## Class 4: Docker vs Virtual Machines

### Architecture Comparison

**Docker**:

- **OS Kernel Layer**: Communicates with hardware
- **Applications Layer**: Based on kernel
- **Virtualization**: Docker virtualizes the Application layer
- **Kernel Usage**: Uses the kernel of the host

**Virtual Machine**:

- **Virtualization**: VM virtualizes the OS
- **Own Kernel**: Has its own OS kernel on top of the host kernel

---

## Class 6: Images and Containers

### Key Differences

1. **Container**: Running environment for image
2. **Virtual File System**: Container has virtual file system
3. **Port Binding**: Talk to application running inside container (port 5000)
4. **Application Images**: postgres, redis, mongo, etc.

---

## Class 7: Essential Docker Commands

### Basic Commands

```bash
# Pull image from Docker Hub
docker pull <image name>

# View existing images
docker images

# Create container and run image
docker run <image name>

# Check running Docker containers
docker ps

# Run container in detached mode
docker run -d redis

# Stop a container
docker stop <id>

# Start a container
docker start <id>
```

### Port Binding

**Purpose**: A Docker container runs in a specific port. To run 2 different versions of the same image, we need port binding.

```bash
# Port binding example
docker run -p6000:6379 redis
# p6000: Host machine's dedicated port
# 6379: Container image port
```

### Advanced Commands

```bash
# Name the container
docker run -d -p6001:6379 --name redis-older redis:6.0

# View container logs
docker logs <container name or id>

# Execute commands inside container
docker exec -it <container id> /bin/bash
# Then: ls -> pwd -> cd / -> ls -> env ...etc

# Remove image from system
docker image rm <image id>
```

---

## Project Implementation

*Project details and implementation steps would be covered in the actual course.*
