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
2. **Comando para construir la imagen del frontend**  

docker build -t frontend .
![Docker Build](/img/dockerbuild-reto3.png)


3. **Comando para ejecutar el contenedor del frontend**  

docker run -d --name frontend --network node-stack_lemoncode -p 3000:3000 --env-file .env lemoncode-frontend

![Docker run](/img/dockerun-reto3.png)

4. **Archivo `.env` con variables de entorno**  
   ```env
   API_URL=http://topics-api:5000/api/classes


5. **Verificación de conectividad con el backend**
![Verificar conect](/img/verify-reto3.png)


## 🔎 Notas adicionales

Durante la implementación fue necesario modificar el nombre del contenedor del backend.

En el reto anterior el backend fue creado con el nombre `backend`, pero en este reto el enunciado especifica que el frontend debe conectarse a:

http://topics-api:5000/api/classes

Por este motivo, se cambió el nombre del contenedor backend a `topics-api` para cumplir exactamente con lo solicitado en el enunciado y permitir la correcta resolución DNS dentro de la red docker.

Este cambio asegura que el frontend pueda resolver correctamente el hostname `topics-api` dentro de la red `node-stack_lemoncode`.

