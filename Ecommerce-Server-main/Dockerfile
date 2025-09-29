# Use an official Node.js runtime as a parent image (choose a version you used in development)
FROM node:18-alpine

# Set the working directory in the container
WORKDIR /app

# Copy package.json and package-lock.json first to leverage Docker cache
COPY package*.json ./

# Install app dependencies
RUN npm install

# Copy the rest of the application source code
COPY . .

# Your app runs on port 5000 (change if yours is different)
EXPOSE 5000

# Command to run the application
CMD ["node", "server.js"]