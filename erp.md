# Especificación de requisitos de software

## Enunciado del problema

Escriban algunas oraciones que describan el problema que están tratando de resolver, es decir, justifiquen por qué se necesita este software.

En el instituto el registro diario de asistencias se lleva de forma manual en una planilla, la cual es 
borrosa, no presenta ninguna informacion util para el preceptor, lo que hace que se pierda mucho tiempo
y se dificulte el proceso. Luego estos datos de todas las planillas se vuelcan a un excel de forma
manual,este proceso demanda mucho tiempo y es muy suceptible a errores al no tener variables normalizadas y datos que se carguen automaticamente, esto es crucial por que los datos sirven para ubicar a cada alumno, frente a las correlatividades, ver el estado en que se encuentra el alumno en cada materia, informe que debe ser presentado al profesor para que conozca que alumno puede o no rendir la materia.
Ademas cuando un alumno precisa conocer su estado en una materia, el preceptor debe buscar en el excel 
y calcular el total de asistencias del alumno.

Entonces el instuto busca facilitar el registro de los alumnos con sus datos personales y asignacion de la carrera que quieran y junto con las materias que puede cursar en base a las correlatividades de las mismas ,tambien se requiere poder hacer de manera sencilla el registro de las asistencias de cada carrera y curso(año)  asi como tambien la facilidad en obtener los informes correspondientes de los datos de los incriptos junto con las materias y asistencias del año.

## Clientes potenciales
 
¿Quiénes están afectados por este problema y se beneficiarían de la solución propuesta? *(es decir, los usuarios potenciales del software que están por construir)*.

El cliente potencial es el instituto en general ya que en la parte del preceptor que es quien se encarga de ir a los cursos, tomar las asistencias y verificar los datos del alumno asi como tambien en la parte del regente o administrador que es quien lleva el control general de los datos personales , asistencias que el preceptor o encargado correpondiente le devuelve, correlativas que los alumnos pueden cursar y demas.

El problema identificado afecta principalmente a los preceptores ya que ellos se encargan de confeccionar lso reportes acerca de las asistencias, que son presentados a los profesores para que conozcan que alumnos pueden rendir la materia y cuales no, ademas la estadisca de presencialidad tambien es util a nivel institucion para conocer que porcentaje de prensencialidad tiene la curricula.

Ademas los Alumnos muchas veces desean conocer su estado en cierta materia 
para no quedar irregulares.

## Solución propuesta 

Escriban algunas oraciones que describan cómo la solución de software resolverá el problema descrito anteriormente.

- El software de gestión académica permitirá a los preceptores y administradores del instituto llevar a cabo un registro eficiente de asistencias, correlatividades y datos personales de los alumnos. 

- Simplificará el proceso de registro de asistencias al proporcionar una interfaz amigable y fácil de usar para los preceptores, eliminando la necesidad de trabajar con planillas borrosas y la carga manual de datos en hojas de cálculo de Excel.

- Ofrecerá la capacidad de asignar a los alumnos a sus respectivas carreras y gestionar las correlatividades de las materias de manera automática, lo que garantiza que los estudiantes puedan inscribirse en las materias adecuadas de acuerdo a su progreso académico. 

- Proporcionará informes detallados sobre las asistencias, lo que facilitará la tarea de los preceptores al presentar informes a los profesores.

- Permitirá a la institución obtener estadísticas de presencialidad de manera más eficiente.

- Para los alumnos, la solución propuesta permitirá acceder fácilmente a su estado en cada materia, brindando transparencia y evitando que queden en situación irregular. En resumen.

## Requisitos

Enumeren los requisitos *(funcionales)* que debe tener el software para resolver el problema mencionado anteriormente. Es útil tratar de agrupar los requisitos en los que son esenciales *(debe estar)* y los que no son esenciales *(sería bueno que estén)*.
 
## Arquitectura de Software

**Tipo de Aplicación:** Aplicación web

**Arquitectura de Software:** Cliente-Servidor

**Lenguajes de Programación:** 
- Frontend: HTML, CSS, JavaScript
- Backend: Python, SQL

**Frameworks y Bibliotecas:**
- Frontend: React y Redux toolkit
- Backend: Django.

**Base de Datos:** Se utilizará la base de datos Mysql

**Tecnologías del Servidor Local:**
- Sistema Operativo: [Especificar el sistema operativo, p. ej., Windows, Linux]
- Servidor Web: Para desplegar el backend y el frontend se utilizara Nginx
- Servidor de Base de Datos Local: Despliegue de base de datos Mysql

**Otros Componentes o Tecnologías Relevantes:** Si se dispone de un servidor windows se va a virtualizar con hyper-v.

