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
<pre style="background-color: #f4f4f4; padding: 10px; font-family: 'Courier New', monospace; font-size: 14px; color: #333;">
# Contenu du docker-compose.build.yml
<span style="color: #0074D9;">version:</span> <span style="color: #666666;">'3'</span>
<span style="color: #0074D9;">services:</span>
  <span style="color: #0074D9;">worker:</span>
    <span style="color: #666666;">build:</span>
      <span style="color: #666666;">context:</span> <span style="color: #0066cc;">./worker</span>
    <span style="color: #666666;">networks:</span>
      - <span style="color: #0066cc;">registry-network</span>
  <span style="color: #0074D9;">vote:</span>
    <span style="color: #666666;">build:</span>
      <span style="color: #666666;">context:</span> <span style="color: #0066cc;">./vote</span>
    <span style="color: #666666;">networks:</span>
      - <span style="color: #0066cc;">registry-network</span>
  <span style="color: #0074D9;">seed-data:</span>
    <span style="color: #666666;">build:</span>
      <span style="color: #666666;">context:</span> <span style="color: #0066cc;">./seed-data</span>
    <span style="color: #666666;">networks:</span>
      - <span style="color: #0066cc;">registry-network</span>
  <span style="color: #0074D9;">result:</span>
    <span style="color: #666666;">build:</span>
      <span style="color: #666666;">context:</span> <span style="color: #0066cc;">./result</span>
    <span style="color: #666666;">networks:</span>
      - <span style="color: #0066cc;">registry-network</span>

<span style="color: #0074D9;">networks:</span>
  <span style="color: #666666;">registry-network:</span>
    <span style="color: #666666;">external:</span> <span style="color: #666666;">true</span>
</pre>


