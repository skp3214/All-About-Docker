# Use the official Node.js image based on Alpine Linux as the base image
FROM node:20-alpine

# Create a new group named 'app' and a new system user named 'app' in that group
# This is done to avoid running the app as the root user for security reasons
RUN addgroup app && adduser -S -G app app

# Switch to the newly created user
USER app

# Set the working directory inside the container to /app
WORKDIR /app

# Copy package.json and package-lock.json files to the working directory
COPY package*.json ./

# Temporarily switch to the root user to change ownership of the files
USER root

# Change ownership of all files in the working directory to the 'app' user and group
RUN chown -R app:app .

# Switch back to the 'app' user
USER app

# Install the dependencies specified in package.json
RUN npm install

# Copy the rest of the application code to the working directory
COPY . .

# Expose port 5173 to allow external access to the application
EXPOSE 5173

# Define the command to run the application
CMD ["npm", "run", "dev"]