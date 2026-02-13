# 🐳 Reto 2 – Dockerizar Backend

## Objetivo
Dockerizar el backend Node.js, ejecutarlo en un contenedor conectado a MongoDB mediante una red Docker y verificar su funcionamiento.

---

## 1. Dockerfile

![Dockerfile](/img/dockerfile-reto2.png)

##  2. Construcción de la imagen

docker build -t lemoncode-backend .
### 🐳 Docker Build
![Docker Build](/img/docker-build.png)


##  3. Ejecución del contenedor y comprobación
docker run -d --name backend --network node-stack_lemoncode -p 5000:5000 -e DATABASE_URL=mongodb://mongo:27017 -e DATABASE_NAME=LemoncodeCourseDb lemoncode-backend

