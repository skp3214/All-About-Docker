# Docker Learning.

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