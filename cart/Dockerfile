FROM node:14 AS build

WORKDIR /opt/server

COPY package.json /opt/server/

RUN npm install --only=production

COPY server.js /opt/server/

FROM node:14-slim AS runtime

ENV INSTANA_AUTO_PROFILE true

EXPOSE 8080

WORKDIR /opt/server

RUN npm install

COPY --from=build /opt/server /opt/server

CMD ["node", "server.js"]

