FROM node:14-alpine

WORKDIR /usr/src/app

# Copy package.json and package-lock.json first to leverage Docker cache
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application code
COPY . .

# Build the React application using build arguments
ARG REACT_APP_AUTHENTICATION_SERVICE_URL
ARG REACT_APP_COMMON_DATA_SERVICE_URL
ARG REACT_APP_PAYMENT_SERVICE_URL
ARG REACT_APP_SEARCH_SUGGESTION_SERVICE_URL

RUN npm run build

# Expose the port the app will run on
EXPOSE 3000

# Serve the React app
CMD ["npm", "start"]
