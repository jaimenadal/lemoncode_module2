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

##  2. Construcción de la imagen
### 🐳 Docker Build
docker build -t lemoncode-backend .

![Docker Build](/img/dockerbuild-reto2-def.png)


##  3. Ejecución del contenedor y comprobación
docker run -d --name backend --network node-stack_lemoncode -p 5000:5000 -e DATABASE_URL=mongodb://mongo:27017 -e DATABASE_NAME=LemoncodeCourseDb lemoncode-backend
![Docker Run +ps](/img/dockerrunpslogs.png)


##  4. Verificar que se conecta correctamente a MongoDB
![Docker logs](/img/dockerlogs-reto2-1.png)

##  5. Exponerse el puerto 5000 para que sea accesible

![API](/img/validandoapi.png)
![logs](/img/dockerlogs-reto2.png)
