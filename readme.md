# Docker Learning.
## [JavaScriptMastery Youtube Channel Docker Guide](/jsmguide.md) [↗](https://www.youtube.com/c/JavaScriptMastery)


## Docker
`Docker` is an open-source platform that automates the deployment, scaling, and management of applications using containerization. `Containers` are lightweight, portable, and self-sufficient units that include everything needed to run a piece of software, including the code, runtime, libraries, and system tools. This ensures that the application runs consistently across different environments.

Key features of Docker:

- **Portability**: Containers can run on any system that supports Docker, ensuring consistent behavior across different environments.
- **Isolation**: Each container runs in its own isolated environment, which helps in avoiding conflicts between applications.
- **Efficiency**: Containers share the host system's kernel and resources, making them more lightweight compared to traditional virtual machines.
- **Scalability**: Docker makes it easy to scale applications up or down by adding or removing containers.
Docker is widely used for developing, shipping, and running applications in a consistent and efficient manner.

## Difference Between Docker Image and Container.

### Docker Image
- **Definition**: A Docker image is a lightweight, standalone, and executable software package that includes everything needed to run a piece of software, such as the code, runtime, libraries, environment variables, and configuration files.
- **Immutability**: Images are immutable, meaning once they are created, they cannot be changed.
- **Layers**: Images are built in layers, where each layer represents a set of file changes or additions.
- **Usage**: Images are used to create containers. They can be shared and distributed via Docker registries like Docker Hub.

### Docker Container
- **Definition**: A Docker container is a runtime instance of a Docker image. It is a lightweight, portable, and self-sufficient unit that can run applications in isolation.
- **Mutability**: Containers are mutable, meaning they can be started, stopped, moved, and deleted. Changes made to a running container do not affect the original image.
- **Isolation**: Containers provide process and filesystem isolation, ensuring that applications run in their own environment without interfering with each other.
- **Usage**: Containers are used to run applications consistently across different environments. They can be scaled up or down easily by adding or removing containers.

In summary, a Docker image is a blueprint for creating containers, while a Docker container is a running instance of that image.

---
## Docker Vs Docker Compose
### [Docker](/react-docker/README.md)
- **Purpose**: A platform to create, manage, and run containers.
- **Primary Use**: Runs a single container per command (e.g., `docker run`, `docker build`).
- **Scope**: Focused on individual containers.
- **Configuration**: Requires manual configuration for each container (e.g., networking, volumes).
- **Commands**: Operates with direct `docker` commands (e.g., `docker build`, `docker run`, `docker stop`).
- **Example Use Case**: Running a single instance of a React app.

---

### [Docker Compose](/react-docker-compose/README.md)
- **Purpose**: A tool to define and manage multi-container Docker applications.
- **Primary Use**: Runs multiple containers defined in a YAML file (`docker-compose.yml`).
- **Scope**: Manages multiple services (e.g., web, database, cache) as a single application.
- **Configuration**: Centralized configuration using a `docker-compose.yml` file.
- **Commands**: Simplifies multi-container management (e.g., `docker compose up`, `docker compose down`).
- **Example Use Case**: Running a React app with a backend API and database simultaneously.

---

### **Key Differences**
| Feature                | Docker                      | Docker Compose               |
|------------------------|-----------------------------|-----------------------------|
| **Focus**             | Single container            | Multi-container applications |
| **Configuration**     | Command-line or Dockerfile  | `docker-compose.yml`         |
| **Ease of Use**       | Requires multiple commands  | Single command to manage all |
| **Networking**        | Must link containers manually | Auto-configured networks     |
| **Usage**             | Standalone container tasks  | Applications with dependencies (e.g., frontend + backend + DB) |

---

### **Summary**
- Use **Docker** for managing individual containers.
- Use **Docker Compose** for orchestrating multi-container environments with ease.

---

## **Volumes**
Volumes are a Docker feature used to manage and persist data beyond the lifecycle of containers.

### **Purpose**
- Store and share data between containers.
- Persist data even if a container is deleted.

### **Types of Volumes**
1. **Anonymous Volumes**: Automatically created and managed by Docker.
   - Example: `docker run -v /app/data my-app`
   - The volume is unnamed and only accessible by this container.

2. **Named Volumes**: Explicitly created with a specific name.
   - Example: `docker volume create my-volume`
   - Accessible by multiple containers.
   - Managed through Docker CLI.

3. **Bind Mounts**: Maps a host machine directory to a container directory.
   - Example: `docker run -v $(pwd):/app my-app`
   - Useful for development (real-time file changes).

### **How to Use Volumes**
1. **CLI Commands**:
   - Create a volume: `docker volume create my-volume`
   - List volumes: `docker volume ls`
   - Remove a volume: `docker volume rm my-volume`

2. **In `docker-compose.yml`**:
```yaml
volumes:
  my-volume:
    driver: local

services:
  app:
    image: my-app
    volumes:
      - my-volume:/app/data
```

### **Benefits**
- Decouples data from containers.
- Easier backups and restoration.
- Increased performance for data-heavy applications.

---

## **Networks**
Networks allow Docker containers to communicate with each other and optionally with the host system.

### **Purpose**
- Isolate and control container communication.
- Connect containers across multiple hosts (using external tools like Docker Swarm).

### **Types of Networks**
1. **Bridge Network** (Default):
   - Allows containers to communicate on the same host.
   - Used when running standalone containers (e.g., `docker run`).

2. **Host Network**:
   - Bypasses Docker's network isolation and uses the host machine's network stack.
   - Faster but less secure.
   - Example: `docker run --network host my-app`

3. **Overlay Network**:
   - Enables communication between containers across multiple hosts.
   - Requires Docker Swarm or other orchestrators.

4. **None Network**:
   - Disables networking for the container.
   - Example: `docker run --network none my-app`

### **How to Use Networks**
1. **CLI Commands**:
   - Create a network: `docker network create my-network`
   - List networks: `docker network ls`
   - Inspect a network: `docker network inspect my-network`
   - Remove a network: `docker network rm my-network`

2. **In `docker-compose.yml`**:
```yaml
networks:
  my-network:
    driver: bridge

services:
  app:
    image: my-app
    networks:
      - my-network
  db:
    image: my-db
    networks:
      - my-network
```

### **Benefits**
- Isolates traffic for better security.
- Simplifies container-to-container communication.
- Offers flexibility for scaling and managing services.
