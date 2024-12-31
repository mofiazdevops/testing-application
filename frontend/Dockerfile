# Stage first
FROM node:21 AS frontend-builder

# Set working dir
WORKDIR /app

# Copy the  package.json and package-lock.json for dependency installation
COPY package*.json ./

COPY . .

# Install dependencies
RUN npm i

# Stage 2
FROM node:21-alpine
# set working dir
WORKDIR /app

# Copy the above satge directory < /app > where all dependency install
COPY --from=frontend-builder /app .

# Copy .env.sample file from .env.local
COPY .env.sample .env.local

# Port expose 5173 for the node.js application
EXPOSE 5173

# Define the default command to run the applicationin development
CMD ["npm", "run", "dev","--","--host"]
