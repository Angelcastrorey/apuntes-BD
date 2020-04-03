# apuntes-BD = FCT
- Estos apuntes se basarán en DML Y DDL que hemos visto en clase
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

***Tipo CHAR,VARCHAR***

Este tipo de datos permite almacenar cadenas de texto fijas(CHAR) o variables (VARCHAR)

El tipo de CHAR permite almacenar cadenas de caracteres de longitud fija entre 1 y 255 caracteres.La longitud de la cadena se debe especificar entre paréntesis en el momento de la declaración (cadena CHAR(25)).

Por otro lado VARCHAR permite almacenar cadenas de caracteres variables hasta 4000 mil caracteres.La declaración de tipo VARCHAR es similar a la de CHAR (cadena VARCHAR(25)).La principal y única diferencia entre estos dos tipos es que el tipo CHAR declara una cadena fija de la longitud especifica mientras que en la declaración de un tipo VARCHAR lo que se especifica es un tamaño máximo,la cadena sólo ocupará el tamaño necesario para almacenar el dato que se contenga(hasta llegar al máximo),la cadena sólo ocupará el tamaño necesario para almacenar el dato que contenga (hasta llegar al máximo). En cualquier caso, no es posible almacenar cadenas de mayor tamaño al especificado en su declaración, puesto que el SGBD truncará el valor almacenándose sólo hasta la longitud establecida.


***TIPO TEXT***

El tipo text permite almacenar cadenas de caracteres de hasta varios GB de longitud y solo se recomienda su uso para textos grandes ya que tiene varias restricciones:

- Solo se puede definir una columna TEXT por tabla
- No se pueden establecer restricciones en columnas de este tipo
- No se pueden utilizar en todas las cláusulas

***TIPOS NUMÉRICOS***

Los tipo más utilizados son BIT,INT,BIGINT,FLOAT,REAL,para la representación de números enteros de menor o mayor tamaño y para números en coma flotante de mayor o menos precisión,también podremos ampliar el rango de un número positivo añadiendo UNSIGNED tras definirlo

```sql
id INT UNSIGNED
```

***TIPOS DE FECHAS***

Los tipos más utilizados para almacenar valores de fechas es 'DATE' o para fechas con hora 'DATETIME'.Por defecto el formato más utilizado es DD/MM/YY

También se puede usar el tipo TIMESTAMP para almacenar una marca de tiempo (fecha y hora).Además permite el uso de la constante CURRENT_TIMESTAMP en la definición de la columna al definirle un valor por defecto al crear esa tabla

***TIPO BOOLEANO***

Permite almacenar valores lógicos verdadero o falso o si o no.Realmente se definde la como del tipo TINYINT,que simplemeente almacena los valores 0 y 1 para indicar los valores lógicos verdadero y falso, también podremos usar los valores true o false o asignar 0 o 1


***RESTRICCIONES***

  Las restricciones se pueden establecer o no ,a las columnas de cada tabla para forzar a que los datos almacenados en ellas cumplan ciertas condiciones para que la información sea la correcta.Por ejemplo ,podemos obligar a un campo donde tenemos el DNI para que tenga una longitud mínima 
  
  Hay que tener en cuenta que por lo general estas restricciones se definen en la línea con la definición del campo pero de forma opcional también pueden ser definidas por separado justo debajo de la definición de todos los campos de la tabla
  
  ***CLAVE PRIMARIA***
  
  Una clave primaria dentro de una tabla es la columna o conjunto de columnas cuyo valor identifica a cada fila.Debe ser única ,no nula y es obligatoria.Como máximo podremos definir una clave primaria por tabla y es recomendable
  
  # PRIMARY KEY
  
  ``` SQL
  DNI VARCHAR(9) PRIMARY KEY
  ```
  
  Y si lo hacemos al final de la definición de las columnas ,quedaría asi:
  ``` SQL
  PRIMARY KEY (DNI)
  ```
  
  Hay que tener en cuenta que a la hora de definir claves primarias compuestas de campos o más ,pues está deberá ser definida forzosamente tras la definición de los campos involucrados:
  ``` sql
  PRIMARY KEY (NOMBRE, APELLIDOS)
  
 # AUTONUMÉRICO

Es especialmente útil en el caso de que las columnas se definan como claves primarias de cada tabla,resulta añadir la restriccion de campo autonumérico,siempre y cuando la columna este de tipo entero haciendo que el gestor de base de datos asigne valores automaticos siempre siendo un valor entero de forma secuencial a medida que se insetar filas en dicha tabla,para definirlo usaremos:

```sql
id INT UNSIGNED PRIMARY KEY AUTO_INCREMENT
```

# CLAVE AJENA

La clave ajena está formada por una o varias columnas que hacen referncia a una clave primaria de otra o de la misma tabla y se pueden definir sin límite.El valor de la columna o columnas que son clave ajena será 'null' o el valor de la clave primaria de la tabla a la que hacen referencia, por ello para definir una clave ajena tenemos que indicar la cláusula referencial con 'REFERENCES' a la tabla que hace referencia.

Para que una clave ajena haga referencia a un campo definido como clave primaria, la columna de la segunda tabla no podrá ser eliminada hasta que no lo haga la columna que le hace referencia.Para evitar eso añadiremos la restricción de clave ajena añadiendo la cláusula on delete o bien on update para el caso de un actualización y indicaremos la operación:

- RESTRICT:Se rechaza la operación de eliminación/actualización

- CASCADE:Realiza la operación y se elimina eb cascada en las filas que hace referencia
- SET NULL:Realiza la operación y fija a NULL el valor al que hace referencia
- NO ACTION:Se rechaza la operación de eliminación/actualización como ocurre con RESTRICT

# EJEMPLOS

```SQL
CURSO VARCHAR(25) REFERENCES CURSOS
CURSO VARCHAR(25) REFERENCES CURSOS ON DELTE CASCADE
```

```SQL
FOREIGN KEY (CURSO) REFERENCES CURSOS
FOREIGN KEY (CURSO) REFERENCES CURSOS ON DELETE CASCADE
```

# CLAVES AJENAS COMPUESTAS

```SQL
FOREIGN KEY (CURSO,AULA) REFERENCES CURSOS
FOREIGN KEY (CURSO,AULA) REFERENCES CURSOS ON DELETE CASCADE
```

# DEFINIR CLAVES AJENAS

- Hay que tener en cuenta varias condiciones:

- La columna deberá ser del mismo tipo y atributos que la columna de la que es clave ajena
- La columna deberá ser un índice
- Si la columna es obligatoria(NOT NULL) no podrá contener 'SET NULL' para on delete y on update

# Ejemplo

```SQL
id_cliente INT UNSIGNED,
INDEX (id_cliente),
FOREIGN KEY(id_cliente) references clientes (id) on delete set null on update set null
```

```sql
create table clientes (
id INT UNSIGNED PRIMARY KEY AUTO_INCREMENT,
);
```

# CAMPOS OBLIGATORIOS

Está restricción obliga a que se tenga que dar un valor obligatoriamente a una columna  y no podrán tener el valor 'NULL' utilizando la palabra 'NOT NULL'

```SQL
APELLIDOS VARCHAR(250) NOT NULL
```

# VALORES POR DEFECTO

Se define el valor que tendrá una columna por defecto si no se especificas el valor y se utiliza 'DEFAULT'

```sql
fecha TIMESTAMP DEFAULT CURRENT_TIMESTAMP
nombre VARCHAR(250) DEFAULT 'SIN NOMBRE'
```

# CONDICIONES

```SQL
NOMBRE VARCHAR(250) CHECK (NOMBRE = UPPER(NOMBRE))
EDAD INT CHECK (EDAD > 0)
CURSO INT CHECK (CURSO BETWEEN 1 AND 2)
```

Podemos definir las condiciones también:

```sql
curso ENUM ('0','2','3'),
horario ENUM ('HOY','MAÑANA','NOCHE')
```

# VALORES ÚNICOS

La restricción 'UNIQUE' evits los valores duplicados de una columna y a diferencia que PRIMARY KEY , unique se puede aplicar a varias columnas de la misma tabla y admite el valor NULL , si una columna lleva UNIQUE solo 1 de sus filas podrán llevar NULL

```sql
email VARCHAR(100) UNIQUE
```

# ÍNDICES

Se utilizan para obetener datos de las tablas de forma rápida asociando el valor de una columna sobre la que definimos el índice con su posición en la tabla

```sql
INDEX autor_index (autor)
```

# USUARIOS Y PRIVILEGIOS

```SQL
CREATE USER 'DESARROLLADOR' IDENTIDIED BY 'MICONTRASEÑA';
GRANT ALL PRIVILEGES ON biblioteca.* TO DESARROLLADOR;
```

# INSTALACION SISTEMA GESTOR DE BASE DE DATOS

- Lo primero será en google buscar el archivo a descargar para poder instalar el MYSQL

![](https://www.mediafire.com/convkey/4def/vad5je94jenwwfyzg.jpg)

- Cogemos el pack de desarrollador para poder realizar más acciones y le daremos a siguiente para proseguir con la instalación

- Después mirará los requerimientos que nos hacen falta pero como no nos hacen falta las herramientas gráficas le daremos a siguiente

![](http://www.mediafire.com/convkey/8c36/t2b11rnxlw3106qzg.jpg)

- Después comenzará a instalar lo necesario para que funcione

![](http://www.mediafire.com/convkey/30b1/1od632ychct7ixkzg.jpg)

- Una vez se descarguen todos estos paquetes ,después se instalarán

![](http://www.mediafire.com/convkey/aaba/quztcqzsast6r1pzg.jpg)

- Luego nos preguntará que queremos y seleccionaremos MYSQL

![](http://www.mediafire.com/convkey/4f26/dwpbqqouox0fjcozg.jpg)

- También nos pedirá que le digamos el tipo y el tcp

![](http://www.mediafire.com/convkey/5767/oyrmozdyuhgk2j3zg.jpg)

- Para acceder tendremos que crear un usuario root y nos mandará introducir una contraseña para ese usuario

![](http://www.mediafire.com/convkey/f37a/qfu6zc0wzqkjaz2zg.jpg)

- También tendremos que configurar el servicio para windows y dejaremos estas opciones por defecto

![](http://www.mediafire.com/convkey/a3a5/809wia9dya7pafnzg.jpg)

- Luego empieza la configuración de todo que es automática

![](http://www.mediafire.com/convkey/53a7/ozeaucd69brqrvmzg.jpg)

- Una vez terminada la configuración ,nos saltará la configuración del router para MYSQL y yo en mi caso deje todo por defecto

![](http://www.mediafire.com/convkey/850b/m4c0gsgbygsmspmzg.jpg)

- Ahora tendremos que conectar nuestro servidor local de MYSQL

![](http://www.mediafire.com/convkey/7575/x1cy26lscl79f4nzg.jpg)

- Una vez conectado el servidor nos saltará una ventana parecida a la siguiente

![](http://www.mediafire.com/convkey/0fb9/vwp38fs74viyx33zg.jpg)

- Cuando se conecta con el servidor aplicará una configuración para que funcione

![](http://www.mediafire.com/convkey/0fb9/vwp38fs74viyx33zg.jpg)

- Una vez terminada la instalación nos saldrá la siguiente ventana y le daremos a finalizar

![](http://www.mediafire.com/convkey/4520/3v7t4xjgn222ilhzg.jpg)

- Una vez instalado todo podremos usar la línea de comandos para configurar nuestro servidor en MYSQL y por ejemplo con el comando 'status' nos enseñara el estado de todo el servidor

![](http://www.mediafire.com/convkey/1608/m99mmmd4twblhymzg.jpg)

- También podemos mirar los comandos que se pueden usar como guía utilizando el comando 'help' y veremos todas las opciones que tenemos

![](http://www.mediafire.com/convkey/6581/ul4hx8l3gryujruzg.jpg)

- Ahora creare una base de datos  y empezaré a usarla creando tablas y sus valores para poder realizar consultas

![](http://www.mediafire.com/convkey/aedf/mr7n9z7ur92xz7kzg.jpg)

