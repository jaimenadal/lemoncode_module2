# 🐳 Reto 2 – Dockerizar Backend

## Objetivo
Dockerizar el backend Node.js, ejecutarlo en un contenedor conectado a MongoDB mediante una red Docker y verificar su funcionamiento.

---

## 1. Dockerfile

```dockerfile
FROM node:18-alpine
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
EXPOSE 5000
CMD ["npm", "start"]

```
