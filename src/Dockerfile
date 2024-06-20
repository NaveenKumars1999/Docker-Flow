# Stage 1: Build the Angular application
FROM node:18.17.1 as build

# Install Angular CLI globally
# RUN npm install -g @angular/cli

# Set the working directory
# WORKDIR /app

# Copy the package.json and package-lock.json files
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application code
COPY . .

# Build the Angular application
# RUN ng build --configuration=production

# Verify the build output directory
# RUN ls -l /dist/DockerAngular

# Stage 2: Serve the Angular application using Nginx
FROM nginx:alpine

# Copy the built Angular application from the previous stage
COPY --from=build /dist/docker-angular /usr/share/nginx/html

# Copy the default Nginx configuration file
COPY nginx.conf /etc/nginx/conf.d/default.conf

# Expose port 4200 (if necessary, though it's not directly used by Nginx)
EXPOSE 4200

# Start Nginx server
CMD ["nginx", "-g", "daemon off;"]
