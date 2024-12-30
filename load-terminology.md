# Cargando terminología

Snowstor es un servidor terminológico compatible con una serie de tesauros médicos que escenciales en la medicina global como SNOMED- CT, Loinc, Cie-10, value sets, codesystems y muchos más.

Cabe destacar que en este proyecto se subió la Norma Técnica 820 de Chile, el estandar terminológico Loinc y Cie-10 además de algunos Value-Set de la guía coreCL. Esto se hizo de forma local en el servido

### Carga de terminologías

Para cargar las terminologías en Snowstorm, se utiliza la API REST. Para ello, primero debes posicionarte en el directorio donde se encuentren los archivos .zip con la terminología en el terminal. Luego, ejecuta los comandos correspondientes que utilizan la herramienta hapi-fhir-cli. En estos comandos, se especifica el nombre del archivo .zip de la terminología y se proporciona una URL que permite el reconocimiento y registro de la terminología cargada.

#### Loinc
```
 ./hapi-fhir-cli upload-terminology -d Loinc_2.74.zip -v r4 -t http://137.184.182.23:8080/fhir -u http://loinc.org -s 10GB
```

#### Cie-10
```
 ./hapi-fhir-cli upload-terminology -d cie_10_deis.zip -v r4 -t http://137.184.182.23:8080/fhir -u http://hl7.org/fhir/sid/icd-10 -s 1GB
```

#### Norma 2.3.1
```
 ./hapi-fhir-cli upload-terminology -d Anamnesis-820.zip -v r4 -t http://137.184.182.23:8080/fhir -u http://biomedica.uv.cl/SIMSADI/Anamnesis

 ./hapi-fhir-cli upload-terminology -d AreaUrbanoCensal-820.zip -v r4 -t http://137.184.182.23:8080/fhir -u http://biomedica.uv.cl/SIMSADI/Area-Urbano-Censal

 ./hapi-fhir-cli upload-terminology -d Comunas-820.zip -v r4 -t http://137.184.182.23:8080/fhir -u http://biomedica.uv.cl/SIMSADI/Comunas

 ./hapi-fhir-cli upload-terminology -d CondicionActividad-820.zip -v r4 -t http://137.184.182.23:8080/fhir -u http://biomedica.uv.cl/SIMSADI/Condicion-Actividad

 ./hapi-fhir-cli upload-terminology -d ConsultaMedica-820.zip -v r4 -t http://137.184.182.23:8080/fhir -u http://biomedica.uv.cl/SIMSADI/Consulta-Medica

 ./hapi-fhir-cli upload-terminology -d ConsultaMedicaEspecialidad-820.zip -v r4 -t http://137.184.182.23:8080/fhir -u http://biomedica.uv.cl/SIMSADI/Consulta-Medica-Especialidad

 ./hapi-fhir-cli upload-terminology -d ConsultaOdontoEspecialidad-820.zip -v r4 -t http://137.184.182.23:8080/fhir -u http://biomedica.uv.cl/SIMSADI/Consulta-Odonto-Especialidad

 ./hapi-fhir-cli upload-terminology -d Diagnostico-820.zip -v r4 -t http://137.184.182.23:8080/fhir -u http://biomedica.uv.cl/SIMSADI/Diagnostico

 ./hapi-fhir-cli upload-terminology -d EspecialidadBioquimica-820.zip -v r4 -t http://137.184.182.23:8080/fhir -u http://biomedica.uv.cl/SIMSADI/Especialidad-Bioquimica

 ./hapi-fhir-cli upload-terminology -d EspecialidadFarma-820.zip -v r4 -t http://137.184.182.23:8080/fhir -u http://biomedica.uv.cl/SIMSADI/Especialidad-Farma

 ./hapi-fhir-cli upload-terminology -d EspecialidadMedica-820.zip -v r4 -t http://137.184.182.23:8080/fhir -u http://biomedica.uv.cl/SIMSADI/Especialidad-Medica

 ./hapi-fhir-cli upload-terminology -d EspecialidadOdontologica-820.zip -v r4 -t http://137.184.182.23:8080/fhir -u http://biomedica.uv.cl/SIMSADI/Especialidad-Odontologica

 ./hapi-fhir-cli upload-terminology -d EstadoCivil-820.zip -v r4 -t http://137.184.182.23:8080/fhir -u http://biomedica.uv.cl/SIMSADI/Estado-Civil

 ./hapi-fhir-cli upload-terminology -d IdentidadGenero-820.zip -v r4 -t http://137.184.182.23:8080/fhir -u http://biomedica.uv.cl/SIMSADI/Identidad-Genero

 ./hapi-fhir-cli upload-terminology -d InstitucionEmisoraTitulo-820.zip -v r4 -t http://137.184.182.23:8080/fhir -u http://biomedica.uv.cl/SIMSADI/Institucion-Emisora-Titulo

 ./hapi-fhir-cli upload-terminology -d InstitucionEspecialidad-820.zip -v r4 -t http://137.184.182.23:8080/fhir -u http://biomedica.uv.cl/SIMSADI/Institucion-Especialidad

 ./hapi-fhir-cli upload-terminology -d LeyesPrevisionales-820.zip -v r4 -t http://137.184.182.23:8080/fhir -u http://biomedica.uv.cl/SIMSADI/Leyes-Previsionales

 ./hapi-fhir-cli upload-terminology -d ModalidadAtencionFonasa-820.zip -v r4 -t http://137.184.182.23:8080/fhir -u http://biomedica.uv.cl/SIMSADI/Modalidad-Atencion-Fonasa

 ./hapi-fhir-cli upload-terminology -d NivelAtencion-820.zip -v r4 -t http://137.184.182.23:8080/fhir -u http://biomedica.uv.cl/SIMSADI/Nivel-Atencion

 ./hapi-fhir-cli upload-terminology -d NivelComplejidad-820.zip -v r4 -t http://137.184.182.23:8080/fhir -u http://biomedica.uv.cl/SIMSADI/Nivel-Complejidad

 ./hapi-fhir-cli upload-terminology -d OcupacionDetallada-820.zip -v r4 -t http://137.184.182.23:8080/fhir -u http://biomedica.uv.cl/SIMSADI/Ocupacion-Detallada

 ./hapi-fhir-cli upload-terminology -d OcupacionPaciente-820.zip -v r4 -t http://137.184.182.23:8080/fhir -u http://biomedica.uv.cl/SIMSADI/OcupacionPaciente

 ./hapi-fhir-cli upload-terminology -d OtroTipoEstablecimientoAsistencial-820.zip -v r4 -t http://137.184.182.23:8080/fhir -u http://biomedica.uv.cl/SIMSADI/Otro-Tipo-Establecimiento-Asistencial

 ./hapi-fhir-cli upload-terminology -d Paises-820.zip -v r4 -t http://137.184.182.23:8080/fhir -u http://biomedica.uv.cl/SIMSADI/Paises

 ./hapi-fhir-cli upload-terminology -d PrevisionSalud-820.zip -v r4 -t http://137.184.182.23:8080/fhir -u http://biomedica.uv.cl/SIMSADI/Prevision-Salud

 ./hapi-fhir-cli upload-terminology -d Provincia-820.zip -v r4 -t http://137.184.182.23:8080/fhir -u http://biomedica.uv.cl/SIMSADI/Provincia

 ./hapi-fhir-cli upload-terminology -d PueblosOriginarios-820.zip -v r4 -t http://137.184.182.23:8080/fhir -u http://biomedica.uv.cl/SIMSADI/PueblosOriginarios

 ./hapi-fhir-cli upload-terminology -d Regiones-820.zip -v r4 -t http://137.184.182.23:8080/fhir -u http://biomedica.uv.cl/SIMSADI/Regiones

 ./hapi-fhir-cli upload-terminology -d Religiones-820.zip -v r4 -t http://137.184.182.23:8080/fhir -u http://biomedica.uv.cl/SIMSADI/Religion

 ./hapi-fhir-cli upload-terminology -d SEREMI-820.zip -v r4 -t http://137.184.182.23:8080/fhir -u http://biomedica.uv.cl/SIMSADI/SEREMI

 ./hapi-fhir-cli upload-terminology -d ServiciosSalud-820.zip -v r4 -t http://137.184.182.23:8080/fhir -u http://biomedica.uv.cl/SIMSADI/Servicios-Salud

 ./hapi-fhir-cli upload-terminology -d SexoBiologico-820.zip -v r4 -t http://137.184.182.23:8080/fhir -u http://biomedica.uv.cl/SIMSADI/Sexo-Biologico

 ./hapi-fhir-cli upload-terminology -d SituacionDiscapacidadNivel-820.zip -v r4 -t http://137.184.182.23:8080/fhir -u http://biomedica.uv.cl/SIMSADI/Situacion-Discapacidad-Nivel

 ./hapi-fhir-cli upload-terminology -d SituacionDiscapacidadOrigen-820.zip -v r4 -t http://137.184.182.23:8080/fhir -u http://biomedica.uv.cl/SIMSADI/Situacion-Discapacidad-Origen

 ./hapi-fhir-cli upload-terminology -d TipoAtencionEstablecimiento-820.zip -v r4 -t http://137.184.182.23:8080/fhir -u http://biomedica.uv.cl/SIMSADI/Tipo-Atencion-Establecimiento

 ./hapi-fhir-cli upload-terminology -d TipoDocumento-820.zip -v r4 -t http://137.184.182.23:8080/fhir -u http://biomedica.uv.cl/SIMSADI/Tipo-DocumentoDEIS

 ./hapi-fhir-cli upload-terminology -d TipoEstablecimientoHospitalario-820.zip -v r4 -t http://137.184.182.23:8080/fhir -u http://biomedica.uv.cl/SIMSADI/Tipo-Establecimiento-Hospitalario

 ./hapi-fhir-cli upload-terminology -d TipoEstablecimientoPublico-820.zip -v r4 -t http://137.184.182.23:8080/fhir -u http://biomedica.uv.cl/SIMSADI/Tipo-Establecimiento-Publico

 ./hapi-fhir-cli upload-terminology -d TipoEstabPubAtenPrim-820.zip -v r4 -t http://137.184.182.23:8080/fhir -u http://biomedica.uv.cl/SIMSADI/Tipo-Establecimiento-Publico-Atencion-Primaria

 ./hapi-fhir-cli upload-terminology -d TipoEstabPubAtenEspec-820.zip -v r4 -t http://137.184.182.23:8080/fhir -u http://biomedica.uv.cl/SIMSADI/Tipo-Establecimiento-Publico-Atencion-Especialidad

 ./hapi-fhir-cli upload-terminology -d TipoOtroTelefono-820.zip -v r4 -t http://137.184.182.23:8080/fhir -u http://biomedica.uv.cl/SIMSADI/Tipo-Otro-Telefono

 ./hapi-fhir-cli upload-terminology -d TipoDocumentoDEIS-820.zip -v r4 -t http://137.184.182.23:8080/fhir -u http://biomedica.uv.cl/SIMSADI/Tipo-Documento-DEIS

 ./hapi-fhir-cli upload-terminology -d TipoPertinenciaEstab-820.zip -v r4 -t http://137.184.182.23:8080/fhir -u http://biomedica.uv.cl/SIMSADI/Tipo-Pertinencia-Establecimiento

 ./hapi-fhir-cli upload-terminology -d TipoPrestador-820.zip -v r4 -t http://137.184.182.23:8080/fhir -u http://biomedica.uv.cl/SIMSADI/Tipo-Prestador

 ./hapi-fhir-cli upload-terminology -d TipoSistemaSalud-820.zip -v r4 -t http://137.184.182.23:8080/fhir -u http://biomedica.uv.cl/SIMSADI/Tipo-Sistema-Salud

 ./hapi-fhir-cli upload-terminology -d TipoVia-820.zip -v r4 -t http://137.184.182.23:8080/fhir -u http://biomedica.uv.cl/SIMSADI/TipoVia

 ./hapi-fhir-cli upload-terminology -d TituloProfesional-820.zip -v r4 -t http://137.184.182.23:8080/fhir -u http://biomedica.uv.cl/SIMSADI/Titulo-Profesional

 ./hapi-fhir-cli upload-terminology -d TramosFonasa-820.zip -v r4 -t http://137.184.182.23:8080/fhir -u http://biomedica.uv.cl/SIMSADI/Tramos-Fonasa

 ./hapi-fhir-cli upload-terminology -d UltimoCursoAprobado-820.zip -v r4 -t http://137.184.182.23:8080/fhir -u http://biomedica.uv.cl/SIMSADI/Ultimo-Curso-Aprobado

 ./hapi-fhir-cli upload-terminology -d UltimoNivelAprobado-820.zip -v r4 -t http://137.184.182.23:8080/fhir -u http://biomedica.uv.cl/SIMSADI/Ultimo-Nivel-Aprobado


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




