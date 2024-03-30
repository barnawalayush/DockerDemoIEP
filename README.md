# Docker


### Ques 1. 
Implement a Docker Compose manifest, which creates a container with the database. Override default username and password with the custom ones.

#### MySQLComposeFile.yaml

```http
version: '3.1'
services:
  mySqlDatabase:
    image: mysql
    ports:
      - 8080: 8080
    environment:
      MYSQL_ROOT_PASSWORD: password
```

### Ques 2. 
Pass sensitive (password, etc) and configurable (username, port, etc) variables using .env file.


#### MySQLComposeFile.yaml

```
version: '3.1'
services:
  mySqlDatabase:
    image: mysql
    ports:
      - 8080:${PORT}
    environment:
      MYSQL_ROOT_PASSWORD: ${MYSQL_ROOT_PASSWORD}
```

#### environment.env
```
MYSQL_ROOT_PASSWORD=password
PORT=8080
```

### Ques 3. 
Configure Docker volume to keep the data in case of container re-creation.

#### MySQLComposeFile.yaml
```
version: '3.1'
services:
  mySqlDatabase:
    image: mysql
    ports:
      - 8080:${PORT}
    environment:
      MYSQL_ROOT_PASSWORD: ${MYSQL_ROOT_PASSWORD}
    volumes: 
      - db-data:/data/db
volumes:
  db-data:
    driver: local
```
#### environment.env
```
MYSQL_ROOT_PASSWORD=password
PORT=8080
```
