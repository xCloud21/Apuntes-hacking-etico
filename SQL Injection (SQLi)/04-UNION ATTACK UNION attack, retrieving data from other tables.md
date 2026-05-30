En este laboratorio se practicara la inyección SQL en el filtro de categorías de productos. Los resultados de la consulta se devuelven en la respuesta de la aplicación, por lo que puedes utilizar
un ataque UNION para recuperar datos de otras tablas. Para llevar a cabo este tipo de ataque.

La base de datos contiene otra tabla llamada «users», con columnas denominadas «username» y «password».

Para resolver el laboratorio, se realiza un ataque de inyección SQL UNION que recupere todos los nombres de usuario y contraseñas, y utiliza la información para iniciar sesión como usuario administrador. 

##
:dart: **RESOLUCION** :
###
Para ello, hay que seguir la misma filosofia que en apartados anteriores. Primeramente, hay que saber si es vulnerable a SQLi. Segundo, habria que identificar ante que base de datos estamos (oracle, SQL, postgres,etc).
Por ultimo, averiguar el numero de columnas que devuelva la query de salida de datos para obtener informacion sensible de la BBDD.
###
En este caso, se trata de un Microsoft SQL y estamos ante dos columnas que devuelven string (cadena - varchar). 
 * Informacion de las tablas de la bbdd:
<img width="1373" height="939" alt="image" src="https://github.com/user-attachments/assets/99e71e41-e67c-4cdb-b15b-54e6e339bad7" />

 * Usuarios y contraseñas expuestas de la tabla 'users'
<img width="1378" height="924" alt="image" src="https://github.com/user-attachments/assets/f47170fd-aebb-44de-95eb-feb4f6e4da8e" />

 * Copiamos la contraseña de 'administrador' y estamos dentro del sistema
<img width="1373" height="797" alt="image" src="https://github.com/user-attachments/assets/9c1a10af-2490-453f-b7db-98b1b0fad7f6" />

   

