FROM node:20-alpine3.21 AS builder
WORKDIR /opt/server
COPY package.json .
COPY *.js .
RUN npm install

FROM node:20-alpine3.21
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop
ENV MONGO="true" \
    MONGO_URL="mongodb://mongodb:27017/user" \
    REDIS_URL="redis://redis:6379"
WORKDIR /opt/server
USER roboshop
COPY --from=builder /opt/server /opt/server/
CMD ["node", "server.js"]


# FROM node:20
# WORKDIR /opt/server
# COPY package.json .
# COPY *.js .
# RUN npm install
# ENV MONGO="true" \
#     MONGO_URL="mongodb://mongodb:27017/user" \
#     REDIS_URL="redis://redis:6379"
# CMD ["node", "server.js"]