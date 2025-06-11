# Explications

## Préambule
Pour pouvoir démarrer l'application, j'ai du supprimer tous les paquets de next du fichier /.sdv-web/package-lock.json
J'ai également cré un network dans le docker compose pour pouvoir faire communiquer les deux conteneurs. J'ai finalement changé l'addresse de l' api de http://api:80 à http://api:8000


## docker-compose
Le fichier de docker compose est un fichier qui permet lancer toute la stack dans des conteneurs dockers
J'ai rédigé plus d'explications directement dans le fichier

## fichiers dockerfile
### FROM
sert de point de départ aux commandes qui vont être jouées. On peut partir d'une image existante ou de rien (FROM scratch)
### ENV
Permet de déclarer des variables d'environnement
 
### WORKDIR 
equivalent d'un cd, permet de se positionner dans un repertoire
### COPY 
copie un fichier/dossier de l'hote vers le conteneur. 

Permet aussi de récupérer des dossiers/fichiers d'un autre conteneur du dockerfile (COPY --from <nom>). Cela permet de générer des images plus légère en compilant l'api rust dans un premier conteneur puis en ne récupérant que l'application compilée dans un autre en laissant derrière tous les outils lourds de compilations

### RUN 
execute une commande
### ENTRYPOINT et CMD
commande a lancer à l'execution du conteneur ["cmd", "arg1", "arg2"]


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
