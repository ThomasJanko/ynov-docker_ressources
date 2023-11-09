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
<pre style="background-color: #f4f4f4; padding: 10px; font-family: 'Courier New', monospace; font-size: 14px;">
# Contenu du docker-compose.build.yml
version: '3'
services:
  worker:
    build:
      context: ./2023/m2/docker/who-rule-the-world/worker
    image: http://localhost:5000/worker
    networks:
      - registry-network
  vote:
    build:
      context: ./2023/m2/docker/who-rule-the-world/vote
    image: http://localhost:5000/vote
    networks:
      - registry-network
  seed-data:
    build:
      context: ./2023/m2/docker/who-rule-the-world/seed-data
    image: http://localhost:5000/seed-data
    networks:
      - registry-network
  result:
    build:
      context: ./2023/m2/docker/who-rule-the-world/result
    image: http://localhost:5000/result
    networks:
      - registry-network

networks:
  registry-network:
    external: true
</pre>

