# React + Vite Dockerized Application

This project demonstrates how to set up and run a React application powered by Vite in a Docker container. It includes live reloading for real-time changes during development.

---

## 🚀 Getting Started

### Prerequisites
Ensure you have the following installed:
- [Docker](https://www.docker.com/)
- [Node.js](https://nodejs.org/) (optional for local testing)

---

## 🛠️ Build and Run the Project in Docker

### 1. Build the Docker Image
To create a Docker image from the provided `Dockerfile`, run:
```bash
docker build -t react-docker .
```

### 2. Run the Docker Container
To start the container and map the application to port `5173`, use:
```bash
docker run -p 5173:5173 -v "$(pwd):/app" -v /app/node_modules react-docker
```

#### Explanation:
- `-p 5173:5173`: Maps port 5173 from the container to your local machine.
- `-v "$(pwd):/app"`: Mounts your local project directory to the `/app` directory in the container.
- `-v /app/node_modules`: Ensures node modules inside the container are used, avoiding conflicts with local modules.

### 3. Access the Application
Open your browser and navigate to:
```
http://localhost:5173
```

---

## 🔄 Real-Time Code Updates in the Container

Vite's Hot Module Replacement (HMR) is configured to detect changes and reload the application automatically. To enable this:

1. **Update the `vite.config.js`** in the project root with (I have already updated):
   ```javascript
   export default {
     server: {
       host: true,
       watch: {
         usePolling: true, // Ensures changes are detected in Docker
       },
     },
   };
   ```

2. Restart the container after saving the changes:
   ```bash
   docker run -p 5173:5173 -v "$(pwd):/app" -v /app/node_modules react-docker
   ```

3. Modify any file, such as `src/App.jsx`, and see the changes reflected in real-time in the browser.

---

## 🛑 Stop the Container
To stop the running container:
1. List the running containers:
   ```bash
   docker ps
   ```

2. Stop the container using its `CONTAINER_ID`:
   ```bash
   docker stop <CONTAINER_ID>
   ```

---

## 🐳 Additional Docker Commands

- **Rebuild the Image**:
   ```bash
   docker build -t react-docker .
   ```

- **Remove Unused Containers**:
   ```bash
   docker rm $(docker ps -a -q)
   ```

- **Remove Unused Images**:
   ```bash
   docker rmi $(docker images -q)
   ```

---

## 📂 Project Structure

```
├── src/
│   ├── App.jsx         # Main React component
│   └── index.jsx       # Entry point for React
├── public/             # Static assets
├── Dockerfile          # Docker configuration
├── package.json        # Dependencies and scripts
├── vite.config.js      # Vite configuration
└── README.md           # Project documentation
```

---

## 📖 Resources
- [Docker Documentation](https://docs.docker.com/)
- [Vite Documentation](https://vitejs.dev/)
- [React Documentation](https://reactjs.org/)
