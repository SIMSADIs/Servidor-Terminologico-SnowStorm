# SnowStorm en Bahmni

SnowStorm es un servidor terminológico OpenSource capáz de validar y codificar terminos y conceptos clínicos en diversas aplicaciones de salud, una de ellas altamente utilizada en los diversos sístemas de salud son los registros clínicos eléctrónicos (EMR) en donde se registra diversidad de información de los pacientes. En este proyecto para demostrar la usabilidad de SnowStorm se integró con el HIS Bahmni, esta integración permite registrar la información de los pacientes de forma codificada y estandarizada asegurando así la calidad de la mismo.

Para crear la integración de SnowStorm con Bahmni se debe seguir lo comentado a continuación

### Instalación de Bahmni

Para instalar Bahmnni se siguió la documentación realizada por Nicolás Muñoz en su trabajó de título en el repositorio [Bahmni SIMSADI](https://github.com/Mitridato/BAHMNI-SIMSADI/tree/main?tab=readme-ov-file). En esta documentación se explica cómo instalar Bahmni y configurarlo para darle funcionalidades. 

Adicional a la documentación mencionada también se revisó la documentación original en [Bahmni Wiki](https://bahmni.atlassian.net/wiki/spaces/BAH/overview?homepageId=491527).

En este proyecto se decidió utilizar Bahmni lite ya que para fines de testeo Universitario es suficiente, si se quisiera ahondar un poco más ya a casos de hospitales de alta complejidad se recomienda el uso de Bahmni Estándar.


A continuación se muestran los comandos con los cuales se instala Bahmni, estos los podemos encontrar en el [link](https://bahmni.atlassian.net/wiki/spaces/BAH/pages/3117744129/Getting+Started+Quickly+with+Bahmni+on+Docker#Running-Bahmni-Standard).

Ubicate en un directorio a elección en la terminal en modo root y ejecuta los siguientes comandos.
```

# Clona el repositorio de Bahmni docker
git clone https://github.com/Bahmni/bahmni-docker.git

cd bahmni-lite

# Edita el archivo .env y sigue los siguientes pasos:
# 1. Cambia `COMPOSE_PROFILES=bahmni-lite` (o usa el valor por defecto que es `emr`)
# 2. Cambia `TZ` a tu zona horaria deseada (o usa el valor por defecto que es `UTC`).
# 3. Para un servidor remoto (si no se está ejecutando en localhost) para crater:
# escribe la dirección IP o el nombre de dominio en las siguientes propiedades (en lugar de localhost):
# CRATER_APP_URL, CRATER_SANCTUM_STATEFUL_DOMAINS y CRATER_SESSION_DOMAIN

# Instala Bahmni

docker compose pull

docker compose build 

docker compose up -d

./run-bahmni.sh .env.dev

```

### Instegración de Bahmni con SnowStorm

Para integrar SnowStorm con Bahmni se ajustan los parámetros como indica este [link](https://bahmni.atlassian.net/wiki/spaces/BAH/pages/3183345706/Bahmni-SNOMED+TS+Integration+Local+Installation+Guide+using+docker)

En archivo .env se deben ajustar los siguientes parámetros considerando cambiar a tu IP:
```
COMPOSE_PROFILES = bahmni-lite, cdss
TERMINOLOGY_SERVER_URL = http://IP:8080/fhir
ICD10_LITE_INDICATOR = false
```

En archivo .envdev se deben ajustar los siguientes parámetros considerando cambiar a tu IP:

```
TERMINOLOGY_SERVER_URL = http://IP:8080/fhir
ICD10_LITE_INDICATOR = false
```

Desde OpenMRS en el URL https://localhost/openmrs/ con el mismo usuario y contraseña especificado anteriormente se realizaron los siguientes ajustes. 

En Administration -> Maintance -> Settings -> Cdss, se ajusta: 

```
cdss.enable =  true
cdss.fhir.baseurl = http://cdss:8080/cds-services 
```

En Administration -> Maintance -> Settings -> Ts, se ajusta:

```
fhir.baseurl = http://IP:8080/fhir   //considera cambiar al IP del servidor a utilizar
Los demás campos se dejan en predeterminado
```

En Administration -> Maintance -> Settings -> Bahmni, se ajusta:

```
bahmni.lookupExternalTerminologyServer = true
```
En Administration -> Maintance -> Settings -> Fhir, se ajusta:

 ```
fhir.export.anonymise.config.path = /openmrs/data/fhir-export-anonymise-config.json
```

