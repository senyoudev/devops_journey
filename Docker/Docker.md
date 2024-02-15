## What is Docker?

Docker is a platform for developing, shipping, and running applications using containerization. It allows you to package your application and its dependencies into a standardized unit for software development. 

## How to use Docker ?

# Containerize your application
You Should use DockerFile to create a container image for your application.

# Example of a DockerFile for Node.js application
```Dockerfile
# Use the official image as a parent image
FROM node:12
WORKDIR /usr/src/app
COPY package*.json ./
RUN npm install
COPY . .
EXPOSE 8080
CMD [ "node", "server.js" ]
```

# Build the container image
```bash
docker build -t my-nodejs-app .
```

# Run the container
```bash
docker run -p 4000:8080 -d my-nodejs-app
```

# Push the container image to a registry
```bash
docker tag my-nodejs-app username/my-nodejs-app
docker push username/my-nodejs-app
```

# UPDATE the container image
```bash
docker build -t my-nodejs-app:2.0 .
docker tag my-nodejs-app:2.0 username/my-nodejs-app:2.0
docker push username/my-nodejs-app:2.0
```

# Pull the container image from the registry
```bash
docker pull username/my-nodejs-app
```

# Remove the old container 
```bash
docker ps
docker stop <container_id>
docker rm <container_id>
```

# Persist the data
```bash
docker run -p 4000:8080 -d -v /path/to/your/data:/usr/src/app/data my-nodejs-app // this will persist the data in the /path/to/your/data directory
```

# Check the logs
```bash
docker logs <container_id>
```

# Use bind mounts
```bash
docker run -it --mount type=bind,src="$(pwd)",target=/src ubuntu bash
```

# Use volumes
```bash
docker run -d -v myvol:/app nginx
```

# Development Containers

let's imagine that you want to develop a nodejs without installing nodejs on your machine, you can use a development container.
To do this, you can use volumes to mount the source code into the container.

Example of volumes in a development container
```bash
docker run -v /path/to/your/app:/usr/src/app -p 4000:8080 -d my-nodejs-app
```

# Docker-compose

Docker-compose is a tool for defining and running multi-container Docker applications. With Compose, you use a YAML file to configure your application's services. Then, with a single command, you create and start all the services from your configuration.

Example of a docker-compose file
```yaml
version: '3'
services:
  web:
    build: .
    ports:
      - "5000:5000"
    volumes:
      - .:/code
    environment:
      FLASK_ENV: development
  redis:
    image: "redis:alpine"
```



