# 🎨 Reto 3: Dockerizar el Frontend

---

1. **Archivo Dockerfile del frontend**  

```dockerfile
# Imagen base ligera de Node.js
FROM node:20-alpine

# Crear directorio de trabajo dentro del contenedor
WORKDIR /app

# Copiar archivos de dependencias
COPY package*.json ./

# Instalar dependencias
RUN npm install

# Copiar el resto del código fuente
COPY . .

# Exponer el puerto 3000
EXPOSE 3000

# Comando para iniciar el servidor
CMD ["node", "server.js"]
```

2. **Archivo `.env` con variables de entorno**  
   ```env
   API_URL=http://topics-api:5000/api/classes

