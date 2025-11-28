# Backend Dockerfile

FROM node:18-alpine

# Create app directory
WORKDIR /app

# Install dependencies first
COPY package*.json ./
RUN npm install --only=production

# Copy rest of backend code
COPY . .

# Expose backend port (the Node server uses 8080 in most tutorials)
EXPOSE 8080

# Start the server
CMD ["node", "server.js"]
