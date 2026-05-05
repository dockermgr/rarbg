## 👋 Welcome to rarbg 🚀  

A self-hosted Torznab API for the RARBG backup, compatible with Prowlarr, Radarr, Sonarr etc. 
  
FROM: <https://github.com/mgdigital/rarbg-selfhosted>
  

## Install my system scripts  

```shell
 sudo bash -c "$(curl -q -LSsf "https://github.com/systemmgr/installer/raw/main/install.sh")"
 sudo systemmgr --config && sudo systemmgr install scripts  
```
  
## Automatic install/update  
  
```shell
dockermgr update rarbg
```
  
## Install and run container
  
```shell
mkdir -p "$HOME/.local/share/srv/docker/rarbg/volumes"
git clone "https://github.com/dockermgr/rarbg" "$HOME/.local/share/CasjaysDev/dockermgr/rarbg"
cp -Rfva "$HOME/.local/share/CasjaysDev/dockermgr/rarbg/volumes/." "$HOME/.local/share/srv/docker/rarbg/volumes/"
docker run -d \
--restart always \
--privileged \
--name casjaysdevdocker-rarbg \
--hostname rarbg \
-e TZ=${TIMEZONE:-America/New_York} \
-v $HOME/.local/share/srv/docker/casjaysdevdocker-rarbg/volumes/data:/data:z \
-v $HOME/.local/share/srv/docker/casjaysdevdocker-rarbg/volumes/config:/config:z \
-p 0.0.0.0:3333:3333 \
casjaysdevdocker/rarbg:latest
```
  
## via docker-compose  
  
```yaml
version: "2"
services:
  ProjectName:
    image: casjaysdevdocker/rarbg
    container_name: casjaysdevdocker-rarbg
    environment:
      - TZ=America/New_York
      - HOSTNAME=rarbg
    volumes:
      - $HOME/.local/share/srv/docker/casjaysdevdocker-rarbg/volumes/data:/data:z
      - $HOME/.local/share/srv/docker/casjaysdevdocker-rarbg/volumes/config:/config:z
    ports:
      - 0.0.0.0:3333:3333
    restart: always
```
  
## Get source files  
  
```shell
dockermgr download src casjaysdevdocker/rarbg
```
  
OR
  
```shell
git clone "https://github.com/casjaysdevdocker/rarbg" "$HOME/Projects/github/casjaysdevdocker/rarbg"
```
  
## Build container  
  
```shell
cd "$HOME/Projects/github/casjaysdevdocker/rarbg"
buildx 
```
  
## Authors  
  
🤖 casjay: [Github](https://github.com/casjay) 🤖  
⛵ casjaysdevdocker: [Github](https://github.com/casjaysdevdocker) [Docker](https://hub.docker.com/u/casjaysdevdocker) ⛵  
