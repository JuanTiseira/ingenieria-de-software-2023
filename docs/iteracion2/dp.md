# Trabajo en equipo

**Lider de equipo:** Sanabria Nicolas Guillermo

**Diseñador:** Kevin Jesus Aliendro

**Analista Funcional:** Juan Ignacio Tiseira

# Diseño OO

## Diagrama ER Regsitro de alumno


```mermaid
erDiagram
    CARRERA {
        integer id PK
        string descripcion
        string plan_de_estudio
        boolean estado

    }
    MATERIA {
        integer id PK
        string descripcion
        integer carrera FK
        integer anio
        integer modulo
    }
    ALUMNO {
        integer id PK
        integer dni
        string nombre
        string apellido
        string correo
        string domicilio
        string fecha_nacimiento
        integer carrera FK
    }
    ALUMNO-MATERIA{
        integer id PK
        integer id_materia FK
        integer id_asistencia FK
        integer id_alumno FK
        integer condicion
    }
    CONDICION{
        integer id PK
        string descripccion
    }
    MODULO{
        integer id PK
        string descripccion
    }
    ASISTENCIA{
        integer id PK
        date fecha
        integer alumno_materia_id FK
        boolean estado
    }
    ESTADO-ASISTENCIA{
        integer id PK
        string descripccion
    }
    ALUMNO-MATERIA ||--|{ CONDICION : ""
    MATERIA ||--|{ CARRERA : ""
    MATERIA ||--|{ MODULO : ""
    ASISTENCIA ||--|{ ESTADO-ASISTENCIA : ""
    ALUMNO ||--|{ ALUMNO-MATERIA : ""
    ASISTENCIA ||--|{ ALUMNO-MATERIA : ""
    MATERIA ||--|{ ALUMNO-MATERIA : ""
```

<br>
<br>
<br>



### Diagrama de Clases 

```mermaid
classDiagram
    class CARRERA {
        +id: integer
        +descripcion: string
        +estado: boolean
    }
    class MATERIA {
        +id: integer
        +descripcion: string
        +carrera: CARRERA
        +anio: integer
        +modulo: integer
        +plan_de_estudio: integer
    }
    class ALUMNO {
        +id: integer
        +dni: integer
        +nombre: string
        +apellido: string
        +correo: string
        +fecha_nacimiento: date
        +domicilio: string
        +carrera: CARRERA
    }
    class ASISTENCIA {
        +id: integer
        +fecha: date
        +alumno: id
        +estado: boolean
        +registrarAsistencia(usuario: USUARIO, fecha: string, materia: MATERIA): boolean
        +modificarAsistencia(usuario: USUARIO, fecha: string, materia: MATERIA, asistencia: ASISTENCIA): boolean
        +eliminarAsistencia(asistencia: ASISTENCIA): boolean
    }
    class USUARIO {
        +id: integer
        +nombre: string
        +apellido: string
        +dni: integer
        +password: string
        +estado: boolean
        +rol: string
    }
    class Autenticación {
        +autenticar(nombreUsuario: string, contraseña: string): boolean
    }
    class Sesión {
        +iniciarSesión(usuario: USUARIO): boolean
        +cerrarSesión(): void
    }
    ASISTENCIA ..> ALUMNO: 
    ASISTENCIA -- USUARIO: 
    USUARIO --> Autenticación: 
    USUARIO --> Sesión: 
    ASISTENCIA ..> CARRERA
    CARRERA -- MATERIA 
```

<br>

# Wireframe y caso de uso
## Wireframe Gestión de Asistencia por Materia y Período
![Ejemplo de Imagen](wireframes/registro_alumnos.png)
![Ejemplo de Imagen](wireframes/modificacion_alumnos.png)
![Ejemplo de Imagen](wireframes/Detalle_alumnos.png)
![Ejemplo de Imagen](wireframes/Consulta_asistencia_alumno.png)


<br>
<br>
<br>

## Caso de uso Registro de alumnos  

**Actor Principal:** Preceptor

**Resumen:** El preceptor registra la asistencia de los alumnos en una clase, filtrando por diferentes criterios y permitiendo marcar ausencias y adjuntar justificaciones.

**Precondiciones:**
- El preceptor debe haber iniciado sesión en el sistema.
- Deben existir registros de alumnos inscritos en la materia.

**Flujo Principal:**

1. El preceptor inicia sesión en el sistema.
2. El preceptor selecciona la materia o asignatura que desea tomar asistencia, utilizando el filtro disponible para "Carrera", "Año", "Módulo", y "Materia".
3. El sistema muestra una lista de alumnos filtrados segun "Carrera", "Año", "Módulo", y "Materia", que se hayan seleccionado.
4. El sistema muestra la lista de alumnos que coinciden con los criterios de filtro seleccionados.

5. El preceptor revisa la lista de alumnos y, para cada estudiante, tiene las siguientes opciones:
   - Marcar "Presente" si el estudiante asistió.
   - Adjuntar un archivo de justificación si el estudiante está ausente seleccionando el alumno.
   - Dejar sin marcar si el estado de asistencia es ausente.

6. El preceptor hace clic en guardar.

**Postcondiciones:**
- Los registros de asistencia se actualizan en el sistema, indicando si un estudiante estuvo presente, ausente o con justificación adjunta.

**Flujos Alternativos:**

1. En el paso 5, el preceptor puede adjuntar archivos de justificación para estudiantes ausentes. El sistema almacena estos archivos en un repositorio adecuado y los relaciona con los registros de asistencia correspondientes.

**Excepciones:**

1. En el paso 3, si no hay alumnos inscritos en la clase que coincidan con los criterios de filtro seleccionados, el sistema muestra un mensaje de notificación.

<br>
<br>

#### Registrar Alumnos

**Actor Principal:** Usuario autorizado (administrador y Preceptor.)

**Resumen:**El usuario registra un alumno ingresando los datos del mismo.

**Precondiciones:**
- El usuario tiene permisos para registrar nuevos alumnos.


**Flujo Principal:**
1. El usuario inicia sesión en el sistema.
2. Accede al módulo de registro de alumnos.
3. Completa los detalles del nuevo alumno, como dni, nombre, apellidos, dirección, correo, fecha de nacimiento, etc.
4. Guarda la información, generando un identificador único para el alumno.

**Postcondiciones:** 
- Si el alumno existe el sistema indica al usuario.
- Si los campos estan vacios el sistema indica al usuario.
- Si el alumno es registrado exitosamente el sistema lo notificara.

**Flujo Alternativo:**
- Si hay campos obligatorios faltantes o datos incorrectos, se muestra un mensaje de error y se solicita la corrección.

#### Modificar Alumnos

**Actor Principal:** Usuario autorizado (administrador y Preceptor.)

**Resumen:**El usuario modifica los datos de un alumno existente.

**Flujo Principal:**
1. El usuario inicia sesión y accede al módulo de gestión de alumnos.
2. Busca al alumno por su nombre, apellido, curso, número de DNI y carrera .
3. Selecciona al alumno y modifica la información relevante, como cambios en la dirección, número de teléfono, etc.
4. Guarda los cambios actualizados en el sistema.

**Postcondiciones:** 
- Si alumno buscado no existe el sistema lo notificará.

**Flujo Alternativo:**
- Si el alumno no es encontrado, se muestra un mensaje indicando que no se encontraron resultados.

**Precondiciones:**
- El usuario tiene permisos para modificar la información de los alumnos.


#### Eliminar Alumnos

**Actor Principal:** Usuario autorizado (administrador y Preceptor.)

**Resumen:**El usuario elimina un alumno del registro.

**Flujo Principal:**
1. El usuario inicia sesión y accede al módulo de gestión de alumnos.
2. Busca al alumno que se va a eliminar,por sus datos citados en el caso de uso de modificacion.
3. Selecciona al alumno y solicita eliminarlo del sistema.
4. El sistema elimina todos los registros relacionados con el alumno, después de confirmar la acción.

**Flujo Alternativo:**
- Si el sistema no puede eliminar al alumno por alguna razón, se muestra un mensaje indicando el problema.

**Postcondiciones:** 
- Si el usuario quiere eliminar un registro de alumnos, el sistema lo notificara.
- Si el registro es eliminado exitosamente el sistema avisara.


**Precondiciones:**
- El usuario tiene permisos para eliminar alumnos del sistema.





## Backlog Iteracion

| Historia de Usuario          | Puntaje |
|-----------------------------|---------|
| HU-01: Registro de Alumno | 5      |
| HU-02: Asignación de Carrera y Materias | 3       |
| HU-03: Consulta de Asistencia de Alumno |    4   |

# Tareas

- Diseño wireframe
    - Registro de alumno
    - Asignacion de carrera y materias
    - formulario de consulta de asistencias de alumno

- Diagrama ER
    - Adaptacion del DER existente.

- Diagrama de Clases
    - Adapttacion del diagrama existente

- Casos de uso
    - Caso de uso registrar alumno
    - Caso de uso Asignar Carrera y Materia
    - Caso de uso consulta de asistencia de alumno
    
# Retrospectiva

- respeten para que los respeten 
- eduquese lo mas que pueda
- conduzca con cuidado

**"Dra. Ana Maria Polo"**