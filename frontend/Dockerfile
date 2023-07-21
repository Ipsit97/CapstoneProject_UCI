# Use the official Node.js image to build the React app
FROM node:latest as build

# Set the working directory
WORKDIR /app

# Copy the package.json and package-lock.json files
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy all other files from the local current directory to the container
COPY ./ .

# Build the React application
RUN npm run build

# Use the official Nginx base image for the production server
FROM nginx:latest

# Set the working directory
WORKDIR /usr/share/nginx/html

# Copy the built files from the build stage (node) to the Nginx container
COPY --from=build /app/build .

# Expose the production server port (if needed)
EXPOSE 80

# Start Nginx to serve the React application
CMD ["nginx", "-g", "daemon off;"]
