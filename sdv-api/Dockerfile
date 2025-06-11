# Image de base
FROM rust:1.82.0-alpine AS base 
ARG pkg=sdv-api
WORKDIR /app
RUN apk add --no-cache musl-dev  


# Image de dev
FROM base AS dev
RUN cargo install cargo-watch


# Image de build pour la prod
FROM base AS builder
COPY . .
RUN --mount=type=cache,target=/app/target \
    --mount=type=cache,target=/usr/local/cargo/registry \
    --mount=type=cache,target=/usr/local/cargo/git \
    set -eux; \
    cargo build --release; \
    objcopy --compress-debug-sections target/release/$pkg ./sdv-api


# Image de prod
FROM alpine:latest AS prod
ENV ROCKET_ADDRESS=0.0.0.0
ENV ROCKET_PORT=80
COPY --from=builder /app/sdv-api /usr/bin/sdv-api
CMD ["sdv-api"]


# Inspiré par la doc de Rocket :
# https://rocket.rs/guide/v0.5/deploying/#containerization
