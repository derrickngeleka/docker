# --- Stage 1: Build React/Vite app ---
FROM node:25-alpine AS build

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .
RUN npm run build



# --- Stage 2: Serve with tiny NGINX image ---
FROM nginx:alpine AS final

# Copy built dist folder to Nginx’s public HTML directory
COPY --from=build /app/dist /usr/share/nginx/html

# Expose port 80 (the default Nginx web server port)
EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
