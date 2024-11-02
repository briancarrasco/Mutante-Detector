**PRIMER PARCIAL DESARROLLO DE SOFTWARE**

Alumno: Brian Carrasco
Comision: 3k09

Mutante Detector

Este proyecto implementa un servicio que permite detectar si un humano es mutante basándose en su secuencia de ADN. Fue desarrollado en Java utilizando el framework Spring Boot y cumple con los requisitos de un examen de MercadoLibre.

Niveles Implementados: 

Nivel 1: Implementación de la función isMutant en una arquitectura con capas de Controlador, Servicio y Repositorio.

Nivel 2: Creación de una API REST desplegada en Render.

Nivel 3: Integración de una base de datos H2 para almacenar registros de ADN y exponer estadísticas de las verificaciones.

**Requisitos**
Para ejecutar este proyecto se necesita:

Java: versión 17 o superior
Maven: para gestionar dependencias y construir el proyecto
Spring Boot: para el desarrollo del servicio API
H2 Database: base de datos en memoria
JMeter: para pruebas de carga 
PostMan

**Ejecución Local**
1. Clonar el repositorio
2. Configurar la Base de Datos
3. Construir el proyecto
4. Ejecutar el proyecto

   
**Endpoints de la API**

Abrimos la aplicacion **POSTMAN** y realizaremos lo siguiente

1. Verificación de Mutante
Detecta si el ADN enviado pertenece a un mutante.

URL: http://localhost:8080/mutant/

Método HTTP: POST

Cuerpo de la solicitud (JSON)

{
  "dna": ["ATGCGA", "CAGTGC", "TTATGT", "AGAAGG", "CCCCTA", "TCACTG"]
}

Respuestas:

200 OK: El ADN pertenece a un mutante.

403 Forbidden: El ADN no pertenece a un mutante.

2. Estadísticas de Verificación
Devuelve un JSON con la cantidad de mutantes y humanos verificados.

URL: http://localhost:8080/stats

Método HTTP: GET

Respuesta (JSON):

{
  "count_mutant_dna": 40,
  "count_human_dna": 100,
  "ratio": 0.4
}

**Ejemplos de ADN**

Ejemplo de matriz **MUTANTE**
{
    "dna": ["ATGCGA", "CAGTGC", "TTATGT", "AGAAGG", "CCCCTA", "TCACTG"]
}
Ejemplo de matriz **NO MUTANTE**
{
    "dna": ["ATGATA", "GTCTTA", "AATTGG", "ACTAGT", "GGATTC", "AGGCAA"]
}
**Pruebas**
Pruebas Unitarias
Las pruebas unitarias están incluidas en el proyecto y pueden ejecutarse con:

mvn test

**Pruebas de Carga con JMeter**

Para garantizar que la API pueda soportar tráfico de 100 a 1 millón de peticiones por segundo, se realizaron pruebas de carga con Apache JMeter. El archivo de configuración de pruebas (mutante_detector.jmx) está disponible en el repositorio.

Ejecucion:

Configuración de HTTP Request en **JMeter**

Agrega un HTTP Request Sampler

Haz clic derecho en Thread Group > Add > Sampler > HTTP Request.

Completa los Campos como Sigue:

Server Name or IP: localhost

Port Number: 8080

Protocol: http (sin el s)

Path: /mutant/ (asegúrate de incluir la barra final)

Method: POST

Haz clic en la pestaña Body Data (en lugar de Parameters).

En Body Data, pega el siguiente JSON:

{
  "dna": ["ATGCGA", "CAGTGC", "TTATGT", "AGAAGG", "CCCCTA", "TCACTG"]
}

Agrega un View Results Tree.

Guarda la configuración.

Ejecuta la prueba haciendo clic en el botón de Play (el triángulo verde en la barra de herramientas).

Ve a View Results Tree y deberías ver la solicitud y respuesta como se mostró en Postman.

Y este seria el resultado final de mi proyecto para el parcial de desarrollo de software, desde ya muchas gracias y un cordial saludo.

