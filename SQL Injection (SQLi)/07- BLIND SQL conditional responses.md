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

* Para ello, primeramente hay que intentar averiguar la longitud de la password para realizar dicho ataque e ir rotando posiciones hasta averiguar cada caracter por cada posicion. En este caso, la longitud **es de 20 caracteres** como podemos ver por la imagen (AND (SELECT 'a' FROM users WHERE username='administrator' AND LENGTH(password)>=20)='a)
 <img width="1571" height="587" alt="image" src="https://github.com/user-attachments/assets/d514bc14-2b1c-4ff9-a652-64f147c24b6d" />

* Siguiente paso, ir averiguando para cada posicion de la contraseña la combinacion de letras y numeros. Para ello, mediante la funcion SUBSTRING() se mete la columna que se va a fuzzear, en este caso 'password' y se iran probando todas las combinaciones. Se lleva este request al Intruder para realizar el ataque y se va a ir rotando en la variable ultima de la consulta cuando se realiza la comparacion contra el caracter. Si devuelve el mensaje significara que se ha averiguado el caracter.
La configuracion del cluster bomb consiste en ir rotando la posicion desde la 1-20 de la funcion SUBSTRING para ir probando combinaciones alfanumericas. El segundo argumento rotativo consiste en la igualacion del select para probar de la a-z y de 0-9. Si cambia la longitud de la respuesta, significa que estamos ante el caracter correcto. Ademas, tambien hay que incluir en la parte de GREP MATCH que el mensaje de Welcome back quiere decir una respuesta exitosa.

Segundo argumento
<img width="1909" height="638" alt="image" src="https://github.com/user-attachments/assets/70dce444-050e-44d7-bb09-b92d36a6f69a" />

Primer argumento
<img width="1915" height="765" alt="image" src="https://github.com/user-attachments/assets/440e4315-deb4-4b46-9e60-209a566f26fd" />

Grep match
<img width="1905" height="840" alt="image" src="https://github.com/user-attachments/assets/6a620ee7-9fab-416f-90c6-7f0f341fcccf" />


* Contraseña obtenida , podemos loguearnos como administrador
 <img width="1469" height="740" alt="image" src="https://github.com/user-attachments/assets/4ede79a4-0ade-4131-ae08-4ef77f658c9e" />
