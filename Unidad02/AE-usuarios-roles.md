# Actividad Práctica Evaluable

## *La Academia "Er Sabel Centro Formativo" abre sus puertas*

### **Descripción**

Eres el nuevo administrador de Moodle de la academia ficticia **"Er
Sabel Centro Formativo"**, donde "se aprende con compás y se enseña con
salero". Tu misión es configurar los usuarios, roles y permisos
necesarios para que la academia funcione correctamente.

## **1. Objetivo**

Configurar correctamente usuarios, roles estándar y un rol personalizado
dentro de Moodle 5.1, comprobando su funcionamiento mediante accesos de
prueba.

## **2. Tareas a realizar**

### **A) Crear usuarios del personal de la academia**

Crea los siguientes usuarios con los roles indicados:

1. **María del Arte Flamenco**

- Rol: *Docente*
- Contexto: Curso "Guitarra para principiantes"

2. **Antonio "El Principiante"**

- Rol: *Docente sin permiso de edición*
- Contexto: Curso "Cante Novato 101"

3. **Lola Administresión**

- Rol: *Gestor / Manager*
- Contexto: Categoría "Formación Profesional"


### **B) Crear usuarios de alumnado**

Da de alta los siguientes estudiantes y asígnalos a sus cursos según el
profesor correspondiente:

- Rocío Palmas
- Manuel Taconeo
- Sira Ritmito
- Pepe Compás

Rol: **Estudiante**

------------------------------------------------------------------------

### **C) Crear un rol personalizado: "Coordinador de Aula"**

Este rol debe permitir:

**Permitir**:

- Ver cursos sin editar
- Ver detalles de usuarios
- Ver calificaciones
- Ver informes y registros

**Prohibir**:

- Editar cursos
- Modificar actividades
- Asignar roles

Nombre del rol: **Coordinador de Aula**
Identificador: `coordinadoraula`

### **D) Asignar el rol personalizado**

Crea el usuario:

- **Carmela Supervisión**

Asígnale el rol **Coordinador de Aula** en el curso "Técnicas de Palmas
Nivel 1".

### **E) Verificación final**

Accede con el usuario "Carmela Supervisión" y comprueba:

1. Qué apartados del curso puede ver
2. Qué acciones NO puede realizar
3. Que los estudiantes ven solo lo correspondiente a su rol
4. Que "Lola Administresión" puede gestionar cursos pero no acceder a
    la administración completa

## **3. Entrega**

Debes entregar un documento en formato PDF o Word con:

- Capturas o descripciones de cada usuario creado
- Configuración del rol "Coordinador de Aula"
- Capturas o descripción de la comprobación final
- Tabla resumen:

  Usuario                   Rol asignado   Contexto   ¿Funciona correctamente?
  ------------------------- -------------- ---------- --------------------------
  María del Arte Flamenco   Docente        Curso X    ✔️ / ❌
  ...                       ...            ...        ...

## **4. Rúbrica de evaluación**

  -----------------------------------------------------------------------
  Criterio         2 puntos           1 punto          0 puntos
  ---------------- ------------------ ---------------- ------------------
  Creación de      Correcta y         Algún error      Varios errores
  usuarios         completa           menor            

  Asignación de    Precisa y          Alguna duda      Incorrecta
  roles            coherente                           

  Rol              Configurado        Incompleto       Incorrecto
  personalizado    correctamente                       

  Verificación     Clara y completa   Poco detallada   Incorrecta o no
  final                                                entregada

  Presentación     Clara y organizada Aceptable        Desordenada
  -----------------------------------------------------------------------

¡Buen trabajo, administrador/a de *Er Sabel*!
