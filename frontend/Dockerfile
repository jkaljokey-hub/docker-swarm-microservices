# Build stage
FROM node:20 AS builder
WORKDIR /app

# Copy package files
COPY movesapp/package*.json ./
RUN npm install

# Copy the entire Next.js project
COPY movesapp/ ./

# Build static export
RUN npm run build

# Runtime stage
FROM nginx:alpine

COPY nginx.conf /etc/nginx/conf.d/default.conf

# Copy static export output
COPY --from=builder /app/out /usr/share/nginx/html

EXPOSE 80

