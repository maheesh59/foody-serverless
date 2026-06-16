# Use a lightweight Node.js base image
FROM node:18-alpine

# Set working directory inside the container
WORKDIR /usr/src/app

# Copy package management files
COPY package*.json ./

# Install application dependencies
RUN npm install --production

# Copy the rest of the application backend code
COPY . .

# Expose the internal port your server listens on (typically 5000 or 8080)
EXPOSE 5001

# Start the Node application
CMD ["node", "index.js"]
