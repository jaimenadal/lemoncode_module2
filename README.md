# Lemoncode Module 2 - Orquestación de Contenedores

Este repositorio contiene los retos del Módulo 2 del Bootcamp DevOps de Lemoncode, centrados en ejecutar y orquestar contenedores Docker para una aplicación completa: MongoDB, Backend y Frontend.

## Estructura del repositorio

- `reto1/` - MongoDB en contenedor y conexión con backend local.  
- `reto2/` - Dockerización del backend.  
- `reto3/` - Dockerización del frontend.  
- `reto4/` - Orquestación completa con Docker Compose (todos los servicios juntos).

Cada carpeta contiene un README.md con instrucciones detalladas con los entregables requeridos.

## Cómo ejecutar toda la aplicación

Toda la aplicación puede levantarse de forma sencilla con Docker Compose:

```bash
docker compose up -d
```

Esto levantará MongoDB, Backend y Frontend conectados en la red lemoncode-network y con los puertos adecuados:

MongoDB: 27017

Backend: 5000

Frontend: 3000

Luego puedes acceder a la aplicación en tu navegador: http://localhost:3000

Y probar las APIs con Postman apuntando al backend: http://localhost:5000/api/classes.

La red Docker y los volúmenes se crean automáticamente a través del docker-compose.yml.

Para más detalles sobre cada reto, revisa el README.md dentro de cada carpeta retoX/

## Requisitos Previos

- [Docker](https://www.docker.com/get-started) instalado
- [Docker Compose](https://docs.docker.com/compose/install/) instalado
- Node.js y npm para pruebas locales del backend (opcional)
- Postman para probar las APIs
- Extensiones recomendadas (opcional):
  - MongoDB for VS Code o MongoDB Compass para verificar los datos almacenados
