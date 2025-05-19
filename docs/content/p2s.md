# **Actividad: Creación de una Base de Datos Básica para una Escuela**

### **Enunciado**

Eres el administrador de una escuela que necesita organizar la información de sus **estudiantes**, **profesores**, **cursos** y **aulas** en una base de datos relacional. Tu tarea es diseñar y crear una base de datos llamada `Escuela` con cuatro tablas: `estudiantes`, `profesores`, `cursos` y `aulas`. Cada tabla debe tener columnas con tipos de datos apropiados y una clave primaria para identificar registros únicos. Sigue los pasos a continuación para completar la actividad.

### **Instrucciones Paso a Paso**

1. **Crea la base de datos**:
   - Usa el comando `CREATE DATABASE` para crear una base de datos llamada `Escuela`.
   - Selecciona la base de datos con `USE Escuela;` para trabajar en ella.

2. **Crea la tabla `estudiantes`**:
   - Debe tener las siguientes columnas:
     - `id_estudiante`: Identificador único del estudiante (entero, clave primaria).
     - `nombre`: Nombre del estudiante (texto, máximo 100 caracteres, obligatorio).
     - `fecha_nacimiento`: Fecha de nacimiento del estudiante (fecha, obligatorio).
   - Usa tipos de datos adecuados y agrega la restricción `PRIMARY KEY` para `id_estudiante`.

3. **Crea la tabla `profesores`**:
   - Debe tener las siguientes columnas:
     - `id_profesor`: Identificador único del profesor (entero, clave primaria).
     - `nombre`: Nombre del profesor (texto, máximo 100 caracteres, obligatorio).
     - `email`: Correo electrónico del profesor (texto, máximo 100 caracteres, obligatorio).
   - Usa la restricción `PRIMARY KEY` para `id_profesor`.

4. **Crea la tabla `cursos`**:
   - Debe tener las siguientes columnas:
     - `id_curso`: Identificador único del curso (entero, clave primaria).
     - `nombre_curso`: Nombre del curso (texto, máximo 150 caracteres, obligatorio).
     - `creditos`: Número de créditos del curso (entero, obligatorio).
   - Usa la restricción `PRIMARY KEY` para `id_curso`.

5. **Crea la tabla `aulas`**:
   - Debe tener las siguientes columnas:
     - `id_aula`: Identificador único del aula (entero, clave primaria).
     - `nombre_aula`: Nombre o código del aula (texto, máximo 50 caracteres, obligatorio).
     - `capacidad`: Capacidad máxima de estudiantes (entero, obligatorio).
   - Usa la restricción `PRIMARY KEY` para `id_aula`.

6. **Prueba y verifica tu base de datos**:
   - Escribe el código SQL completo para crear la base de datos y las tablas.
   - Opcional: Inserta un registro de ejemplo en cada tabla para verificar que las tablas funcionan correctamente (esto no es obligatorio, pero es útil para practicar el comando `INSERT`).

### **Pistas**
- Usa tipos de datos como `INT`, `VARCHAR`, `DATE` y asegúrate de que sean adecuados para cada columna.
- Asegúrate de que cada tabla tenga una clave primaria definida con `PRIMARY KEY`.
- Si usas MySQL, PostgreSQL u otro SGBD, la sintaxis es generalmente la misma, pero verifica la documentación para comandos como `DEFAULT` o tipos de datos específicos.

### **Entrega**
Escribe un archivo SQL que contenga todos los comandos necesarios para crear la base de datos y las tablas. Asegúrate de incluir comentarios que expliquen cada paso.

---

## **Solución de Ejemplo**

A continuación, se proporciona la solución actualizada en un archivo SQL, envuelto en un artefacto con el mismo `artifact_id` del artefacto anterior (ya que es una actualización de la actividad), pero con un nuevo título para reflejar el cambio de tema.

```sql
-- Paso 1: Crear la base de datos
CREATE DATABASE Escuela;

-- Seleccionar la base de datos para trabajar en ella
USE Escuela;

-- Paso 2: Crear la tabla 'estudiantes'
CREATE TABLE estudiantes (
    id_estudiante INT PRIMARY KEY,
    nombre VARCHAR(100) NOT NULL,
    fecha_nacimiento DATE NOT NULL
);

-- Paso 3: Crear la tabla 'profesores'
CREATE TABLE profesores (
    id_profesor INT PRIMARY KEY,
    nombre VARCHAR(100) NOT NULL,
    email VARCHAR(100) NOT NULL
);

-- Paso 4: Crear la tabla 'cursos'
CREATE TABLE cursos (
    id_curso INT PRIMARY KEY,
    nombre_curso VARCHAR(150) NOT NULL,
    creditos INT NOT NULL
);

-- Paso 5: Crear la tabla 'aulas'
CREATE TABLE aulas (
    id_aula INT PRIMARY KEY,
    nombre_aula VARCHAR(50) NOT NULL,
    capacidad INT NOT NULL
);

-- Opcional: Insertar datos de ejemplo para probar las tablas
INSERT INTO estudiantes (id_estudiante, nombre, fecha_nacimiento) 
VALUES (1, 'María López', '2005-03-15');

INSERT INTO profesores (id_profesor, nombre, email) 
VALUES (1, 'Carlos Gómez', 'carlos.gomez@escuela.com');

INSERT INTO cursos (id_curso, nombre_curso, creditos) 
VALUES (1, 'Matemáticas Básicas', 4);

INSERT INTO aulas (id_aula, nombre_aula, capacidad) 
VALUES (1, 'Aula 101', 30);
```

---

## **Guía para los Estudiantes**

1. **Ejecuta el código**:
   - Usa un SGBD como MySQL, PostgreSQL o SQL Server.
   - Copia el código SQL en una herramienta como MySQL Workbench, pgAdmin o SQL Server Management Studio.
   - Ejecuta los comandos en orden para crear la base de datos y las tablas.

2. **Verifica las tablas**:
   - Usa `DESCRIBE nombre_tabla;` (en MySQL) o `\d nombre_tabla` (en PostgreSQL) para verificar la estructura de cada tabla.
   - Si insertaste datos de ejemplo, ejecuta `SELECT * FROM nombre_tabla;` para ver los registros.

3. **Errores comunes y cómo solucionarlos**:
   - **Falta de `NOT NULL`**: Asegúrate de que las columnas indicadas como obligatorias tengan esta restricción.
   - **Tipos de datos incorrectos**: Usa `DATE` para fechas, `VARCHAR` para textos y `INT` para números enteros.
   - **Olvidar la clave primaria**: Cada tabla debe tener una columna con `PRIMARY KEY`.

4. **Ampliación (opcional)**:
   - Agrega más columnas, como `telefono` en `profesores` o `ubicacion` en `aulas`.
   - Practica comandos DML como `INSERT`, `UPDATE` o `SELECT` con las tablas creadas.
   - Crea una tabla adicional, como `asistencias`, con columnas simples.

---

## **Notas para el Profesor**

- **Nivel**: Principiante (introducción a SQL y bases de datos).
- **Duración estimada**: 25-35 minutos, dependiendo de si se incluyen datos de ejemplo.
- **Evaluación**:
  - Verifica que el código SQL sea correcto y funcional.
  - Evalúa el uso adecuado de tipos de datos, claves primarias y restricciones `NOT NULL`.
  - Considera puntos extra por comentarios claros, datos de ejemplo o ampliaciones.
- **Variaciones**:
  - Cambia el tema (e.g., hospital, tienda, biblioteca).
  - Pide a los estudiantes que agreguen más tablas o columnas.
  - Introduce restricciones adicionales como `DEFAULT` o `UNIQUE` para un desafío extra.

Esta actividad mantiene la simplicidad al evitar claves foráneas, pero amplía la práctica con cuatro tablas y un tema nuevo (escuela). Si necesitas más modificaciones, actividades adicionales o un enfoque diferente, házmelo saber. 😊