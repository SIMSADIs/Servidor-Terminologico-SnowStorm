## Despliegue local de SnowStorm

Para desplegar SnowStorm se deben ejecutar los siguientes comandos en la terminal del dispositivo.


```
cd
```

```
systemctl status docker
```
```
docker volume create portainer_data
```
```
docker run -d -p 8000:8000 -p 9443:9443 --name portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:latest
```
```
sudo sysctl -w vm.max_map_count=262144
```

```
wget https://github.com/IHTSDO/snowstorm/archive/refs/tags/10.3.1.zip
```
```
unzip 10.3.1.zip
```

```
cd snowstorm-10.3.1/
```

```
nano docker-compose.yml
```
```
docker-compose up -d
```
## Carga de Snomed Internacional

![Obtener ID](/deploy-snowstorm/1.gif)

## En caso de error como quitar los contenedores

eliminar contenedores
```
docker-compose down --volumes --rmi all
docker volume prune -f
docker network prune -f
```
quita portainer y carpeta
```
docker stop portainer
docker rm portainer
rm -r snowstorm-10.3.1/
```
## Docker Compose
```
curl -SL https://github.com/docker/compose/releases/download/v2.28.0/docker-compose-linux-x86_64 -o /usr/local/bin/docker-compose
```
```
sudo chmod +x /usr/local/bin/docker-compose
```
```
docker-compose --version
```




