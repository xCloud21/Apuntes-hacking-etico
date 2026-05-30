# ATAQUES UNION #

En los casos donde una aplicacion responde con resultados de una query, un atacante puede usar SQLi para recuperar datos de otras tablas en la misma Base de datos. Se puede usar UNION.
##
:information_source: Para realizar este ataque debemos saber cuantas columnas devuelve la query que saca la informacion. Para ello, cuando se esta haciendo este tipo de ataque UNION, hay dos maneras para determinar cuantas columnas
devuelve la query original. Uno de los metodos es a traves de ORDER BY se puede ir incrementando por cada columna hasta que ocurra un error:
``
' ORDER BY 1 '--
' ORDER BY 2 '--
' ORDER BY 3 '--
...
``
Cuando la columna indice especificada se exceda al numero actual de columnas , **la base de datos devolvera un error estilo: INTERNAL SERVER ERROR , The ORDER BY position number 3 is out of range of the number of items in the select list**

###
Otra manera es realizar con **UNION SELECT** . La idea es la misma (poner tantos NULL en las columnas hasta con dar con el numero exacto que devuelve la query de negocio para recuperar la informacion):
`` 'UNION SELECT NULL -- -
'UNION SELECT NULL, NULL -- -
'UNION SELECT NULL, NULL, NULL -- -
...
``
## 
:dart: En este laboratorio, consiste en encontrar informacion sobre la base de datos. Por ejemplo, tipo y version del SW de la BBDD, las tablas y columnas que contienen. Habria que saber las columnas que tiene la tabla para realizar
posteriormente la consulta para recuperar los usuarios de la BBDD.
**EN ORACLE** , cada SELECT tiene que ir acompañado de un FROM. Hay una tabla llamada 'dual' que se puede utilizar para que no de error (es una tabla de sistema).
Para ello, se visualiza en el siguiente ejemplo:

<img width="1555" height="920" alt="image" src="https://github.com/user-attachments/assets/d7594ed3-f04b-430b-8dc9-da4aee478b21" />

