# apuntes-BD = FCT

# Restricciones de unidad:

[CONSTRAINT <nombre-de-restriccion>]
  
    UNIQUE (palabra clave para la restricción de la unidad)
    |
    |-/Es igual que la restricción de la primary key
    Unique se emplea para declarar claves candidatas */
    
      [CONSTRAINT] Persona_dni_unique
        UNIQUE    DNI ,dni char(9) not null,
                  CONSTRAINT FK    
                  
   [CONSTRAINT <nombre-de-restricción>]
   
   CHECK (atributoA IN ('VALOR1',...,'valorN'))
   
   [[NOT]DEFERRABLE]
   
   [INITIALLY INMEDIATE|DEFERRED]
   
   CONSTRAINT CHECK_OBXECTIVO_POSITIVO
   
   CHECK OBXECTIVO >0
   
   CHECK (<PREDICADO(ATRIBUTO)>)
   
   Constraint check_soldo_maximo
   
   check soldo >= (
   
   SELECT SOLDO
   
   FROM EMPLEADO
   
   WHERE DEPT = 'A'
   
   );
   DEFERRABLE
   INITIALLY DEFERRED;
   
   
   # DROP TABLE
   [IF EXISTS]<NOME-DA-TÁBOA>
   
   [CASCADE |RESTRICT];
   
   #DROP SCHEMA
   [IF EXISTS]<NOME-DA-BASE-DE-DATOS>
  
  [CASCADE] [RESTRICT] --> PROTEXE SE A BASE DE DATOS NON ESTA BALEIRA
  --> BORRA AÍNDA QUE ESTEA CHEA
  
  #ALTER TABLE
  
  COLUMNAS | RESTRICCIÓN
  
  ENGADIR|ELIMINAR    || ENGADIR|ELIMINAR
  
  ADD|DROP            || ADD|DROP
  
  ADD [COLLUMN]<ATRIBUTO1><DOMINIO>[NOT NULL] [DEFAULT<X>]
  
  DROP [COLUMN]<ATRIBUTO1>[CASCADE|RESTRICT]
