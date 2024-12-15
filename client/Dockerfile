# Build stage
FROM node:14-slim AS build

# Set the working directory in the container
WORKDIR /usr/src/app

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
COPY --from=build /usr/src/app/build ./build

# Install a lightweight HTTP server to serve static files
RUN npm install -g serve

# Expose the port the app will run on
EXPOSE 3000

# Serve the production build
CMD ["serve", "-s", "build", "-l", "3000"]







# # Build stage






# FROM node:14-slim AS build

# # Set the working directory in the container
# WORKDIR /usr/src/app


# # Copy package.json and package-lock.json
# COPY package*.json ./

# # Install dependencies
# RUN npm install

# # Copy the rest of the application code
# COPY . .

# # Build the app for production
# RUN npm run build

# # Production stage
# FROM node:14-slim

# # Set the working directory in the container
# WORKDIR /app

# # Copy the build output from the build stage
# COPY --from=build /usr/src/app /app


# # Install serve globally (static file server)
# RUN npm install --production

# # Expose the port the app will run on
# EXPOSE 3000

# # Start the app using serve to serve the production build
# CMD ["npm", "start"]
