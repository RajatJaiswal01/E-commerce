# STAGE 1: Build the React application
FROM node:18-alpine as builder

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .
# This command creates the static files in the /app/build folder
RUN npm run build

# STAGE 2: Serve the built application with Nginx
FROM nginx:stable-alpine

# Copy the static files from the 'builder' stage
COPY --from=builder /app/build /usr/share/nginx/html

# When a request comes in, Nginx will serve index.html
# This allows React Router to handle the routing
COPY nginx.conf /etc/nginx/conf.d/default.conf

# Tell Docker that the container listens on port 80
EXPOSE 80

# The command to start Nginx when the container launches
CMD ["nginx", "-g", "daemon off;"]