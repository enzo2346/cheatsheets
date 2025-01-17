### Dockerfile:

```Dockerfile
FROM node:21-alpine

RUN apk --no-cache add unzip

RUN npm install -g http-server

WORKDIR /app

COPY webHelp12-all.zip /app/

RUN unzip webHelp12-all.zip

CMD [ "http-server"]
```

## Pull and run the docker image

```bash
docker run -d -p 8080:8080 enzo2346/docs:latest
```

## Push a new version of the docker image

### Build the docker image

```bash
docker build -t docs .
```

### Run the docker image

```bash
docker run -d -p 8080:8080 docs
```

### Login to docker hub

```bash	
docker login -u enzo2346
```

### Tag the docker image

```bash
docker tag docs:latest enzo2346/docs:latest
```

### Push the docker image

```bash
docker push enzo2346/docs:latest
```
