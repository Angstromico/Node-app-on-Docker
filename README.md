# Node.js App with Docker - Course Example

## Learn Docker, Docker Compose, Multi-Container Projects, Deployment and all about Kubernetes from the ground up!

This is the first example, a simple Node.js web application running in Docker. The app allows users to set and display a course goal through a web interface.

## About the Application

- **Technology Stack**: Node.js with Express.js
- **Purpose**: Simple web app for setting and displaying course goals
- **Features**: 
  - Displays current course goal
  - Form to update the course goal
  - Static CSS styling
  - Runs on port 80

## Docker Setup

### Prerequisites
- Docker installed on your system
- Basic understanding of command line

### Quick Start

1. **Build the Docker image:**
   ```bash
   docker build -t node-course-app .
   ```

2. **Run the container:**
   ```bash
   docker run -p 3000:80 node-course-app
   ```

3. **Access the application:**
   Open your browser and navigate to `http://localhost:3000`

### Docker Commands Reference

| Command | Description |
|---------|-------------|
| `docker build -t node-course-app .` | Build the Docker image with tag `node-course-app` |
| `docker run -p 3000:80 node-course-app` | Run container, mapping port 3000 (host) to port 80 (container) |
| `docker run -d -p 3000:80 --name my-app node-course-app` | Run in detached mode with custom name |
| `docker stop my-app` | Stop the running container |
| `docker rm my-app` | Remove the container |
| `docker rmi node-course-app` | Remove the image |

### Dockerfile Explanation

The `Dockerfile` follows these steps:
1. **Base Image**: Uses `node:18` as the foundation
2. **Working Directory**: Sets `/app` as the working directory
3. **Dependencies**: Copies `package.json` and runs `npm install`
4. **Application Code**: Copies all source files into the container
5. **Port Exposure**: Exposes port 80 (the app's internal port)
6. **Start Command**: Runs `node server.js` to start the application

### Development Workflow

1. **Make changes to your code**
2. **Rebuild the image:**
   ```bash
   docker build -t node-course-app .
   ```
3. **Stop and remove the old container (if running):**
   ```bash
   docker stop my-app && docker rm my-app
   ```
4. **Run the new container:**
   ```bash
   docker run -d -p 3000:80 --name my-app node-course-app
   ```

### Troubleshooting

- **Port already in use**: Change the host port mapping (e.g., `-p 3001:80`)
- **Container not starting**: Check logs with `docker logs my-app`
- **Build issues**: Ensure all files are present and `package.json` is valid

## Project Structure

```
.
├── Dockerfile          # Docker configuration
├── package.json        # Node.js dependencies
├── server.js           # Main application file
├── public/             # Static assets (CSS)
│   └── styles.css
└── README.md           # This file
```
