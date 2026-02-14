# Usamos una imagen ligera de Node.js
FROM node:18-alpine

# Creamos el directorio de trabajo
WORKDIR /app

# Copiamos archivos de dependencias y las instalamos
COPY package*.json ./
RUN npm install

# Copiamos el resto del código fuente
COPY . .

# Exponemos el puerto que utiliza la API
EXPOSE 5000

# Comando para arrancar la aplicación
CMD ["npm", "start"]
