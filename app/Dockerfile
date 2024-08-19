# Use an official Node.js runtime as a parent image
FROM node:18-alpine

# Set the working directory in the container
WORKDIR /app

# Copy the package.json and install dependencies
COPY package.json yarn.lock ./
RUN yarn install --frozen-lockfile

# Copy the rest of the application code
COPY . .

# Build the TypeScript code
RUN yarn build

# Expose port 3000 to the outside world
EXPOSE 3000

# Run the app
CMD ["yarn", "start"]
