

# React + Vite Dockerized Application with Docker Compose

This project demonstrates how to set up and run a React application powered by Vite using Docker Compose. It includes real-time code synchronization and **watch mode** for seamless development.

---

## 🚀 Getting Started

### Prerequisites
Ensure you have the following installed:
- [Docker](https://www.docker.com/)
- [Docker Compose](https://docs.docker.com/compose/)

---

## 🛠️ Build and Run the Project with Docker Compose

### 1. Clone the Repository
```bash
git clone <repository-url>
cd <repository-folder>
```

### 2. Start the Services in Watch Mode
Run the following command to build and start the services with watch mode enabled:
```bash
docker compose up
```

- The `docker-compose.yml` file is configured to:
  - Sync files in the `./web` directory to `/src/web` in the container.
  - Trigger live synchronization when files are changed.
  - Rebuild the container automatically when `package.json` or dependencies are modified.

### 3. Access the Application
Open your browser and navigate to:
```
http://localhost:5173
```

---

## 🔄 Real-Time Code Updates with Watch Mode

The `docker-compose.yml` file uses the following watch configuration:
```yaml
develop:
  watch:
    - action: sync
      path: ./web
      target: /src/web
      ignore:
        - node_modules/
    - action: rebuild
      path: package.json
```

### How It Works:
1. **Sync Mode**: Changes to files in `./web` are immediately reflected in the `/src/web` directory inside the container.
2. **Rebuild Mode**: Modifications to `package.json` automatically rebuild the container to reflect dependency updates.

#### Test It:
- Modify any file (e.g., `src/App.jsx`) to see instant updates in the browser.
- Update dependencies in `package.json` and observe the container rebuilding.

---

## 🛑 Stop the Services
To stop the running services:
```bash
docker compose down
```

---

## 📂 Project Structure

```
├── web/
│   ├── src/
│   │   ├── App.jsx         # Main React component
│   │   └── index.jsx       # Entry point for React
│   ├── public/             # Static assets
│   ├── Dockerfile          # Docker configuration for the web service
│   ├── package.json        # Dependencies and scripts
│   └── vite.config.js      # Vite configuration
├── docker-compose.yml      # Docker Compose configuration
└── README.md               # Project documentation
```

---

## 📖 Useful Commands

### Start Services in Watch Mode
```bash
docker compose up
```

### Rebuild Services Manually
```bash
docker compose up --build
```

### Stop Services
```bash
docker compose down
```

### View Logs
```bash
docker compose logs
```

---

## 📖 Resources
- [Docker Documentation](https://docs.docker.com/)
- [Docker Compose Documentation](https://docs.docker.com/compose/)
- [Vite Documentation](https://vitejs.dev/)
- [React Documentation](https://reactjs.org/)

---
