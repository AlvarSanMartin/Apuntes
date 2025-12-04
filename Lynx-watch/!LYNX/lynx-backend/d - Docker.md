-- Desactualizado, no creo que lo siga usando
## 1. Creación de la imagen del servicio

```dockerfile
# /notes-service
FROM node:18.7.0
WORKDIR /code
COPY package.json package.json
COPY package-lock.json package-lock.json
RUN npm install
COPY . .
CMD [ "node", "server.js" ]
```

```bash
docker build -t notes-service .
```

## 2. Creación de volúmenes para la BDD mongo y la configuración

``` bash
docker volume create mongodb
docker volume create mongodb_config

docker network create mongodb
```

Lanzar los volúmenes
```bash
docker run -it --rm -d \
-v mongodb:/data/db \ 
-v mongodb_config:/data/configdb \
-p 27017:27017 \
--network mongodb \
--name mongodb mongo
```

Configuración de variables de entorno
``` bash
docker run \
-it --rm -d \
--network mongodb \
--name notes \
-p 8081:8081 \
-e SERVER_PORT=8081 \
-e SERVER_PORT=8081 \
-e DATABASE_CONNECTIONSTRING=mongodb://mongodb:27017/yoda_notes \
notes-service
```