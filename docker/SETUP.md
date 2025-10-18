# Docker Setup Documentation

## Prerequisites
- Docker installed on your system

## Overview

The Docker setup consists of two main containers:
- **afs-server-main**: The main file server (port 5000)
- **afs-client**: The client application


## Quick Start

### 1. Build and Start Containers

```bash
# Navigate to the docker directory
cd docker

# Build and start all services
docker compose up -d

# Or build and start with logs visible
docker compose up
```

### 2. Verify Containers are Running

```bash
docker ps
```

### 3. Stopping Containers

```bash
# Stop all services
docker compose down
```

```bash
# Stop and remove volumes (WARNING: This will delete data)
docker compose down -v
```

### Restarting Containers

```bash
# Restart all services
docker compose restart

# Restart specific service
docker compose restart afs-server-main
```

## Accessing Containers

### Enter a Running Container

```bash
# Or use docker directly
docker exec -it afs-server-main-main bash
docker exec -it afs-client bash
```

## Monitoring and Debugging

### Check Container Status

```bash
# View all containers (running and stopped)
docker compose ps -a

# Check container logs
docker compose logs afs-server-main
docker compose logs afs_client

# Follow logs in real-time
docker compose logs -f afs-server-main
```

### Container Health Checks

```bash
# Check if containers are responding
docker exec afs-server-main ping -c 3 afs-client
docker exec afs-client ping -c 3 afs-server-main
```

## Data Management

### Accessing Host Data Volumes

The containers mount data from the host system:

- **Server data**: `./data/afs_server_main` → `/data` in container
- **Client data**: `./data/afs_client` → `/data` in container
