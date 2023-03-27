# Procedimiento almacenados en PostgreSQL

Un procedimiento almacenado es un conjunto de instrucciones SQL que se pueden almacenar en la base de datos y ejecutar posteriormente.

# ¿Cómo llamar a un procedimiento almacenado en PostgreSQL?

Podemos llamarlo tal que así:

      CALL ejemplo(3, ?);

Para llamar a un procedimiento almacenado en PostgreSQL, se utiliza el comando CALL. Pero antes debemos saber cómo funciona el paso de parámetros en Postgresql.

# Uso de parámetros en pl/pgsql

Los modos en los que utilizamos los parámetros determinan el comportamiento de los parámetros. PL/pgSQL admite tres modos de parámetros: in, out y inout. Un parámetro toma el in por defecto si no lo especifica explícitamente. 

## El modo in se utiliza para pasar un valor a la función.

## El modo out se utiliza para devolver un valor desde una función.


    CREATE OR REPLACE PROCEDURE ejemploinout(IN numero INT, OUT resultado INT)
    LANGUAGE plpgsql
    AS $$
    BEGIN
        resultado := numero * 2;
    END;
    $$;

    CALL mi_procedimiento(8, ?);   --OJO que en datagrip sale un prompt
    
# Un paso más allá INOUT

Las variables INOUT son valores que se pasan al procedimiento cuando se llama y que también pueden ser modificados por el procedimiento y devueltos como resultado. Aquí tienes un ejemplo sencillo de un procedimiento que utiliza una variable INOUT:

      CREATE OR REPLACE PROCEDURE masalla(INOUT numero INT)
      LANGUAGE plpgsql
      AS $$
      BEGIN
          numero := numero * 2;
      END;
      $$;
      
Podemos verlo así:

      CALL masalla(3);
