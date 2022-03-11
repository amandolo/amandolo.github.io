FROM node:lts-bullseye-slim as base
RUN apt update -y && \
    apt install hugo -y && \
    npm i -g postcss postcss-cli autoprefixer

FROM base as build-base
WORKDIR /site
COPY . .

FROM build-base as generate-base
RUN hugo

FROM scratch as generate
COPY --from=generate-base /site/public/ ./

FROM build-base as server
CMD hugo serve --bind 0.0.0.0
