En este laboratorio se encuentra expuesta a una SQLi en el filtro de categorías de productos. Los resultados de la consulta se devuelven en la respuesta de la aplicación, por lo que se puede utilizar
un ataque UNION para recuperar datos de otras tablas. Para resolver el ejercicio, se realiza un ataque de inyección SQL UNION que recupere todos los nombres de usuario y contraseñas, y utiliza esa
información para iniciar sesión como usuario administrador. 

#
:dart **RESOLUCION** : en esta ocasion estamos ante que la query resultante de busqueda devuelve dos columnas de MySQL. Una devuelve datos numericos y la otra devuelve una cadena (string). Por lo tanto,
habria que **dumpear (volvar) en una sola columna toda la informacion**. 

* Informacion sacada del numero de columnas y tipos de datos
<img width="1370" height="827" alt="image" src="https://github.com/user-attachments/assets/5a32c435-a329-4c67-b044-3e0da613b853" />

* Mismo caso anterior, obtener toda la informacion de las tablas de la bbdd. Se observa que hay una tabla 'users'. Dumpear el nombre de las columnas con el mismo procedimiento: 
<img width="1357" height="872" alt="image" src="https://github.com/user-attachments/assets/b6bf80d2-87b2-49f3-ab4b-a8921257c45a" />


* Concatenar en una sola columna para dumpear el usuario y contraseña de la tabla 'users'. Para ello, se puede emplear '||' :
<img width="1305" height="899" alt="image" src="https://github.com/user-attachments/assets/0ef3a2d8-e2fd-4cac-ba65-ab7912ac4978" />

* Resuelto el laboratorio una vez hecho el login en la aplicacion con el usuario adminitrador
  
