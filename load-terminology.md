# Cargando terminología

En este proyecto se subió la Norma Técnica 2.3.1 de Chile, el estandar terminológico Loinc y Cie-10. Esto se hizo de forma local en el servido, cargando un archivo .zip con la terminología y se da una dirección para hacer llamado a la terminología. 

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
