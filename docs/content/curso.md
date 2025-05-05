# **Estructura del Curso: Bases de Datos Relacionales (60 horas totales)**

#### **Clase 1: Introducción a las Bases de Datos**
- **Objetivo**: Comprender qué son las bases de datos y su importancia.
- **Contenido**:
  - Definición y tipos de bases de datos (relacionales, no relacionales).
  - Historia y evolución de los SGBD (Sistemas Gestores de Bases de Datos).
  - Introducción a los conceptos: tablas, filas, columnas, claves.
  - Herramientas: MySQL, PostgreSQL, SQLite (instalación y configuración).
- **Práctica**:
  - Instalar un SGBD (MySQL/PostgreSQL).
  - Crear una base de datos simple y explorar la interfaz.
- **Evaluación**: Quiz sobre conceptos básicos y discusión sobre casos de uso.
- **Duración**: Teoría (2.5h), Práctica (2.5h), Evaluación (1h).

#### **Clase 2: Fundamentos del Modelo Relacional**
- **Objetivo**: Entender los principios del modelo relacional.
- **Contenido**:
  - Reglas de Codd para bases de datos relacionales.
  - Entidades, atributos y relaciones.
  - Claves primarias, foráneas y su rol.
  - Normalización: conceptos básicos (1NF, 2NF, 3NF).
- **Práctica**:
  - Diseñar un esquema relacional simple (ejemplo: sistema de biblioteca).
  - Identificar claves primarias y foráneas en diagramas.
- **Evaluación**: Ejercicio de modelado básico y revisión grupal.
- **Duración**: Teoría (2.5h), Práctica (2.5h), Evaluación (1h).

#### **Clase 3: Lenguaje SQL - Fundamentos**
- **Objetivo**: Aprender los comandos básicos de SQL.
- **Contenido**:
  - Estructura de SQL: DDL, DML, DCL, TCL.
  - Comandos básicos: CREATE, INSERT, SELECT, UPDATE, DELETE.
  - Tipos de datos en SQL (INT, VARCHAR, DATE, etc.).
- **Práctica**:
  - Crear tablas con restricciones (NOT NULL, UNIQUE).
  - Insertar y consultar datos en una base de datos predefinida.
- **Evaluación**: Resolver ejercicios de consultas básicas.
- **Duración**: Teoría (2h), Práctica (3h), Evaluación (1h).

#### **Clase 4: Consultas Avanzadas en SQL**
- **Objetivo**: Dominar consultas más complejas.
- **Contenido**:
  - Operadores: WHERE, AND, OR, LIKE, BETWEEN.
  - Funciones de agregación: COUNT, SUM, AVG, MAX, MIN.
  - Ordenación (ORDER BY) y agrupación (GROUP BY, HAVING).
- **Práctica**:
  - Escribir consultas con filtros y agregaciones (ejemplo: ventas por región).
  - Resolver problemas prácticos con datos reales.
- **Evaluación**: Mini-proyecto de consultas sobre un dataset.
- **Duración**: Teoría (2h), Práctica (3h), Evaluación (1h).

#### **Clase 5: Relaciones y Joins**
- **Objetivo**: Comprender y aplicar relaciones entre tablas.
- **Contenido**:
  - Tipos de relaciones: 1:1, 1:N, N:N.
  - Tipos de JOIN: INNER, LEFT, RIGHT, FULL.
  - Uso de claves foráneas en consultas.
- **Práctica**:
  - Crear una base de datos con múltiples tablas relacionadas.
  - Escribir consultas con JOINs para combinar datos.
- **Evaluación**: Ejercicios de JOINs y discusión de resultados.
- **Duración**: Teoría (2.5h), Práctica (2.5h), Evaluación (1h).

#### **Clase 6: Normalización y Diseño de Bases de Datos**
- **Objetivo**: Diseñar bases de datos eficientes.
- **Contenido**:
  - Proceso de normalización en detalle (hasta 3NF).
  - Diagramas ER (Entidad-Relación) y su traducción a tablas.
  - Buenas prácticas en diseño de bases de datos.
- **Práctica**:
  - Diseñar un diagrama ER para un caso práctico (ejemplo: tienda online).
  - Normalizar un conjunto de datos no estructurado.
- **Evaluación**: Presentación de diagramas ER y retroalimentación.
- **Duración**: Teoría (2.5h), Práctica (2.5h), Evaluación (1h).

#### **Clase 7: Índices y Optimización**
- **Objetivo**: Mejorar el rendimiento de las bases de datos.
- **Contenido**:
  - Qué son los índices y cómo funcionan.
  - Creación y gestión de índices (CREATE INDEX).
  - Introducción al análisis de rendimiento (EXPLAIN PLAN).
- **Práctica**:
  - Crear índices en una base de datos existente.
  - Comparar tiempos de consulta con y sin índices.
- **Evaluación**: Análisis de consultas optimizadas.
- **Duración**: Teoría (2h), Práctica (3h), Evaluación (1h).

#### **Clase 8: Transacciones y Seguridad**
- **Objetivo**: Gestionar transacciones y proteger datos.
- **Contenido**:
  - Concepto de transacciones: ACID.
  - Comandos: COMMIT, ROLLBACK, SAVEPOINT.
  - Gestión de usuarios y permisos (GRANT, REVOKE).
- **Práctica**:
  - Simular transacciones en un escenario real (ejemplo: transferencias bancarias).
  - Configurar roles y permisos en una base de datos.
- **Evaluación**: Ejercicio de transacciones y revisión de seguridad.
- **Duración**: Teoría (2.5h), Práctica (2.5h), Evaluación (1h).

#### **Clase 9: Introducción a Procedimientos y Triggers**
- **Objetivo**: Automatizar tareas en bases de datos.
- **Contenido**:
  - Procedimientos almacenados: creación y uso.
  - Triggers: definición y casos de uso.
  - Introducción a vistas (CREATE VIEW).
- **Práctica**:
  - Crear un procedimiento almacenado para un caso práctico.
  - Implementar un trigger para auditoría.
- **Evaluación**: Desarrollo de un trigger funcional.
- **Duración**: Teoría (2h), Práctica (3h), Evaluación (1h).

#### **Clase 10: Proyecto Final y Cierre**
- **Objetivo**: Aplicar todo lo aprendido en un proyecto integral.
- **Contenido**:
  - Revisión de conceptos clave.
  - Buenas prácticas en desarrollo y mantenimiento de bases de datos.
  - Introducción a temas avanzados (NoSQL, replicación, escalabilidad).
- **Práctica**:
  - Proyecto final: diseñar y desarrollar una base de datos completa (ejemplo: sistema de gestión escolar o tienda online).
  - Presentación de resultados.
- **Evaluación**: Evaluación del proyecto (funcionalidad, diseño, consultas) y retroalimentación grupal.
- **Duración**: Teoría (1.5h), Práctica (3.5h), Evaluación (1h).

### **Notas Adicionales**
- **Recursos**:
  - Software: MySQL Workbench, pgAdmin, DBeaver.
  - Datasets de práctica: datos abiertos (Kaggle, bases de datos de ejemplo como Sakila o Northwind).
  - Material teórico: presentaciones, guías de SQL, diagramas ER.
- **Metodología**:
  - Clases interactivas con ejemplos reales.
  - Ejercicios progresivos para reforzar conceptos.
  - Proyecto final para integrar conocimientos.
- **Evaluación**:
  - Participación en clase (20%).
  - Ejercicios prácticos (30%).
  - Proyecto final (50%).
- **Adaptaciones**:
  - Si el grupo tiene experiencia previa, acelerar los temas iniciales y profundizar en optimización o temas avanzados.
  - Incluir descansos cada 1.5-2 horas para mantener la atención.

