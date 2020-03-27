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
-Crea objetos de la base de datos como tablas,vistas e índices

***ALTER***
-Altera la estructura de una tabla

***DROP***
-Elimina objetos de la base de datos

# Estructura de DDL con create
DDL utiliza ciertos predicados para realizar distintas funciones ,con create se utilizan los siguientes:

DATABASE:Predicado básico para crear una base de datos

TABLE:Sirve para crear una tabla en la base de datos

IF NOT EXITS:Se emplea para determinar si hay o no datos en una lista de valores.

SCHEMA:Mismo uso que 'DATABASE' pero menos rectrictivo

CHARACTER SET:

USER:Sirve para crear usuarios en la base
