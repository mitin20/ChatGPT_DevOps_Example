#Node.js Dockerfile with base image Node

FROM node:12.4.0-alpine

# Create app directory
WORKDIR /src

# Copy package.json and package-lock.json
COPY src/* ./

# Install
RUN npm install

# Bundle app source
COPY . .

# Expose port
EXPOSE  3000

#Startup command
ENTRYPOINT ["node","index.js"]
