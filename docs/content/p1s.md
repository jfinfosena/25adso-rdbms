## **Ejercicio: Normalización de una Tabla de Vehículos**

A continuación, se presenta un ejercicio basado en el proceso de normalización descrito previamente. Deberás aplicar las tres primeras formas normales (**1NF**, **2NF**, **3NF**) a una tabla no normalizada que contiene información sobre ventas de vehículos en una concesionaria. El objetivo es identificar los problemas en la tabla inicial y transformarla paso a paso hasta alcanzar la **3NF**, siguiendo el formato del ejemplo anterior (mencionando solo el problema y la solución en cada paso).

---

### **Problema Inicial**

La concesionaria tiene una tabla no normalizada para registrar las ventas de vehículos. La tabla contiene redundancias, valores multivaluados y dependencias que generan anomalías en las operaciones de la base de datos.

**Tabla no normalizada: Ventas_Vehiculos**
| ID_Venta | ID_Cliente | Nombre_Cliente | Ciudad_Cliente | Vehiculos_Comprados | Precio_Total |
|----------|------------|----------------|----------------|---------------------|--------------|
| 1        | 201        | Laura          | Lima           | Sedan, SUV          | 45000        |
| 2        | 202        | Carlos         | Bogotá         | Camioneta           | 30000        |
| 3        | 201        | Laura          | Lima           | SUV, Hatchback      | 40000        |

**Problemas:**
- **Valores multivaluados**: La columna **Vehiculos_Comprados** contiene listas de vehículos (violación de 1NF).
- **Redundancia**: **Nombre_Cliente** y **Ciudad_Cliente** se repiten para el mismo cliente.
- **Dependencias parciales**: **Nombre_Cliente** y **Ciudad_Cliente** dependen solo de **ID_Cliente**, no de toda la clave primaria.
- **Dependencias transitivas**: **Ciudad_Cliente** depende de **ID_Cliente**, no directamente de la clave primaria.

---

### **Instrucciones para Resolver**

Transforma la tabla **Ventas_Vehiculos** en **1NF**, **2NF** y **3NF**, paso a paso. Para cada forma normal, identifica el **problema** específico y proporciona la **solución** con las tablas resultantes. Sigue el formato del ejemplo anterior:

1. **Paso 1: Llevar a 1NF**
   - Identifica el problema (por ejemplo, valores multivaluados).
   - Proporciona la tabla en 1NF.
2. **Paso 2: Llevar a 2NF**
   - Identifica el problema (por ejemplo, dependencias parciales).
   - Proporciona las tablas en 2NF.
3. **Paso 3: Llevar a 3NF**
   - Identifica el problema (por ejemplo, dependencias transitivas).
   - Proporciona las tablas en 3NF.

---

### **Solución Esperada**

A continuación, se proporciona la solución al ejercicio para que puedas verificar tu trabajo después de intentarlo.

#### **Paso 1: Llevar a 1NF**
**Problema**: 
- La columna **Vehiculos_Comprados** contiene valores multivaluados.
- No hay una clave primaria clara que garantice unicidad.

**Solución**: 
- Dividir **Vehiculos_Comprados** para que cada vehículo tenga su propia fila.
- Definir una clave primaria compuesta (**ID_Venta**, **Vehiculo_Comprado**).

**Tabla en 1NF: Ventas_Vehiculos**
| ID_Venta | ID_Cliente | Nombre_Cliente | Ciudad_Cliente | Vehiculo_Comprado | Precio_Total |
|----------|------------|----------------|----------------|-------------------|--------------|
| 1        | 201        | Laura          | Lima           | Sedan             | 45000        |
| 1        | 201        | Laura          | Lima           | SUV               | 45000        |
| 2        | 202        | Carlos         | Bogotá         | Camioneta         | 30000        |
| 3        | 201        | Laura          | Lima           | SUV               | 40000        |
| 3        | 201        | Laura          | Lima           | Hatchback         | 40000        |

---

#### **Paso 2: Llevar a 2NF**
**Problema**: 
- **Nombre_Cliente** y **Ciudad_Cliente** dependen solo de **ID_Cliente**, no de la clave primaria completa (**ID_Venta**, **Vehiculo_Comprado**).
- **Precio_Total** depende solo de **ID_Venta**, no de **Vehiculo_Comprado**.

**Solución**: 
- Separar los atributos con dependencias parciales en tablas distintas:
  - Una tabla para clientes (**ID_Cliente**, **Nombre_Cliente**, **Ciudad_Cliente**).
  - Una tabla para ventas (**ID_Venta**, **ID_Cliente**, **Precio_Total**).
  - Una tabla para detalles de venta (**ID_Venta**, **Vehiculo_Comprado**).

**Tablas en 2NF:**

**Tabla 1: Clientes**
| ID_Cliente | Nombre_Cliente | Ciudad_Cliente |
|------------|----------------|----------------|
| 201        | Laura          | Lima           |
| 202        | Carlos         | Bogotá         |

**Tabla 2: Ventas**
| ID_Venta | ID_Cliente | Precio_Total |
|----------|------------|--------------|
| 1        | 201        | 45000        |
| 2        | 202        | 30000        |
| 3        | 201        | 40000        |

**Tabla 3: Detalles_Venta**
| ID_Venta | Vehiculo_Comprado |
|----------|-------------------|
| 1        | Sedan             |
| 1        | SUV               |
| 2        | Camioneta         |
| 3        | SUV               |
| 3        | Hatchback         |

---

#### **Paso 3: Llevar a 3NF**
**Problema**: 
- En la tabla **Clientes**, **Ciudad_Cliente** depende de **ID_Cliente**, pero no hay dependencias transitivas adicionales (suponemos que **Ciudad_Cliente** no depende de otro atributo no clave, como un código postal).

**Solución**: 
- Verificar que no haya dependencias transitivas. Las tablas ya cumplen 3NF, ya que:
  - **Clientes**: Todos los atributos (**Nombre_Cliente**, **Ciudad_Cliente**) dependen directamente de **ID_Cliente**.
  - **Ventas**: **Precio_Total** depende de **ID_Venta**, y **ID_Cliente** es una clave foránea.
  - **Detalles_Venta**: **Vehiculo_Comprado** depende de **ID_Venta**.

**Tablas en 3NF**: Las mismas que en 2NF.

**Tabla 1: Clientes**
| ID_Cliente | Nombre_Cliente | Ciudad_Cliente |
|------------|----------------|----------------|
| 201        | Laura          | Lima           |
| 202        | Carlos         | Bogotá         |

**Tabla 2: Ventas**
| ID_Venta | ID_Cliente | Precio_Total |
|----------|------------|--------------|
| 1        | 201        | 45000        |
| 2        | 202        | 30000        |
| 3        | 201        | 40000        |

**Tabla 3: Detalles_Venta**
| ID_Venta | Vehiculo_Comprado |
|----------|-------------------|
| 1        | Sedan             |
| 1        | SUV               |
| 2        | Camioneta         |
| 3        | SUV               |
| 3        | Hatchback         |

---

### **Resultado Final**
La base de datos está ahora en **3NF**, con las siguientes características:
- **Clientes**: Almacena información única de los clientes, eliminando redundancia.
- **Ventas**: Registra cada venta con su precio total y referencia al cliente.
- **Detalles_Venta**: Detalla los vehículos comprados en cada venta, permitiendo múltiples vehículos por venta.
- Se han eliminado redundancias, dependencias parciales y transitivas, optimizando la base de datos para operaciones de inserción, actualización y eliminación.

---

**Tarea**: Intenta resolver el ejercicio paso a paso antes de comparar con la solución proporcionada. Si necesitas ayuda con algún paso o quieres verificar tu solución, ¡pídeme asistencia!