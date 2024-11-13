# Cargando terminología

Snowstor es un servidor terminologico compatible con una serie de tesauros médicos que escenciales en la médicina global como SNOMED- CT, Loinc, Cie-10, value sets, codesystems y muchos más.

Se pueden subir terminología las distintas terminologías a SnowStorm como se muestra a continuación.

Cabe destacar que en este proyecto se subió la Norma Técnica 2.3.1 de Chile, el estandar terminológico Loinc y Cie-10 además de algunos Value-Set de la guía coreCL. Esto se hizo de forma local en el servido

### Carga de terminologías

Para cargar las terminologías se hace a través de la API FHIR de SnowStorm, debes ubicarte en un directorio donde tengas tus archivos .zip con la terminología en el terminal, se ingresan los comandos que se indican a continuación, los cuales indican que se está utilizanddo la herramienta hapi-fhir-cli, se escribe el nombre del archivo .zip de la terminología y se da una dirección url como para hacer reconocimiento de la terminología. 

#### Loinc
```
 ./hapi-fhir-cli upload-terminology -d Loinc_2.74.zip -v r4 -t http://localhost:8080/fhir -u http://loinc.org -s 10GB
```

#### Cie-10
```
 ./hapi-fhir-cli upload-terminology -d cie_10_deis.zip -v r4 -t http://localhost:8080/fhir -u http://hl7.org/fhir/sid/icd-10 -s 1GB
```

#### Norma 820
```
 ./hapi-fhir-cli upload-terminology -d cie_10_deis.zip -v r4 -t http://192.168.10.187:8080/fhir -u http://hl7.org/fhir/sid/icd-10
```

### Carga de Value Sets

Para cargar un Value Set en SnowStorm se debe realizar en un consultador de API REST como Postman ya que puede almacenar y administrar especificaciones de API, se debe hacer un Post a la API del servidor 

Dirección del servidor

```
http://localhost:8080/ 
```

Ejemplo de Value-Set
```
{
    "resourceType": "ValueSet",
    "url": "http://minsal.cl/fhir/vs/sexo_biologico",
    "version": "0.1",
    "name": "Sexo Biologico",
    "description": "Lista de los posibles sexos para captura de detalle de pacicentes.",
    "status": "draft",
    "experimental": true,
    "language": "es",
    "compose": {
        "include": [
            {
                "system": "http://snomed.info/sct/449081005",
                "concept": [
                    {
                        "code": "248153007"
                    },
                    {
                        "code": "248152002"
                    },
                    {
                        "code": "32570691000036108"
                    },
                    {
                        "code": "407377005"
                    },
                    {
                        "code": "407376001"
                    }
                ]
            }
        ]
    }
}
```




