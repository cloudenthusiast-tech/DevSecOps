FROM node:20.19.6-alpine3.23 AS build
WORKDIR /opt/server
COPY *.json .
RUN npm install
COPY . .

FROM node:20.19.6-alpine3.23
WORKDIR /opt/server
RUN addgroup -S agent && adduser -S agent -G agent && \
    chown -R agent:agent /opt/server
COPY --from=build /opt/server /opt/server
USER agent
CMD ["index.js"]
ENTRYPOINT ["node"]
