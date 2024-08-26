# Assignment (Own image from scratch)

## 1. Create a node app with express

First I created a node app with express: `npm init`. \
Installed express: `npm install express`. \
Created a simple "app.js" -file that I later changed to index.js. \

## 2. Make sure it works locally

Ran app by command `npm start`.

## 3. Docker init

Ran command: `docker init` and edited the dockerfile suitable to my program. \
For example, since my program ran on root (./), changed the "WORKDIR" to: `WORKDIR ./` \
Added "watch" to "services" in "compose.yaml". \
