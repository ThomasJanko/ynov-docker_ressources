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
Nous allons composer ce fichier yaml à l'aide de la commande :
```bash
docker compose -f docker-compose.build.yml build
```
Et voici le résultat de la commande :
```bash
[+] Building 0.0s (0/0)                                                                                                                      docker:default
[+] Building 110.5s (19/45)                                                                                                                  docker:default
[+] Building 110.6s (19/45)                                                                                                                  docker:default
[+] Building 316.2s (49/49) FINISHED                                                                                                         docker:default
 => [result internal] load build definition from Dockerfile                                                                                            0.8s
 => => transferring dockerfile: 525B                                                                                                                   0.2s
 => [result internal] load .dockerignore                                                                                                               1.0s
 => => transferring context: 54B                                                                                                                       0.1s
 => [vote internal] load build definition from Dockerfile                                                                                              1.0s
 => => transferring dockerfile: 1.09kB                                                                                                                 0.0s
 => [vote internal] load .dockerignore                                                                                                                 1.2s
 => => transferring context: 2B                                                                                                                        0.0s
 => [worker internal] load build definition from Dockerfile                                                                                            1.2s
 => => transferring dockerfile: 533B                                                                                                                   0.0s
 => [worker internal] load .dockerignore                                                                                                               1.3s
 => => transferring context: 2B                                                                                                                        0.0s
 => [seed-data internal] load build definition from Dockerfile                                                                                         1.2s
 => => transferring dockerfile: 347B                                                                                                                   0.0s
 => [seed-data internal] load .dockerignore                                                                                                            1.3s
 => => transferring context: 2B                                                                                                                        0.0s
 => [result internal] load metadata for docker.io/library/node:18-slim                                                                                 3.5s
 => [vote internal] load metadata for docker.io/library/python:3.11-slim                                                                               3.1s
 => [worker internal] load metadata for mcr.microsoft.com/dotnet/runtime:7.0                                                                           1.3s
 => [worker internal] load metadata for mcr.microsoft.com/dotnet/sdk:7.0                                                                               1.4s
 => [seed-data internal] load metadata for docker.io/library/python:3.9-slim                                                                           2.6s
 => [worker build 1/7] FROM mcr.microsoft.com/dotnet/sdk:7.0@sha256:7776f4a8f9f4a809374c44f1214d49b22975cdf47a9ef44acf87fec8b0216e95                 281.6s
 => => resolve mcr.microsoft.com/dotnet/sdk:7.0@sha256:7776f4a8f9f4a809374c44f1214d49b22975cdf47a9ef44acf87fec8b0216e95                                0.8s
 => => sha256:7776f4a8f9f4a809374c44f1214d49b22975cdf47a9ef44acf87fec8b0216e95 1.79kB / 1.79kB                                                         0.0s
 => => sha256:a972771bac63e3b2979a838bd0ae04b368a0350e6f3e1cc42a39ec196b8fb7c8 2.01kB / 2.01kB                                                         0.0s
 => => sha256:889872ffeee7a1aed0eb3523b44542672b7211edf29240e03d7425296a63200c 5.28kB / 5.28kB                                                         0.0s
 => => sha256:0bc8ff246cb8ff91066742f8f7ded40397e7aaaa925200b7bec5382d1ffcd6a0 31.42MB / 31.42MB                                                      26.5s
 => => sha256:711eaa7c8f3b33bee5f2f315cbe0147a4e65c0e3f67e6f924af1250e4dd1233b 32.46MB / 32.46MB                                                      54.5s
 => => sha256:5c7a0ff61f6b8430f0383462fbd6e2b1a45b1cd917c03120e09e5cd720659c3e 14.97MB / 14.97MB                                                      18.7s
 => => sha256:3a15a3647c58c15fc183536f7bfab56ea6c76bd3ed6db635a104b92515d8590c 154B / 154B                                                            18.9s
 => => sha256:20fa5f436d27e8ec2798a3781cc08278e1519bb682a60a52259bfe37fa1a8893 10.12MB / 10.12MB                                                      28.4s
 => => sha256:7f70ff820d70543a3a58f64a743dfb15d1e60d84f7a83999817edad533c2c2bc 25.38MB / 25.38MB                                                      42.0s
 => => extracting sha256:0bc8ff246cb8ff91066742f8f7ded40397e7aaaa925200b7bec5382d1ffcd6a0                                                             25.4s
 => => sha256:59fab9224636a0b076b5ad6d93a6d2fbf358d704f3aaa26eb4df61c4422a54ed 180.96MB / 180.96MB                                                   239.8s
 => => sha256:7a14ac1ce672a28ee49d8e19e037207891fc737f615673a263d4e394be339850 13.98MB / 13.98MB                                                      53.0s
 => => extracting sha256:5c7a0ff61f6b8430f0383462fbd6e2b1a45b1cd917c03120e09e5cd720659c3e                                                              6.0s
 => => extracting sha256:711eaa7c8f3b33bee5f2f315cbe0147a4e65c0e3f67e6f924af1250e4dd1233b                                                            252.2s
 => => extracting sha256:3a15a3647c58c15fc183536f7bfab56ea6c76bd3ed6db635a104b92515d8590c                                                              0.0s
 => => extracting sha256:20fa5f436d27e8ec2798a3781cc08278e1519bb682a60a52259bfe37fa1a8893                                                              6.4s
 => => extracting sha256:7f70ff820d70543a3a58f64a743dfb15d1e60d84f7a83999817edad533c2c2bc                                                             21.3s
 => => extracting sha256:59fab9224636a0b076b5ad6d93a6d2fbf358d704f3aaa26eb4df61c4422a54ed                                                             37.6s
 => => extracting sha256:7a14ac1ce672a28ee49d8e19e037207891fc737f615673a263d4e394be339850                                                              1.8s
 => [worker stage-1 1/3] FROM mcr.microsoft.com/dotnet/runtime:7.0@sha256:709d5795be92db33931ef7485aa9b07ad5854734229276cb464a2ee392131c78            78.1s
 => => resolve mcr.microsoft.com/dotnet/runtime:7.0@sha256:709d5795be92db33931ef7485aa9b07ad5854734229276cb464a2ee392131c78                            0.9s
 => => sha256:709d5795be92db33931ef7485aa9b07ad5854734229276cb464a2ee392131c78 1.79kB / 1.79kB                                                         0.0s
 => => sha256:fc024dc1213e67cc9f87965af8249dc75acf9380bde822992e39c0af2da111ab 1.16kB / 1.16kB                                                         0.0s
 => => sha256:e8698d209f83b13c33e2d449904631efd3bfeb73c90c7b66afa9c3aecbf77da3 1.93kB / 1.93kB                                                         0.0s
 => => sha256:0bc8ff246cb8ff91066742f8f7ded40397e7aaaa925200b7bec5382d1ffcd6a0 31.42MB / 31.42MB                                                      26.4s
 => => sha256:5c7a0ff61f6b8430f0383462fbd6e2b1a45b1cd917c03120e09e5cd720659c3e 14.97MB / 14.97MB                                                      18.6s
 => => sha256:711eaa7c8f3b33bee5f2f315cbe0147a4e65c0e3f67e6f924af1250e4dd1233b 32.46MB / 32.46MB                                                      54.4s
 => => sha256:3a15a3647c58c15fc183536f7bfab56ea6c76bd3ed6db635a104b92515d8590c 154B / 154B                                                            18.8s
 => => extracting sha256:0bc8ff246cb8ff91066742f8f7ded40397e7aaaa925200b7bec5382d1ffcd6a0                                                            285.0s
 => => extracting sha256:5c7a0ff61f6b8430f0383462fbd6e2b1a45b1cd917c03120e09e5cd720659c3e                                                            258.6s
 => => extracting sha256:711eaa7c8f3b33bee5f2f315cbe0147a4e65c0e3f67e6f924af1250e4dd1233b                                                             13.8s
 => [worker internal] load build context                                                                                                               0.4s
 => => transferring context: 6.56kB                                                                                                                    0.0s
 => [vote base 1/5] FROM docker.io/library/python:3.11-slim@sha256:f89d4d260b6a5caa6aa8e0e14b162deb76862890c91779c31f762b22e72a6cef                  123.9s
 => => resolve docker.io/library/python:3.11-slim@sha256:f89d4d260b6a5caa6aa8e0e14b162deb76862890c91779c31f762b22e72a6cef                              0.9s
 => => sha256:52cf1e24d0baa095fd8137e69a13042442d40590f03930388df49fe4ecb8ebdb 1.37kB / 1.37kB                                                         0.0s
 => => sha256:f89d4d260b6a5caa6aa8e0e14b162deb76862890c91779c31f762b22e72a6cef 1.65kB / 1.65kB                                                         0.0s
 => => sha256:4a8189355e725d8d250876af1f90af19e36f869fe5d1553a8969d35f18274465 6.93kB / 6.93kB                                                         0.0s
 => => sha256:578acb154839e9d0034432e8f53756d6f53ba62cf8c7ea5218a2476bf5b58fc9 29.15MB / 29.15MB                                                      66.3s
 => => sha256:ac65017cfc5699a3ab0e5ed6e11c321fc0c664fd6b4c8744cda7914e74897c47 3.51MB / 3.51MB                                                        55.9s
 => => sha256:201dfde4aadff9e0b4279613ea9091c25c7bd5f75419be222cff87de7a83dddb 12.84MB / 12.84MB                                                      63.4s
 => => sha256:e2162e32ea00fa4f706ac3276b3073819b55df822b0d0faeb12d712c6773b9b8 245B / 245B                                                            64.5s
 => => sha256:3cef43552ffac628f757a39a16b1af774bffdb891088899c049127eb2f5b9ecc 3.39MB / 3.39MB                                                        66.4s
 => => extracting sha256:578acb154839e9d0034432e8f53756d6f53ba62cf8c7ea5218a2476bf5b58fc9                                                             25.9s
 => => extracting sha256:ac65017cfc5699a3ab0e5ed6e11c321fc0c664fd6b4c8744cda7914e74897c47                                                              2.9s
 => => extracting sha256:201dfde4aadff9e0b4279613ea9091c25c7bd5f75419be222cff87de7a83dddb                                                             16.1s
 => => extracting sha256:e2162e32ea00fa4f706ac3276b3073819b55df822b0d0faeb12d712c6773b9b8                                                              0.0s
 => => extracting sha256:3cef43552ffac628f757a39a16b1af774bffdb891088899c049127eb2f5b9ecc                                                              6.1s
 => [vote internal] load build context                                                                                                                 0.7s
 => => transferring context: 6.46kB                                                                                                                    0.1s
 => [seed-data 1/5] FROM docker.io/library/python:3.9-slim@sha256:2b76740d0b7b94c299868555a14bf4e8a50e0cf74cd7b8c6136d4f4a10fb12bf                   122.0s
 => => resolve docker.io/library/python:3.9-slim@sha256:2b76740d0b7b94c299868555a14bf4e8a50e0cf74cd7b8c6136d4f4a10fb12bf                               1.0s
 => => sha256:2b76740d0b7b94c299868555a14bf4e8a50e0cf74cd7b8c6136d4f4a10fb12bf 1.86kB / 1.86kB                                                         0.0s
 => => sha256:590aa200bf472f2b15eb5b72bbe20410ddeee30c79c2c306c1c83ee315cd1efb 1.37kB / 1.37kB                                                         0.0s
 => => sha256:e388a3937df2eecf1838b6055a1365da2e6370d4cd33b3ab69725bb75ca2c6da 6.92kB / 6.92kB                                                         0.0s
 => => sha256:578acb154839e9d0034432e8f53756d6f53ba62cf8c7ea5218a2476bf5b58fc9 29.15MB / 29.15MB                                                      66.2s
 => => sha256:ac65017cfc5699a3ab0e5ed6e11c321fc0c664fd6b4c8744cda7914e74897c47 3.51MB / 3.51MB                                                        55.8s
 => => sha256:54b9f39df8ebf1d4894786c64114220c3b92ef7e17c8e249d56d9a6dd0b2a221 244B / 244B                                                            66.8s
 => => sha256:fee64e946eb667cbc95de09a39a18e13287a6946b2bcb605f7b19b11b87addfa 11.89MB / 11.89MB                                                      74.3s
 => => extracting sha256:578acb154839e9d0034432e8f53756d6f53ba62cf8c7ea5218a2476bf5b58fc9                                                             25.9s
 => => sha256:579b778deb443132bd8f35d4617de8d1dc45c00e537f0c4469081af7fe186cf3 3.13MB / 3.13MB                                                        69.3s
 => => extracting sha256:ac65017cfc5699a3ab0e5ed6e11c321fc0c664fd6b4c8744cda7914e74897c47                                                              2.9s
 => => extracting sha256:fee64e946eb667cbc95de09a39a18e13287a6946b2bcb605f7b19b11b87addfa                                                             11.5s
 => => extracting sha256:54b9f39df8ebf1d4894786c64114220c3b92ef7e17c8e249d56d9a6dd0b2a221                                                              0.0s
 => => extracting sha256:579b778deb443132bd8f35d4617de8d1dc45c00e537f0c4469081af7fe186cf3                                                              7.1s
 => [seed-data internal] load build context                                                                                                            0.4s
 => => transferring context: 1.09kB                                                                                                                    0.1s
 => [result 1/7] FROM docker.io/library/node:18-slim@sha256:d2d8a6420c9fc6b7b403732d3a3c5395d016ebc4996f057aad1aded74202a476                         177.2s
 => => resolve docker.io/library/node:18-slim@sha256:d2d8a6420c9fc6b7b403732d3a3c5395d016ebc4996f057aad1aded74202a476                                  0.9s
 => => sha256:d2d8a6420c9fc6b7b403732d3a3c5395d016ebc4996f057aad1aded74202a476 1.21kB / 1.21kB                                                         0.0s
 => => sha256:ef52e84aa85baadfcdfe6f40162c368c08d4def29751ed1429abe1908316b198 1.37kB / 1.37kB                                                         0.0s
 => => sha256:3c4184b9cda1859a9b16e8818925c1b644cd8485f8e1a084d3b64f07d6f215df 7.31kB / 7.31kB                                                         0.0s
 => => sha256:578acb154839e9d0034432e8f53756d6f53ba62cf8c7ea5218a2476bf5b58fc9 29.15MB / 29.15MB                                                      66.1s
 => => extracting sha256:578acb154839e9d0034432e8f53756d6f53ba62cf8c7ea5218a2476bf5b58fc9                                                             25.9s
 => => sha256:f3a2b77f992882abd7dda47f1dbd6b239e90f00fdc930b4442ebc5fcf6ba5aa1 3.35kB / 3.35kB                                                        70.1s
 => => sha256:ec092ab086f2a82aaa9384abddccc15009eb4559edbe1f2a0aacd43ed2344fec 46.36MB / 46.36MB                                                     101.3s
 => => sha256:82924524a3e0665ba81690cd19e5a6e7448900caf5bd60eb1f411abfdaad8023 2.67MB / 2.67MB                                                        76.1s
 => => sha256:0fc3c53bc7992fd2a6f822f0b0c69841607df94c5d19961c2b086135caef3444 453B / 453B                                                            76.5s
 => => extracting sha256:f3a2b77f992882abd7dda47f1dbd6b239e90f00fdc930b4442ebc5fcf6ba5aa1                                                              0.0s
 => => extracting sha256:ec092ab086f2a82aaa9384abddccc15009eb4559edbe1f2a0aacd43ed2344fec                                                             66.7s
 => => extracting sha256:82924524a3e0665ba81690cd19e5a6e7448900caf5bd60eb1f411abfdaad8023                                                              2.1s
 => => extracting sha256:0fc3c53bc7992fd2a6f822f0b0c69841607df94c5d19961c2b086135caef3444                                                              0.0s
 => [result internal] load build context                                                                                                               0.8s
 => => transferring context: 278.07kB                                                                                                                  0.1s
 => [worker stage-1 2/3] WORKDIR /app                                                                                                                  2.5s
 => [seed-data 2/5] RUN apt-get update     && apt-get install -y --no-install-recommends     apache2-utils     && rm -rf /var/lib/apt/lists/*         53.7s
 => [vote base 2/5] RUN apt-get update &&     apt-get install -y --no-install-recommends curl &&     rm -rf /var/lib/apt/lists/*                      56.1s
 => [seed-data 3/5] WORKDIR /seed                                                                                                                      1.2s
 => [seed-data 4/5] COPY . .                                                                                                                           0.9s
 => [result 2/7] RUN apt-get update &&     apt-get install -y --no-install-recommends curl tini &&     rm -rf /var/lib/apt/lists/*                    51.4s
 => [seed-data 5/5] RUN python make-data.py                                                                                                            4.7s
 => [vote base 3/5] WORKDIR /usr/local/app                                                                                                             0.7s
 => [vote base 4/5] COPY requirements.txt ./requirements.txt                                                                                           0.6s
 => [vote base 5/5] RUN pip install --no-cache-dir -r requirements.txt                                                                                21.3s
 => [seed-data] exporting to image                                                                                                                     1.8s
 => => exporting layers                                                                                                                                1.7s
 => => writing image sha256:cd4471177ddd7734a1a4a9493ef3e2a49e7f63dc84df9df692b69ac7efc4f344                                                           0.0s
 => => naming to docker.io/library/who-rule-the-world-seed-data                                                                                        0.0s
 => [vote final 1/1] COPY . .                                                                                                                          0.8s
 => [vote] exporting to image                                                                                                                          2.4s
 => => exporting layers                                                                                                                                2.4s
 => => writing image sha256:df1ba20116471e2520c00a0329fa96ab95ee87a532d2628841238693ddbbeeee                                                           0.0s
 => => naming to docker.io/library/who-rule-the-world-vote                                                                                             0.0s
 => [result 3/7] WORKDIR /usr/local/app                                                                                                                0.6s
 => [result 4/7] RUN npm install -g nodemon                                                                                                           10.4s
 => [result 5/7] COPY package*.json ./                                                                                                                 0.8s
 => [result 6/7] RUN npm ci &&  npm cache clean --force &&  mv /usr/local/app/node_modules /node_modules                                              25.9s
 => [result 7/7] COPY . .                                                                                                                              0.9s
 => [result] exporting to image                                                                                                                        3.7s
 => => exporting layers                                                                                                                                3.6s
 => => writing image sha256:79c52bf65a71848324c5a8ad5b34703799ebd7fe94dff6e44f163ffe9790f3f5                                                           0.0s
 => => naming to docker.io/library/who-rule-the-world-result                                                                                           0.0s
 => [worker build 2/7] RUN echo "I am running on linux/amd64, building for linux/amd64"                                                                1.9s
 => [worker build 3/7] WORKDIR /source                                                                                                                 0.4s
 => [worker build 4/7] COPY *.csproj .                                                                                                                 0.2s
 => [worker build 5/7] RUN dotnet restore -a amd64                                                                                                    18.3s
 => [worker build 6/7] COPY . .                                                                                                                        0.5s
 => [worker build 7/7] RUN dotnet publish -c release -o /app -a amd64 --self-contained false --no-restore                                              8.7s
 => [worker stage-1 3/3] COPY --from=build /app .                                                                                                      0.1s
 => [worker] exporting to image                                                                                                                        0.2s
 => => exporting layers                                                                                                                                0.2s
 => => writing image sha256:3d5b93132cff171467b19dd04ece29c239ed2e68e1761b3e1fa6b09192e1122b                                                           0.0s
 => => naming to docker.io/library/who-rule-the-world-worker
```
Nous allons ensuite tagger les images dans le registre:
```bash
docker tag who-rule-the-world-worker:latest localhost:5000/worker
docker push localhost:5000/worker
```
```bash
docker tag who-rule-the-world-vote:latest localhost:5000/vote
docker push localhost:5000/vote
```
```bash
docker tag who-rule-the-world-seed-data:latest localhost:5000/seed-data
docker push localhost:5000/seed-data
```
```bash
docker tag who-rule-the-world-result:latest localhost:5000/result
docker push localhost:5000/result
```
