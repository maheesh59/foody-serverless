# --- Stage 1: Build the React application ---
FROM node:18-alpine AS builder
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

# --- Stage 2: Serve the assets using Nginx ---
FROM nginx:1.25-alpine

# Copy the build output from Stage 1 to Nginx's public directory
COPY --from=builder /app/build /usr/share/nginx/html

# Copy a custom Nginx config to handle React Router client-side routing safely
COPY nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
