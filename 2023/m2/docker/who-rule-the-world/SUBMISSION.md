# **RENDU DU JEUDI 09 NOVEMBRE 2023**
## MEMBRES DU PROJET :
##### Thomas Jankowski
##### Koceila ARHAB
##### Léo MAGNANT

```bash
# Pour le répertoire "worker"
cd worker
touch Dockerfile
nano Dockerfile
# Copier-coller du Dockerfile du repo

# Pour le répertoire "vote"
cd vote
touch Dockerfile
nano Dockerfile
# Copier-coller du Dockerfile du repo

# Pour le répertoire "seed-data"
cd seed-data
touch Dockerfile
nano Dockerfile
# Copier-coller du Dockerfile du repo

# Pour le répertoire "result"
cd result
touch Dockerfile
nano Dockerfile
# Copier-coller du Dockerfile du repo
```
Nous allons build les images à partir du fichier:
docker-compose.build.yml
```yaml
# Contenu du docker-compose.build.yml
version: '3'
services:
  worker:
    build:
      context: ./worker
    networks:
      - registry-network
  vote:
    build:
      context: ./vote
    networks:
      - registry-network
  seed-data:
    build:
      context: ./seed-data
    networks:
      - registry-network
  result:
    build:
      context: ./result
    networks:
      - registry-network

networks:
  registry-network:
    external: true
```


