# apuntes-BD = FCT
1 Sublenguajes de SQL
- DDL
- DML

DDL (Data Definition Language): Definición de datos. - Que datos queremos guardar: tablas y atributos. - Integridad de los datos: claves primárias y foráneas , restricciones de usuario.

DML (Data Manipulation Language): Acceso y Actualización de los datos. - Consultas - Inserciones - Actualizaciones - Eliminaciones

```
2. [Clausulas](#Clausula)
```
2.1 SELECT: Atributos que se desean mostrar.

2.2 FROM: Tablas necesarias para obtener la información que se quiere mostrar en SELECT.

2.3 WHERE: Condiciones que han de cumplir los registros que se mostrarán

2.4 GROUP BY: Atributos para los que se ha de agrupar el resultado de la consulta.

2.5 HAVING: Condiciones que han de cumplir los grupos que se muestren.

2.6 ORDER BY: Atributos que determinan el orden de mostrado de los datos.

# Que es SQL
Es un lenguaje declarativo que se utiliza en programación para administrar y recuperar información de un sistema de gestión de bases de datos relacionales y además de ellos podemos crear consultas,bases de datos ,crear tablas y borrarlas...

## Lenguaje de definicion de datos
***CREATE***
- Crea objetos de la base de datos como tablas,vistas e índices

***ALTER***
- Altera la estructura de una tabla

***DROP***
- Elimina objetos de la base de datos

# Reglas de Nomenclatura
Los nombres de tablas y columnas:
Deben empezar por una letra
Deben tener entre 1 y 30 caracteres
No deben duplicar el nombre de otro objeto del mismo usuario


# Estructura de DDL con create
DDL utiliza ciertos predicados para realizar distintas funciones ,con create se utilizan los siguientes:

DATABASE:Predicado básico para crear una base de datos

TABLE:Sirve para crear una tabla en la base de datos

IF NOT EXITS:Se emplea para determinar si hay o no datos en una lista de valores.

SCHEMA:Mismo uso que 'DATABASE' pero menos rectrictivo

CHARACTER SET:Sirve para añadir carácteres a la tabla

USER:Sirve para crear usuarios en la base

DEFAULT:vuelve todo al valor por defecto

# Crear un objeto:CREATE
Es la sentencia utilizada para la creación de un objeto(base de datos,tabla,vista,usuario,procedimiendo)en una base de datos

- La sintaxis para la creación de una tabla es la siguiente

``` sql
create table [if not exists] <nombre_tabla>
(
  <nombre_columna1> <tipo_dato> <restricciones>
  <nombre_columna2> <tipo_dato> <restricciones>
  .............................
)
```

- Para crear una base de datos 
```sql
CREATE DATABASE [IF NOT EXISTS] <nombre_base_de_datos>
```

# Eliminar un objeto :DROP
- Es la sentencia utilizada para eliminar objetos(tabla,usuario,vista,procedimiento)en la base de datos
- La sentencia para eliminar una tabla
```sql
DROP table [if exists] <nombre_tabla>
```
- Para eliminar una base de datos
```sql
DROP DATABASE [IF EXISTS] <nombre_base_de_datos>
```

# Modificar un objeto:ALTER
Es la sentencia utilizada para modificar tablas usuarios ,vista, procedimientos de una base de datos
- La sintaxis para modificar la tabla es:
```sql
ALTER TABLE <nombre_tabla>
  [ADD <Definicion_columna> ]
  [CHANGE <nombre_columna> <definicion_columna>]
  [DROP COLUMN <nombre_columna>]
  [ADD CONSTRAINT <restriccion>]
```
# Conceder privilegios sobre un objeto:GRANT
Permite conceder privilegios sobre un objeto a un usuario de la base de datos

```sql
GRANT <privilegio>
ON <objeto>
TO <usuario>
[WITH GRANT OPTIONS]
```

# Revocar privilegios sobre un objeto:revoke
Permite eliminar un privilegio sobre un objeto a un usuario

``` sql
REVOKE <privilegio>
ON <objeto>
from <usuario>
```
# Conectar con una base de datos
Permite realizar la conexión con una base de datos de MySQL

```sql
USE <nombre_base_de_datos>
```
# Comentarios en SQL
Existe la posibilidad de añadir comentarios al código del lenguaje SQL según la siguiente sintaxis:
``` sql
--Esto es un comentario y MySQL no lo ejecuta
/* Esto también es un comentario y tampoco se ejecuta */
```
# Tipos de datos
Cadenas de caracteres

Tipo CHAR,VARCHAR

Este tipo de datos permite almacenar cadenas de texto fijas(CHAR) o variables (VARCHAR)

El tipo de CHAR permite almacenar cadenas de caracteres de longitud fija entre 1 y 255 caracteres.La longitud de la cadena se debe especificar entre paréntesis en el momento de la declaración (cadena CHAR(25)).

Por otro lado VARCHAR permite almacenar cadenas de caracteres variables hasta 4000 mil caracteres.La declaración de tipo VARCHAR es similar a la de CHAR (cadena VARCHAR(25)).La principal y única diferencia entre estos dos tipos es que el tipo CHAR declara una cadena fija de la longitud especifica mientras que en la declaración de un tipo VARCHAR lo que se especifica es un tamaño máximo,la cadena sólo ocupará el tamaño necesario para almacenar el dato que se contenga(hasta llegar al máximo),la cadena sólo ocupará el tamaño necesario para almacenar el dato que contenga (hasta llegar al máximo). En cualquier caso, no es posible almacenar cadenas de mayor tamaño al especificado en su declaración, puesto que el SGBD truncará el valor almacenándose sólo hasta la longitud establecida.


***TIPO TEXT***

El tipo text permite almacenar cadenas de caracteres de hasta varios GB de longitud y solo se recomienda su uso para textos grandes ya que tiene varias restricciones:

- Solo se puede definir una columna TEXT por tabla
- No se pueden establecer restricciones en columnas de este tipo
- No se pueden utilizar en todas las cláusulas
