# 🎪 Reto 4: Docker Compose — Todo Junto

El objetivo de este reto es orquestar toda la aplicación (MongoDB, Backend y Frontend) utilizando Docker Compose, permitiendo levantar todos los servicios con un único comando.


## 1. Archivo docker-compose.yml documentado

```yaml
version: "3.9"

services:

  # =========================
  # Servicio MongoDB
  # =========================
  mongo:
    image: mongo:8               # Imagen oficial de MongoDB versión 8
    container_name: mongo        # Nombre del contenedor
    restart: unless-stopped      # Reinicia automáticamente si se cae
    ports:
      - "27017:27017"            # Puerto de MongoDB accesible desde host
    volumes:
      - mongo_data:/data/db      # Volumen persistente para los datos
    networks:
      - lemoncode                # Red compartida para comunicación con backend

  # =========================
  # Servicio Backend API
  # =========================
  topics-api:
    build: ./backend             # Construye la imagen a partir del Dockerfile del backend
    container_name: topics-api   # Nombre del contenedor (coincide con API_URL en frontend)
    restart: unless-stopped
    ports:
      - "5000:5000"              # Puerto de la API accesible desde host
    env_file:
      - .env                     # Variables de entorno para la conexión a MongoDB
    depends_on:
      - mongo                     # Se inicia después de Mongo
    networks:
      - lemoncode

  # =========================
  # Servicio Frontend
  # =========================
  frontend:
    build: ./frontend            # Construye la imagen a partir del Dockerfile del frontend
    container_name: frontend
    restart: unless-stopped
    ports:
      - "3000:3000"              # Puerto accesible desde el navegador
    env_file:
      - .env                     # Variables de entorno para conexión al backend
    depends_on:
      - topics-api               # Se inicia después del backend
    networks:
      - lemoncode

# =========================
# Volúmenes persistentes
# =========================
volumes:
  mongo_data:                     # Volumen para persistir datos de MongoDB

# =========================
# Red compartida
# =========================
networks:
  lemoncode:
    driver: bridge                # Red bridge para que todos los contenedores puedan comunicarse

```
## 2. Archivo .env con variables de entorno
```env
DATABASE_URL=mongodb://mongo:27017
DATABASE_NAME=LemoncodeCourseDb
API_URL=http://topics-api:5000/api/classes
```

## 3. Comando docker-compose up ejecutándose exitosamente
```bash
docker compose up -d --build
```
![Docker Compose up](/img/reto4-compose-up.png)

## 4. Captura de pantalla de todos los servicios corriendo (docker-compose ps)
```bash
docker compose ps
```
Comprueba que los tres servicios (mongo, topics-api, frontend) están activos.

![servicios corriendo](/img/reto4-compose-ps.png)


## 5- Captura de pantalla de la aplicación completa en http://localhost:3000

![aplicación](/img/reto4-screen.png)
