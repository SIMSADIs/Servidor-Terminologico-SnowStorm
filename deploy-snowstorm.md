## Despliegue de SnowStorm

Para desplegar SnowStorm se deben ejecutar los siguientes comandos en la terminal del dispositivo después de haber instalado los requerimientos que se muentran en la rama principal  de este repositorio. Adicional a eso debes estar en modo root en la terminal.

1.- Va a la raíz del sistema
```
cd
```

2.- Verifica el estado de servicio docker 
```
systemctl status docker
```

3.- Crea volumen portainer_data, este crea almacenamiento persistente para los datos.
```
docker volume create portainer_data
```

4.- Inicia un contenedor de Docker en segundo plano (-d) para Portainer CE. Publica los puertos 8000 y 9443 en la máquina host, monta el socket de Docker para gestión local, y utiliza el volumen portainer_data para persistencia de datos. Además, asegura que el contenedor se reinicie automáticamente (--restart=always) si se detiene.
```
docker run -d -p 8000:8000 -p 9443:9443 --name portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:latest
```

5.- Ajusta el límite de memoria mapeada necesario para Elasticsearch.

```
sudo sysctl -w vm.max_map_count=262144
```

6.- Descarga Snowstorm versión 10.3.1.
```
wget https://github.com/IHTSDO/snowstorm/archive/refs/tags/10.3.1.zip
```

7.- Extrae los archivos de Snowstorm.
```
unzip 10.3.1.zip
```

8.- Entra al directorio descomprimido.
```
cd snowstorm-10.3.1/
```

9.- Abre el archivo de configuración de Docker Compose.
```
nano docker-compose.yml
```
10.- Levanta los servicios en segundo plano.
```
docker-compose up -d
```
## Carga de Snomed Internacional
Para cargar SNOMED-CT en inglés y en distintos idiomas se debe hacer desde la url https://[IP]:8080/ la cual lleva a Swagger UI, a continuación se muestra  el paso a paso.

1.- Desde Swagger UI se debe ir a la sección Imports, POST/imports y en body request se debe pegar la definición entregada en este [link](https://github.com/IHTSDO/snowstorm/blob/master/docs/loading-snomed.md) , al hacer click en Execute se entregará un ID.

<img src="https://github.com/SIMSADIs/Servidor-Terminologico-SnowStorm/blob/deploy-snowstorm/1.gif" alt="Obtener ID" width="500" height="300">


2.- El ID entregado debe pegarse en la sección GET/import/{importId} y dar click en Execute.

<img src="https://github.com/SIMSADIs/Servidor-Terminologico-SnowStorm/blob/deploy-snowstorm/2.gif" alt="Pegar ID" width="500" height="300">

3.- También se debe pegar el ID en la sección POST/imports/{importId}/archive, y adicionalmente se debe seleccionar el archivo  que contiene SNOMED-CT buscando en tu equipo y hacer click en Execute, luego de unos minutos se subirá el archivo.

<img src="https://github.com/SIMSADIs/Servidor-Terminologico-SnowStorm/blob/deploy-snowstorm/3.gif" alt="Subir archivo" width="500" height="300">

4.- Finalmente se puede ir a ver en el log del contenedor de snowstorm si comienzan a subirse correctamente SNOMED-CT.

<img src="https://github.com/SIMSADIs/Servidor-Terminologico-SnowStorm/blob/deploy-snowstorm/4.gif" alt="Revisando logs" width="500" height="300">





