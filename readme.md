# Assignment (Own image from scratch)

## 1. Create a node app with express

First I created a node app with express: `npm init`. \
Installed express: `npm install express`. \
Created a simple "app.js" -file that I later changed to index.js.

## 2. Make sure it works locally

Ran app by command `npm start`.

## 3. Docker init

Ran command: `docker init` and edited the dockerfile suitable to my program. \
For example, since my program ran on root (./), changed the "WORKDIR" to: `WORKDIR ./` \
Added "watch" to "services" in "compose.yaml": \

```
services:
  server:
    build:
      context: .
    environment:
      NODE_ENV: production
    develop:
      watch:
      - path: ./
        action: sync
        target: ./
    ports:
      - 3000:3000
```

## 4. Test by running `docker compose up --watch`

```
[+] Running 3/0
 ✔ Container docker-server-1         Created                                                             0.0s
 ✔ Container docker-mongo-express-1  Created                                                             0.0s
 ✔ Container docker-mongo-1          Created                                                             0.0s
Attaching to mongo-1, mongo-express-1, server-1
        ⦿ Watch enabled
```

## 5. Build and run

`docker compose build` \
-->`[+] Building 3.1s (13/13) FINISHED`

## 6. Develop your image further

Added mongo and mongo-express to "compose.yaml" in "services":

```
mongo:
    image: mongo
    restart: always
    environment:
      MONGO_INITDB_ROOT_USERNAME: root
      MONGO_INITDB_ROOT_PASSWORD: example

  mongo-express:
    image: mongo-express
    restart: always
    ports:
      - 8081:8081
    environment:
      ME_CONFIG_MONGODB_ADMINUSERNAME: root
      ME_CONFIG_MONGODB_ADMINPASSWORD: example
      ME_CONFIG_MONGODB_URL: mongodb://root:example@mongo:27017/
      ME_CONFIG_BASICAUTH: false
```

After that I pulled with command: `docker compose up` and visited the mongo URL and it worked.
