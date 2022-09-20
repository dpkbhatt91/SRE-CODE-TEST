FROM node

RUN mkdir -p /var/node
ADD . /var/node/
WORKDIR /var/node
RUN npm install
ENV NEW_RELIC_NO_CONFIG_FILE=true
ENV NEW_RELIC_DISTRIBUTED_TRACING_ENABLED=true
ENV NEW_RELIC_LOG=stdout
EXPOSE 3000
CMD ./bin/www
