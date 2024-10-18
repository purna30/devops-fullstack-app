FROM node:14.17.0

# Set working directory
WORKDIR /app

# Copy package.json and package-lock.json
COPY package*.json ./

# Install frontend dependencies
RUN npm install

# Copy the rest of the application code
COPY . .

# Build the React app
RUN npm run build

# Expose the port the app will run on
EXPOSE 3000

# Start the React app
CMD ["npm", "start"]

# # Stage 1: Build the React app
# FROM node:14-alpine AS build

# # Set working directory
# WORKDIR /app

# # Copy package.json and package-lock.json
# COPY package*.json ./

# # Install dependencies
# RUN npm install --production

# # Copy the rest of the application code
# COPY . .

# # Build the React app for production
# RUN npm run build

# # Stage 2: Serve the app with Nginx
# FROM nginx:alpine

# # Copy the build output to Nginx's default HTML directory
# COPY --from=build /app/build /usr/share/nginx/html

# # Expose port 80 for Nginx
# EXPOSE 80

# # Start Nginx server
# CMD ["nginx", "-g", "daemon off;"]
