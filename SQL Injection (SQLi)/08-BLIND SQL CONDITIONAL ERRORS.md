Este ejercicio contiene una vulnerabilidad de inyección SQL ciega. La aplicación utiliza una cookie de seguimiento con fines analíticos y realiza una consulta SQL que incluye el valor de la cookie enviada.

Los resultados de la consulta SQL no se muestran, y la aplicación **no cambia su comportamiento en función de si la consulta devuelve alguna fila**. Si la consulta SQL provoca un error, la aplicación muestra un
mensaje de error personalizado.

Lo que se pretende realizar en este laboratorio es practicar el Blind sql mediante condiciones de error. Es decir, en caso de que exista un usuario llamado 'administrator' y la contraseña sea mayor o igual a 20
caracteres, se provoca una division entre 0 para afirmar que la contraseña sea igual a 20. En caso de fuera igual o menor , la aplicacion se mostraria correctamente.
Para ello, se hace la siguiente condicion (ORACLE): `` xyz' AND (SELECT '' WHEN (1=1) THEN TO_CHAR(1/0) ELSE '' END FROM users WHERE username='administrator' and LENGTH(password)>=20 ``


