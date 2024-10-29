# Sup de Vinci - Containers module project

*Tested with `rust v1.82.0` et `node 23.0.0`.*

## Development

### Without  Docker

#### API

Use `cargo run` to start the dev environment.

You can also install [cargo-watch](https://crates.io/crates/cargo-watch) to watche over your project's source for changes, and runs Cargo commands when they occur : `cargo-watch -x run`.

#### Web

Use `npm install` to install all dependancies, and `npm run dev` to start the dev environment.

### Using Docker

Run `docker compose up --build` to start the dev stack.


## Production

### Without Docker

#### API

Run `cargo build --release` to build and compile the app. This will create an executable in `/target/release/sdv-api`.

#### Web

Run `npm run build` to build the application, and run `npm run start` to start the Node.js server. 

### Using Docker

The production images are automatically built and uploaded on Docker Hub.
