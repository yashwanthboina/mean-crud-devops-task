# Frontend Dockerfile (multi-stage build)

# Stage 1: Build Angular app
FROM node:18-alpine AS build

WORKDIR /app

# Install dependencies
COPY package*.json ./
RUN npm install

# Copy source and build
COPY . .
RUN npm run build --prod

# Stage 2: Serve with Nginx
FROM nginx:alpine

# Remove default nginx static content
RUN rm -rf /usr/share/nginx/html/*

# ⚠️ IMPORTANT:
# Open frontend/angular.json and check outputPath under "architect > build > options"
# Example: "outputPath": "dist/frontend"  OR "dist/angular-crud"
# Replace <dist-folder> below with that folder name.

COPY --from=build /app/dist/frontend/ /usr/share/nginx/html/

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
