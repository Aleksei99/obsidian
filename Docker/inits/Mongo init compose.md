#creation_date:  2025-01-03 15:00
#modification_date: Friday 3rd January 2025 15:00:45
Error generating daily quote
#mongo #mongo-express #docker

```yml
version: '3.8'

services:
  mongo:
    image: mongo:latest
    container_name: mongodb
    environment:
      MONGO_INITDB_ROOT_USERNAME: admin
      MONGO_INITDB_ROOT_PASSWORD: password
    ports:
      - "27017:27017"
    volumes:
      - mongo-data:/data/db
  

  mongo-express:
    image: mongo-express:latest
    container_name: mongo-express
    environment:
      ME_CONFIG_MONGODB_ADMINUSERNAME: admin
      ME_CONFIG_MONGODB_ADMINPASSWORD: password
      ME_CONFIG_MONGODB_SERVER: mongodb
      ME_CONFIG_MONGODB_PORT: 27017
      ME_CONFIG_MONGODB_ENABLE_ADMIN: 'true'
      ME_CONFIG_BASICAUTH_USERNAME: admin
      ME_CONFIG_BASICAUTH_PASSWORD: password
    ports:
      - "8081:8081"
    depends_on:
      - mongo

volumes:
  mongo-data:
    driver: local
```