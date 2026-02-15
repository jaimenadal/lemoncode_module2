# Dockerfile
# 1. Imagen base
FROM node:20-alpine

# 2. Directorio de trabajo dentro del contenedor
WORKDIR /app

# 3. Copiar package.json y package-lock.json para instalar dependencias
COPY package*.json ./

# 4. Instalar dependencias
RUN npm install

# 5. Copiar el resto del código
COPY . .

# 6. Exponer puerto 3000
EXPOSE 3000

# 7. Comando para iniciar la app
CMD ["npm", "start"]

