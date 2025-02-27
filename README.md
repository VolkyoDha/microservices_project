# Docker Compose Setup for Clientes, Productos, and Visualización Apps Using EC2

This setup uses Docker Compose to orchestrate three separate Node.js applications (Clientes, Productos, Visualización) and a MongoDB database. Each application runs in its own container and connects to the shared MongoDB instance.

Made by Carlos Lobo and Paola Solano

## Technologies Used

- Node.js
- Express
- Mongoose
- Docker
- Docker Compose
- MongoDB

## Setup Instructions

1. **Clone the repositories:**
   ```bash
   git clone https://github.com/VolkyoDha/Dock_Clientes DOCK_CLIENTES
   git clone https://github.com/VolkyoDha/Dock_productos DOCK_PRODUCTOS
   git clone https://github.com/VolkyoDha/Dock_Visual DOCK_VISUAL
   ```
2. **Navigate to the directory containing docker-compose.yml file:**

3. **Ensure the necessary Docker images are available:**
   ```bash
   docker pull your_username/dock_productos:latest
   docker pull your_username/dock_clientes:latest
   docker pull your_username/dock_visual:latest
   ```
4. **Build and start the Docker containers:**
   ```bash
   docker-compose up --build
   ```
4. **Access the applications:**

Clientes App: http://localhost:3001
Productos App: http://localhost:3002
Visualización App: http://localhost:3003

## Services Overview

## dock_clientes
    Description: This service handles the entry of client information (name and phone number).
    image: volkyodha/dock_clientes:latest
    Port: 3001
    Environment Variable: MONGO_URL=mongodb://mongo:27017/elysium
## dock_productos
    Description: This service handles the entry of product information (name and price).
    image: volkyodha/dock_productos:latest
    Port: 3002
    Environment Variable: MONGO_URL=mongodb://mongo:27017/elysium
## dock_visual
    Description: This service displays the client and product information in a web interface.
    image: volkyodha/dock_visual:latest
    Port: 3003
    Environment Variable: MONGO_URL=mongodb://mongo:27017/elysium
## mongo
    Description: MongoDB database service is used by the above applications.
    Image: mongo:latest
    Port: 27017
    Volume: mongo-data:/data/db

5. **Stopping the Containers**
```bash
docker-compose down
```
This will stop and remove the containers, but the data in the MongoDB volume will be persisted.


