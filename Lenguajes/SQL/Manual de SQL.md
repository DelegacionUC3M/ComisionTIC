# Manual de SQL

SQL es un lenguaje destinado a la manipulación de datos en bases de datos.



## Instrucciones básicas

### Crear una base de datos

Primero deberemos crear un base de datos para almacenar toda la información. Esto lo haremos mediante `CREATE DATABASE`.

```sql
CREATE DATABASE Comision;
```

> Las instrucciones en SQL deben terminar con punto y coma. 
>
> En caso de no ponerlo podemos continuar la instrucción en otra linea.

### Crear tablas

Para crear una tabla deberemos introducir `CREATE TABLE`. Ademas deberemos de introducir las columnas de nuestra tabla al igual que su tipo de datos:

```sql
CREATE TABLE Persons (
    ID int NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int,
    PRIMARY KEY (ID)
);
```

> Es conveniente crear una clave primaria para hacer que los elementos sean únicos e incrementemos la velocidad de las búsquedas.

### Insertar columnas

Para insertar datos utilizaremos `INSERT` junto con la tabla donde introduciremos los datos y el valor de estos:

```sql
INSERT INTO Persons(ID,LastName,FirstName,Age)
VALUES(1,'Apellido','Nombre',20);
```

### Seleccionar datos

No nos sirve de mucha la base de datos si solo podemos introducir datos. Podemos buscar datos mediante la instrucción `SELECT`.

```sql
SELECT FirstName, Age FROM Persons;
```

También podemos obtener todas las columnas de la tabla usando un asterisco:

```sql
SELECT * FROM Persons;
```

#### WHERE

Podemos concretar nuestra búsqueda mediante el uso de `WHERE`, mediante el cual especificaremos las condiciones necesarias:

```sql
SELECT * FROM Persons WHERE Age=24;
```

#### AND/OR

En caso de necesitar mas de una condición, podemos combinarlas mediante `AND` y `OR` para realizar búsquedas tan precisas como necesitemos:

```sql
SELECT * FROM Persons WHERE Age>=24 OR FirstName='Foo';
```

#### In/Between/Like

Tambien podemos utilizar estos comandos con WHERE para refinar aun mas las busquedas:

- **IN** - Compara una columna con un conjunto de valores.

  ```sql
  SELECT * FROM Persons WHERE FirstName IN ('Foo','Bar');
  ```

- **BETWEEN** - El valor de la columna pertenece al rango.

  ```sql
  SELECT * FROM Persons WHERE Age BETWEEN 20 AND 42;
  ```

- **LIKE** - Para buscar un patrón genérico.

  ```sql
  SELECT * FROM Persons WHERE FirstName LIKE '_a%';
  ```

> % representa cero, uno o varios caracteres. _ Representa un solo carácter.