# Use the official Nginx image as the base image
FROM nginx:latest

# Copy the files from the local directory into the container's default Nginx web root directory
COPY . /usr/share/nginx/html

# Expose port 80 to allow incoming HTTP traffic
EXPOSE 80

# Start Nginx server on container startup
CMD ["nginx", "-g", "daemon off;"]