# lemoncode_module2
DevOps Bootcamp - Módulo 2: Orquestación de Contenedores (Retos 1-4)

Markdown
# 🏗️ Reto 1: MongoDB en Contenedor

El objetivo de este primer reto fue desplegar una base de datos **MongoDB** utilizando docker, asegurando la persistencia de los datos y permitiendo que un backend de Node.js ejecutándose en local pudiera realizar operaciones CRUD completas

## 🛠️ Configuración del Entorno

Para el despliegue se utilizó un archivo `compose.yml` con las siguientes características técnicas:

* [cite_start]**Versión de MongoDB**: Se utilizó la imagen oficial `mongo:8` (estable)[cite: 5].
* [cite_start]**Red Docker**: Se creó una red de tipo bridge llamada `lemoncode` para aislar el tráfico[cite: 1, 18].
* [cite_start]**Persistencia**: Se configuró un volumen llamado `mongo_data` mapeado a `/data/db` para garantizar que la información no se pierda al reiniciar el contenedor[cite: 11, 15].
* [cite_start]**Mapeo de Puertos**: Se expuso el puerto `27017` del contenedor al host local[cite: 9].

### Archivo de Configuración (`compose.yml`)
```yaml
version: "3.9"

services:
  mongo:
    image: mongo:8
    container_name: mongo
    restart: unless-stopped
    ports:
      - "27017:27017"
    volumes:
      - mongo_data:/data/db
    networks:
      - lemoncode

volumes:
  mongo_data:

networks:
  lemoncode:
    driver: bridge
[cite_start]``` [cite: 2, 5, 11, 18]

---

## 🚀 Despliegue y Verificación

### 1. Levantando el servicio
Se ejecutó el comando para iniciar el contenedor en segundo plano:
```bash
docker compose up -d
[cite_start]``` [cite: 20]

![Reto1: docker compose up -d](./dockercomposeup.png)

### 2. Estado del contenedor y red
[cite_start]Se verificó que el contenedor estuviera corriendo y que la red se hubiera creado correctamente mediante `docker ps` y `docker network ls`[cite: 23, 40].
* [cite_start]**Contenedor**: mongo [cite: 25]
* [cite_start]**Estado**: Up [cite: 26]
* [cite_start]**Puerto**: 27017 [cite: 27]

> **[INSERTA AQUÍ TU CAPTURA DE 'docker ps' Y 'docker network ls']**

---

## ✅ Conexión del Backend y Pruebas CRUD

[cite_start]Se arrancó el backend en local (`npm start`) configurado para apuntar al MongoDB del contenedor[cite: 31, 32].

### Logs de conexión exitosa
[cite_start]El backend confirmó la conexión y la carga de la colección de clases de forma satisfactoria[cite: 35].

> **[INSERTA AQUÍ TU CAPTURA DE LA TERMINAL DE NODE (CONEXIÓN EXITOSA)]**

### Validación de operaciones (REST Client)
[cite_start]Se realizaron pruebas CRUD exitosas (GET, POST, PUT, DELETE) utilizando el cliente REST para interactuar con la API en `http://localhost:5000/api/classes`[cite: 32].

> **[INSERTA AQUÍ TUS CAPTURAS DE POSTMAN/REST CLIENT]**

---
