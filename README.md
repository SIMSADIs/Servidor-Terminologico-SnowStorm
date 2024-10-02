# Servidor terminológico SnowStorm
A continuación se muestra paso a paso cómo instalar el servidor terminológico open-source Snowstorm de Snomed-CT en un sistema operativo Linux.

# Despliegue local de servidor 
Para desplegar el servidor terminológico SnowStorm se utiliza la documentación entregada por Snomed-CT en https://github.com/IHTSDO/snowstorm?tab=readme-ov-file.

## Requisitos

- Sistema operativo Linux
- 8G de memoria RAM
- Disco SSD


### Instalación de Docker

Para instalar Docker en Linux se utilizan los siguientes comandos en orden, estos deben ser ingresados en la terminal.

1.- Actualizar lista de paquetes disponibles en el sistema.
```
sudo apt update && sudo apt upgrade -y
```

2.- Utilizar gestor de paquetes apt e instalar certificados y herramienta de transferencia de datos "curl".
```
sudo apt-get install ca-certificates curl
```

3.- Crer un directorio seguro para llaves de repositorios APT.
```
sudo install -m 0755 -d /etc/apt/keyrings
```

4.- Descargar y guardar clave GPG de Docker en el sistema.
```
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
```

5.- Otorgar permisos de lectura a todos los usuarios para la clave GPG de Docker.
```
sudo chmod a+r /etc/apt/keyrings/docker.asc
```

6.- Agregar el repositorio de Docker a las fuentes de Apt y actualizar la lista de paquetes.
```
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```

7.- Instalar Docker Engine, CLI, Containerd, Buildx y Compose plugins.
```
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

## Instalación de SnowStorm
Para instalar SnowStorm se deben ejecutar los siguientes comandos.
```
sudo su
```

```
cd ..
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
curl -SL https://github.com/docker/compose/releases/download/v2.28.0/docker-compose-linux-x86_64 -o /usr/local/bin/docker-compose
```
```
sudo chmod +x /usr/local/bin/docker-compose
```
```
docker-compose --version
```
```
wget
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
docker compose-up -d
```
## Carga de Snomed Internacional

falta agregar :D


## Carga de terminologías

## Requisitos

- Java instalado.
- HAPI-FHIR Tool instalado.
  

### Instalar Java
1.- Se instala Java
```
sudo apt install openjdk-17-jre-headless  # version 17.0.12+7-1ubuntu2~24.04
```

### Instalar HAPI-FHIR Tool

Para instalar Hapi-Fhir Tool se utiliza la documentación entregada en https://hapifhir.io/hapi-fhir/docs/tools/hapi_fhir_cli.html.

1.- Descargar el archivo comprimido llamado hapi-fhir-[versión]-cli.zip desde https://github.com/hapifhir/hapi-fhir/releases .

2.- Descomprime el archivo descargado, utiliza la terminal, ubicate en el directorio donde se encuntra el archivo e ingresa el siguiente comando, recuerda cambiar la versión a la que estés ocupando.
```
unzip hapi-fhir-7.4.2-cli.zip
```

3.- Ejecuta el archivo hapi-fhir-cli.jar.
```
java hapi-fhir-cli.jar
```

4.- Inicia HAPI-FHIR Tool.
```
 ./hapi-fhir-cli
```

### Carga de terminología

#### Loinc
```
 ./hapi-fhir-cli upload-terminology -d Loinc_2.74.zip -v r4 -t http://localhost:8080/fhir -u http://loinc.org -s 10GB
```

#### Cie-10
```
 ./hapi-fhir-cli upload-terminology -d cie_10_deis.zip -v r4 -t http://localhost:8080/fhir -u http://hl7.org/fhir/sid/icd-10 -s 1GB
```

#### Norma 820




