## 1. Choice of Base Image
The base image used to build containers:
1. Client: ```node``` 
2. Backend: ```node``` 

## 2. Dockerfile directives used in creation for each container

1. Client Dockerfile

```
# Build stage
# Use node:14-slim runtime as a parent image

FROM node:14-slim AS build

# Set the working directory in the container
WORKDIR /app

# Copy package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application code
COPY . .

# Build the app for production
RUN npm run build

# Production stage
FROM node:14-slim

# Set the working directory in the container
WORKDIR /app

# Copy the build output from the build stage
COPY --from=build /app/build /app/build

# Install serve globally (static file server)
RUN npm install -g serve

# Expose the port the app will run on
EXPOSE 3000

# Start the app using serve to serve the production build
CMD ["serve", "-s", "build", "-l", "3000"]

```


2. Backend Dockerfile

```
# Use an official Node runtime as a parent image
FROM node:14 AS build

# Set the working directory in the container
WORKDIR /usr/src/app

# Copy the package.json and package-lock.json files to the container
COPY package*.json ./

# Install application dependencies
RUN npm install

# Copy the rest of the application code to the container
COPY . .

#Add multi-stage build
FROM alpine:3.16.7

WORKDIR /app

RUN apk update && apk add --update nodejs

COPY --from=build /usr/src/app /app

# Expose the port the app runs on
EXPOSE 5000

# Define the command to run your app
CMD ["node", "server.js"]
```
## 3. Docker-compose Networking.

I have created one network called, ```app-network``` that allows the three containers created to communicate.

In this configuration, the backend container is mapped to port 5000 of the host, the client container is mapped to port 3000 of the host, and mongodb container is mapped to port 27017 of the host

```
networks:
  app-network:
    name: app-network
    driver: bridge
```

## 4. Docker-compose volume definition and usage

The Docker Compose file includes volume definitions for MongoDB data storage. The relevant section is as follows:

```
volumes:
  mongo-volume:  
    driver: local
```

## 5. Git workflow used to achieve the task

1. Fork the repository on github.
2. Clone the repository into your local machine.

    ```
    git clone https://github.com/Michael-Otieno/yolo.git 
    ```

3. Added Dockerfile to client and backend application then create the image

5. Create two repositories on docker hub to push the created images

5. Build the images using

    ```
    docker build -t my-username/my-image:v1.0.0 .
    ```

6. Push the images to dockerhub

    ```
    docker push my-username/my-image
    ```

5. Added docker-compose file on the root of the project to containerise the application


6. Add the changes 
    ``` git add . ```

7. Commit the changes: 
    ``` git commit -m "changes" ```

8. Pushed the files to github: 
    ```git push```

