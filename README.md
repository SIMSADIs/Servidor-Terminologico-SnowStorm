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

## Carga de Snomed Internacional

falta agregar :D


## Carga de terminologías


