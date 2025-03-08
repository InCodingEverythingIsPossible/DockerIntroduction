# Specify a base image
FROM node:14-alpine

# Specify working directory
WORKDIR '/app'

# Install some depenendencies
COPY ./package.json ./
RUN npm install

# Copy changes in source code
COPY ./ ./

# Default command
CMD ["npm", "start"]