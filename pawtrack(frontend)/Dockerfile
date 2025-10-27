# Stage 1: Build the React app
FROM node:18 AS build

WORKDIR /app

# Copy package.json and install dependencies
COPY package*.json ./
RUN npm install

# Copy the rest of the app and build it
COPY . .
RUN npm run build

# Stage 2: Serve with nginx
FROM nginx:alpine

# Copy build files from previous stage to nginx html folder
COPY --from=build /app/build /usr/share/nginx/html

# Expose port 80 (default HTTP)
EXPOSE 80

# Start nginx
CMD ["nginx", "-g", "daemon off;"]
