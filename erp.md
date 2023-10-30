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

- Para los alumnos, la solución propuesta permitirá acceder fácilmente a su estado en cada materia, brindando transparencia y evitando que queden en situación irregular. 

## Requisitos

## Solución propuesta 

Escriban algunas oraciones que describan cómo la solución de software resolverá el problema descrito anteriormente.
 

# Requisitos

## Debe tener o estar:

### Registro de Alumno

1.Como preceptor, quiero registrar un nuevo alumno en el sistema con sus datos personales como su nombre, apellido, DNI, dirección, número de teléfono, fecha de nacimiento.

### Asignación de Carrera y Materias 

2.Como preceptor, quiero poder asignar a un alumno a una carrera y las materias que puede cursar al inicio de su inscripción. El sistema debe permitir seleccionar las materias de acuerdo con el plan de estudios, y la Secretaría Académica debe verificar si cumple con los requisitos.

### Consulta de Asistencia de Alumno

3.Como preceptor, quiero consultar la asistencia de un alumno ingresando su nombre, apellido o número de identificación. El sistema debe mostrar las fechas de clases a las que asistió, las fechas de ausencia y el motivo de la ausencia, además de proporcionar un gráfico de torta con el porcentaje de asistencias e inasistencias.

### Gestión de Correlatividades

4.Como preceptor, necesito que el sistema verifique automáticamente las correlatividades de las materias a las que un alumno quiere inscribirse. Debe mostrar si el alumno cumple con los requisitos previos.

### Gestión de Asistencia por Materia y Período

5.Como preceptor, necesito registrar la asistencia de los alumnos en cada sesión o clase. Los datos de asistencia deben ingresarse en el sistema, y el sistema debe permitir filtrar las materias y los períodos para una gestión más eficiente.

### Inicio de Sesión y Seguridad

6.Como preceptor, quiero que el sistema requiera un inicio de sesión para garantizar que solo los responsables tengan acceso. Esto debe incluir autenticación y autorización.

### Generación de Informes Automáticos

7.Como preceptor, deseo que el sistema permita generar informes, incluyendo listados de asistencia por alumno, listados de asistencia por materia, informes de rendimiento académico y correlatividades, para facilitar la gestión académica.

### Gestión de Ausencias Justificadas

8.Como preceptor, quiero poder registrar ausencias justificadas con sus respectivos justificativos.


## Seria Bueno:

### Consideración de Excepciones en la Asistencia

1.Como preceptor, necesito la capacidad de no tomar asistencia en circunstancias excepcionales, como cortes de luz o malas condiciones climáticas para que no marque inasistencia a la mayoría.

### Registro de Datos de Asignaturas

2.Como preceptor, necesito poder registrar información sobre las asignaturas, incluyendo nombre, código, descripción, créditos, duración (cuatrimestral o anual), docentes asignados y requisitos de correlatividad.

### Gestión de Alumnos Libres

3.Como preceptor, quiero que el sistema identifique automáticamente a los alumnos que no cumplen con los requisitos académicos, marcándolos como "libres" en una materia, lo que requiere que vuelvan a cursar en el próximo período académico.

### Alertas de Inasistencia

4.Como preceptor, necesito que el sistema genere alertas cuando un alumno esté a punto de quedar libre en una materia debido a inasistencias.

### Registro de Tardanzas

5.Como preceptor, quiero registrar la llegada tardía de un alumno como "tardanza", especificando la hora de llegada y si es justificada o no.

 
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

