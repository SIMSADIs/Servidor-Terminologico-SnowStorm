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
Para cargar SNOMED-CT en inglés y en distintos idiomas se debe hacer desde la url https://[IP]:8080/ la cual lleva a Swagger UI, a continuación se muestra  el paso a paso.

1.- Desde Swagger UI se debe ir a la sección Imports, POST/imports y en body request se debe pegar la definición entregada en este [link](https://github.com/IHTSDO/snowstorm/blob/master/docs/loading-snomed.md) 

<img src="https://github.com/SIMSADIs/Servidor-Terminologico-SnowStorm/blob/deploy-snowstorm/1.gif" alt="Obtener ID" width="500" height="300">

<img src="https://github.com/SIMSADIs/Servidor-Terminologico-SnowStorm/blob/deploy-snowstorm/2.gif" alt="Pegar ID" width="500" height="300">

<img src="https://github.com/SIMSADIs/Servidor-Terminologico-SnowStorm/blob/deploy-snowstorm/3.gif" alt="Subir archivo" width="500" height="300">

<img src="https://github.com/SIMSADIs/Servidor-Terminologico-SnowStorm/blob/deploy-snowstorm/4.gif" alt="Revisando logs" width="500" height="300">


## En caso de error quita los contenedores y vuelve a subir

quita docker
```
sudo apt-get purge -y docker-ce docker-ce-cli containerd.io
sudo apt-get autoremove -y --purge
sudo dnf remove -y docker-ce docker-ce-cli containerd.io
sudo dnf autoremove -y

sudo rm -rf /var/lib/docker
sudo rm -rf /var/lib/containerd
sudo rm -rf /etc/docker

sudo rm -rf /var/run/docker.sock
sudo rm -rf ~/.docker

sudo groupdel docker

sudo rm -rf /usr/local/bin/docker*

```
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




