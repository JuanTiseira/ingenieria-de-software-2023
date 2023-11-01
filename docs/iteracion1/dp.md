# Trabajo en equipo

**Lider de equipo:** Kevin Jesus Aliendro

**Diseñador:** Juan Ignacio Tiseira

**Analista Funcional:** Sanabria Nicolas Guillermo


# Diseño OO

## Diagrama ER Regsitro de asistencia


```mermaid
erDiagram
    CARRERA {
        integer id PK
        string descripcion
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
        string nombre
        string apellido
        string email
        string domicilio
        integer carrera FK
    }
    ALUMNO-MATERIA{
        integer id PK
        integer alumno FK
        integer materia FK
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

### Diagrama ER Login


```mermaid
erDiagram
    USUARIO ||--o{ ROLES : ""
    USUARIO {
        integer id PK
        string nombre
        string apellido
        integer dni
        string password
        boolean estado
    }
    ROLES {
        integer id PK
        string descripcion 
    }
```
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
    }
    class ALUMNO {
        +id: integer
        +nombre: string
        +apellido: string
        +email: string
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

### Wireframe Iniciar Sesión
![Ejemplo de Imagen](wireframes/login.jpeg)
<br>
<br>
<br>
## Caso de Uso: Iniciar Sesión

**Actor Principal:** Usuario registrado

**Resumen:** El usuario inicia sesión en el sistema ingresando sus credenciales (nombre de usuario y contraseña).

**Precondiciones:** 
- El usuario debe estar registrado en el sistema.
- El usuario debe estar en la página de inicio de sesión.

**Flujo Principal:**

1. El usuario ingresa a la página de inicio de sesión.
2. El sistema muestra un formulario de inicio de sesión con dos campos: "Nombre de Usuario" y "Contraseña".
3. El usuario ingresa su nombre de usuario y contraseña en los campos correspondientes.
4. El usuario hace clic en el botón "Iniciar Sesión".
5. El sistema verifica las credenciales del usuario:
   - Si las credenciales son válidas, el sistema autentica al usuario y le permite acceder a su cuenta.
   - Si las credenciales son inválidas, el sistema muestra un mensaje de error y permite al usuario intentar de nuevo.

**Postcondiciones:**
- Si las credenciales son válidas, el usuario inicia sesión y accede a la pantalla principal.
- Si las credenciales son inválidas, se notifica al usuario.

**Notas:**
- El sistema debe implementar medidas de seguridad adecuadas, como el cifrado de contraseñas, para proteger la información del usuario.

<br>
<br>
<br>
<br>
<br>

## Wireframe Gestión de Asistencia por Materia y Período
![Ejemplo de Imagen](wireframes/asistencias1.jpeg)
![Ejemplo de Imagen](wireframes/asistencias2.jpeg)

<br>
<br>
<br>

## Caso de uso Gestión de Asistencia por Materia y Período

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
<br>

# Backlog de iteracion

| Historia de Usuario          | Puntaje |      Tiempo estimado en horas |
|-----------------------------|---------|---------------------|
| HU-06: Inicio de Sesion y Seguridad | 3    |   32    |
| HU-03: Gestión de Asistencia por Materia y Período | 5   |   48    |

# Tareas

- Diseño wireframe
- Diagrama ER
- Diagrama de Clases
- Casos de uso