# Mini Tutorial de SQLite con DBeaver

## Instalación de DBeaver
Para comenzar a trabajar con bases de datos en SQLite, te recomendamos instalar DBeaver, un cliente de base de datos universal.

### Pasos de instalación:
1. Descarga DBeaver desde [aquí](https://dbeaver.io/download/).
2. Instala el programa siguiendo las instrucciones del instalador.
3. Abre DBeaver y crea una nueva conexión seleccionando **SQLite**.
4. En la configuración de la conexión, elige el archivo `database.db` generado con el script anterior.
5. Conéctate y empieza a explorar la base de datos.

---

## Consultas Básicas en SQLite
### 1. Ver todas las tablas en la base de datos
```sql
SELECT name FROM sqlite_master WHERE type='table';
```

### 2. Mostrar todos los clientes
```sql
SELECT * FROM Cliente;
```

### 3. Mostrar los primeros 10 productos
```sql
SELECT * FROM Producto LIMIT 10;
```

### 4. Obtener las órdenes de un cliente específico
```sql
SELECT * FROM Orden WHERE cliente_id = 1;
```

### 5. Obtener detalles de una orden específica
```sql
SELECT * FROM DetalleOrden WHERE orden_id = 1;
```

### 6. Listar productos y su categoría
```sql
SELECT Producto.nombre, Categoria.nombre AS categoria
FROM Producto
JOIN Categoria ON Producto.categoria_id = Categoria.id;
```

### 7. Obtener el total gastado por cada cliente
```sql
SELECT Cliente.nombre, SUM(Orden.total) AS total_gastado
FROM Cliente
JOIN Orden ON Cliente.id = Orden.cliente_id
GROUP BY Cliente.id;
```

### 8. Obtener las órdenes con más de 3 productos
```sql
SELECT orden_id, COUNT(*) AS cantidad_productos
FROM DetalleOrden
GROUP BY orden_id
HAVING cantidad_productos > 3;
```

---

## Conclusión
Este mini tutorial te ayudará a explorar SQLite con DBeaver, ejecutar consultas y entender la estructura de la base de datos. ¡Sigue practicando y experimentando con más consultas! 🚀
