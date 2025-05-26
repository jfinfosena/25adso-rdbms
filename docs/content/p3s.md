# **Actividad: Análisis de Ventas de Tienda Electrónica**

**Enunciado (recordatorio):**  
Has recibido el encargo de analizar las ventas de una tienda de productos electrónicos utilizando una base de datos SQL. La tabla `ventas_tienda` contiene información sobre las ventas realizadas, incluyendo el producto vendido, su categoría, precio unitario, cantidad vendida, fecha de venta, vendedor y región. Los siguientes ejercicios requieren escribir consultas SQL para extraer información específica usando los operadores **WHERE**, **AND**, **OR**, **LIKE**, **BETWEEN**, las funciones de agregación **COUNT**, **SUM**, **AVG**, **MAX**, **MIN**, y las cláusulas **ORDER BY**, **GROUP BY**, **HAVING**.

---

```sql
-- Ejercicio 1: Filtrar ventas de una categoría específica
-- Selecciona todas las columnas de las ventas de la categoría 'Teléfonos'.
SELECT *
FROM ventas_tienda
WHERE categoria = 'Teléfonos';

-- Ejercicio 2: Ventas con precio alto
-- Muestra el producto, precio unitario y vendedor de las ventas con un precio unitario mayor a 1000.
SELECT producto, precio_unitario, vendedor
FROM ventas_tienda
WHERE precio_unitario > 1000;

-- Ejercicio 3: Ventas en un rango de fechas
-- Encuentra todas las ventas realizadas entre el 1 de enero de 2024 y el 31 de diciembre de 2024.
SELECT *
FROM ventas_tienda
WHERE fecha_venta BETWEEN '2024-01-01' AND '2024-12-31';

-- Ejercicio 4: Ventas por vendedor específico
-- Selecciona el producto, cantidad vendida y fecha de venta de todas las ventas realizadas por 'Ana López'.
SELECT producto, cantidad_vendida, fecha_venta
FROM ventas_tienda
WHERE vendedor = 'Ana López';

-- Ejercicio 5: Productos con nombre específico
-- Muestra las ventas de productos cuyo nombre comienza con 'Smartphone'.
SELECT *
FROM ventas_tienda
WHERE producto LIKE 'Smartphone%';

-- Ejercicio 6: Ventas en regiones específicas
-- Selecciona todas las ventas realizadas en las regiones 'Norte' o 'Sur'.
SELECT *
FROM ventas_tienda
WHERE region = 'Norte' OR region = 'Sur';

-- Ejercicio 7: Ventas con múltiples condiciones
-- Encuentra las ventas de la categoría 'Laptops' con un precio unitario mayor a 1200 y cantidad vendida mayor a 1.
SELECT *
FROM ventas_tienda
WHERE categoria = 'Laptops' AND precio_unitario > 1200 AND cantidad_vendida > 1;

-- Ejercicio 8: Ventas recientes
-- Muestra las ventas realizadas después del 1 de julio de 2024, ordenadas por fecha descendente.
SELECT *
FROM ventas_tienda
WHERE fecha_venta > '2024-07-01'
ORDER BY fecha_venta DESC;

-- Ejercicio 9: Total de ventas por categoría
-- Calcula el número total de ventas (usando COUNT) por categoría.
SELECT categoria, COUNT(*) AS total_ventas
FROM ventas_tienda
GROUP BY categoria;

-- Ejercicio 10: Suma de ingresos por región
-- Calcula la suma del ingreso total (precio_unitario * cantidad_vendida) por región.
SELECT region, SUM(precio_unitario * cantidad_vendida) AS ingreso_total
FROM ventas_tienda
GROUP BY region;

-- Ejercicio 11: Precio promedio por categoría
-- Encuentra el precio unitario promedio de los productos vendidos por categoría.
SELECT categoria, AVG(precio_unitario) AS precio_promedio
FROM ventas_tienda
GROUP BY categoria;

-- Ejercicio 12: Producto más caro
-- Selecciona el producto con el precio unitario más alto.
SELECT producto, precio_unitario
FROM ventas_tienda
WHERE precio_unitario = (SELECT MAX(precio_unitario) FROM ventas_tienda);

-- Ejercicio 13: Producto más barato
-- Selecciona el producto con el precio unitario más bajo.
SELECT producto, precio_unitario
FROM ventas_tienda
WHERE precio_unitario = (SELECT MIN(precio_unitario) FROM ventas_tienda);

-- Ejercicio 14: Ventas por vendedor con filtro
-- Muestra el número de ventas por vendedor, pero solo para aquellos con más de 5 ventas.
SELECT vendedor, COUNT(*) AS total_ventas
FROM ventas_tienda
GROUP BY vendedor
HAVING COUNT(*) > 5;

-- Ejercicio 15: Ventas de auriculares
-- Encuentra todas las ventas de productos cuyo nombre contiene 'Auriculares'.
SELECT *
FROM ventas_tienda
WHERE producto LIKE '%Auriculares%';

-- Ejercicio 16: Ventas con cantidad alta
-- Selecciona las ventas con una cantidad vendida mayor o igual a 3.
SELECT *
FROM ventas_tienda
WHERE cantidad_vendida >= 3;

-- Ejercicio 17: Ingresos por vendedor
-- Calcula el ingreso total (precio_unitario * cantidad_vendida) por vendedor.
SELECT vendedor, SUM(precio_unitario * cantidad_vendida) AS ingreso_total
FROM ventas_tienda
GROUP BY vendedor;

-- Ejercicio 18: Ventas ordenadas por precio
-- Muestra el producto, precio unitario y categoría, ordenados por precio unitario descendente.
SELECT producto, precio_unitario, categoria
FROM ventas_tienda
ORDER BY precio_unitario DESC;

-- Ejercicio 19: Ventas por región y categoría
-- Agrupa las ventas por región y categoría, mostrando el número de ventas para cada combinación.
SELECT region, categoria, COUNT(*) AS total_ventas
FROM ventas_tienda
GROUP BY region, categoria;

-- Ejercicio 20: Ventas en 2023
-- Encuentra todas las ventas realizadas en el año 2023.
SELECT *
FROM ventas_tienda
WHERE YEAR(fecha_venta) = 2023;

-- Ejercicio 21: Vendedores con ingresos altos
-- Muestra los vendedores con un ingreso total (precio_unitario * cantidad_vendida) mayor a 2000.
SELECT vendedor, SUM(precio_unitario * cantidad_vendida) AS ingreso_total
FROM ventas_tienda
GROUP BY vendedor
HAVING SUM(precio_unitario * cantidad_vendida) > 2000;

-- Ejercicio 22: Productos con nombre largo
-- Selecciona los productos cuyo nombre tiene más de 20 caracteres.
SELECT producto
FROM ventas_tienda
WHERE LENGTH(producto) > 20;

-- Ejercicio 23: Ventas por mes
-- Agrupa las ventas por mes y cuenta el número de ventas por mes.
SELECT EXTRACT(MONTH FROM fecha_venta) AS mes, EXTRACT(YEAR FROM fecha_venta) AS año, COUNT(*) AS total_ventas
FROM ventas_tienda
GROUP BY EXTRACT(YEAR FROM fecha_venta), EXTRACT(MONTH FROM fecha_venta);

-- Ejercicio 24: Ventas de tablets caras
-- Encuentra las ventas de la categoría 'Tablets' con un precio unitario mayor a 500.
SELECT *
FROM ventas_tienda
WHERE categoria = 'Tablets' AND precio_unitario > 500;

-- Ejercicio 25: Ventas con bajo inventario
-- Selecciona las ventas con una cantidad vendida menor a 2.
SELECT *
FROM ventas_tienda
WHERE cantidad_vendida < 2;

-- Ejercicio 26: Máximo ingreso por venta
-- Calcula el ingreso máximo (precio_unitario * cantidad_vendida) de una sola venta.
SELECT producto, (precio_unitario * cantidad_vendida) AS ingreso_venta
FROM ventas_tienda
WHERE (precio_unitario * cantidad_vendida) = (SELECT MAX(precio_unitario * cantidad_vendida) FROM ventas_tienda);

-- Ejercicio 27: Promedio de cantidad vendida por región
-- Calcula la cantidad promedio vendida por región.
SELECT region, AVG(cantidad_vendida) AS cantidad_promedio
FROM ventas_tienda
GROUP BY region;

-- Ejercicio 28: Ventas ordenadas por vendedor y fecha
-- Muestra todas las ventas, ordenadas primero por vendedor (alfabéticamente) y luego por fecha de venta (ascendente).
SELECT *
FROM ventas_tienda
ORDER BY vendedor ASC, fecha_venta ASC;

-- Ejercicio 29: Ventas por categoría con filtro
-- Agrupa las ventas por categoría y muestra solo aquellas categorías con un ingreso total mayor a 3000.
SELECT categoria, SUM(precio_unitario * cantidad_vendida) AS ingreso_total
FROM ventas_tienda
GROUP BY categoria
HAVING SUM(precio_unitario * cantidad_vendida) > 3000;

-- Ejercicio 30: Consulta combinada
-- Encuentra los vendedores que han vendido productos de la categoría 'Teléfonos' en 2024, con un ingreso total mayor a 1500, ordenados por ingreso descendente.
SELECT vendedor, SUM(precio_unitario * cantidad_vendida) AS ingreso_total
FROM ventas_tienda
WHERE categoria = 'Teléfonos' AND YEAR(fecha_venta) = 2024
GROUP BY vendedor
HAVING SUM(precio_unitario * cantidad_vendida) > 1500
ORDER BY ingreso_total DESC;
```

---

### **Explicación de las Soluciones**

1. **Ejercicio 1**: Filtra las ventas por la categoría 'Teléfonos' usando **WHERE**.
2. **Ejercicio 2**: Usa **WHERE** para seleccionar ventas con precio unitario mayor a 1000, mostrando solo las columnas solicitadas.
3. **Ejercicio 3**: Utiliza **BETWEEN** para filtrar ventas en 2024.
4. **Ejercicio 4**: Filtra las ventas de 'Ana López' con **WHERE** y selecciona las columnas solicitadas.
5. **Ejercicio 5**: Usa **LIKE** con el patrón 'Smartphone%' para encontrar productos que comienzan con 'Smartphone'.
6. **Ejercicio 6**: Combina dos condiciones con **OR** para filtrar ventas de las regiones 'Norte' o 'Sur'.
7. **Ejercicio 7**: Combina tres condiciones con **AND** para filtrar ventas de 'Laptops' con precio > 1200 y cantidad > 1.
8. **Ejercicio 8**: Filtra ventas posteriores a julio de 2024 con **WHERE** y las ordena con **ORDER BY DESC**.
9. **Ejercicio 9**: Usa **GROUP BY** y **COUNT** para contar ventas por categoría.
10. **Ejercicio 10**: Calcula el ingreso total (`precio_unitario * cantidad_vendida`) por región con **SUM** y **GROUP BY**.
11. **Ejercicio 11**: Calcula el promedio de `precio_unitario` por categoría con **AVG** y **GROUP BY**.
12. **Ejercicio 12**: Usa una subconsulta con **MAX** para encontrar el producto más caro.
13. **Ejercicio 13**: Usa una subconsulta con **MIN** para encontrar el producto más barato.
14. **Ejercicio 14**: Usa **GROUP BY** y **HAVING** para mostrar vendedores con más de 5 ventas.
15. **Ejercicio 15**: Usa **LIKE** con '%Auriculares%' para encontrar ventas de auriculares.
16. **Ejercicio 16**: Filtra ventas con cantidad vendida ≥ 3 usando **WHERE**.
17. **Ejercicio 17**: Calcula el ingreso total por vendedor con **SUM** y **GROUP BY**.
18. **Ejercicio 18**: Ordena las ventas por precio unitario descendente con **ORDER BY**.
19. **Ejercicio 19**: Agrupa por región y categoría con **GROUP BY** y cuenta las ventas con **COUNT**.
20. **Ejercicio 20**: Usa la función `YEAR` (o `EXTRACT` en algunos SGBD) para filtrar ventas de 2023.
21. **Ejercicio 21**: Usa **GROUP BY** y **HAVING** para mostrar vendedores con ingresos > 2000.
22. **Ejercicio 22**: Usa la función `LENGTH` para filtrar productos con nombres de más de 20 caracteres.
23. **Ejercicio 23**: Agrupa por año y mes con **EXTRACT** y **GROUP BY** para contar ventas por mes.
24. **Ejercicio 24**: Combina **WHERE** y **AND** para filtrar tablets con precio > 500.
25. **Ejercicio 25**: Filtra ventas con cantidad < 2 usando **WHERE**.
26. **Ejercicio 26**: Usa una subconsulta con **MAX** para encontrar la venta con mayor ingreso.
27. **Ejercicio 27**: Calcula el promedio de `cantidad_vendida` por región con **AVG** y **GROUP BY**.
28. **Ejercicio 28**: Usa **ORDER BY** con dos criterios (vendedor y fecha) para ordenar las ventas.
29. **Ejercicio 29**: Usa **GROUP BY** y **HAVING** para mostrar categorías con ingresos > 3000.
30. **Ejercicio 30**: Combina **WHERE**, **GROUP BY**, **HAVING**, y **ORDER BY** para una consulta compleja que filtra por categoría, año, e ingreso.

---
