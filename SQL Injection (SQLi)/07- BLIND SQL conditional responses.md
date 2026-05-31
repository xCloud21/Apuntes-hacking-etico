A continuacion, para aplicar los conceptos teoricos de una SQL Blind. Se va a practicar para el caso de una respuesta condicional.
La aplicacion esta exponiendo un mensaje de 'Welcome back'. Dicho mensaje se devuelve si la query resultante de dumpear los datos para mostrar la informacion es correcta por el numero de columnas.
Si no devuelve el mensaje, significa que no estamos ante el numero correcto de columnas.
#
:dart: **Utilizamos burpsuite** para mandar la informacion al Repeater y a partir de ahi manipular el request para averiguar el numero de columnas devuelto en la query resultante.
Lo primero que llama la atencion es la Cookie 'trackingId'. Esto se puede utilizar como punto para manipular y dumpear la informacion.
<img width="880" height="633" alt="image" src="https://github.com/user-attachments/assets/382bcd4a-8a18-4fc6-b07e-3de3f382fd6d" />

* Utilizando payloads para respuestas condicionadas, se puede concatenar la condicion ' AND '1'='1 y como siempre 1=1 obtendremos el mensaje de bienvenida. Lo que quiere decir que es vulnerable a este tipo de ataque.
Si ponemos en la condicion '2'='1 , no devolvera el mensaje de bienvenida porque ambos numeros no son iguales. **Hay que jugar con esta condicion** para intentar sacar informacion de usuarios contra la
tabla 'users' y sacar la contraseña mediante un **cluster bomb** en burp suite.

<img width="1597" height="632" alt="image" src="https://github.com/user-attachments/assets/7c34d0fc-2ae8-4c39-97bd-e27591da4087" />

