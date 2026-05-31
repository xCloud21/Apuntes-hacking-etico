# ¿Que es una Blind SQLi? #

Se produce cuando una aplicación es vulnerable a la inyección SQL, pero sus respuestas HTTP no contienen los resultados de la consulta SQL en cuestión ni los
detalles de los posibles errores de la base de datos.

Muchas técnicas, como los ataques UNION, no son eficaces ante vulnerabilidades de inyección SQL ciega. Esto se debe a que dependen de poder ver los resultados de la
consulta inyectada en las **respuestas de la aplicación**. Aún así, es posible aprovechar la inyección SQL ciega para acceder a datos no autorizados, pero para ello hay
que emplear técnicas diferentes que se veran en los siguientes puntos.

Es decir, estos ataques van en base a la respuesta del servidor ante la modificacion de la consulta original. Por ejemplo, si la aplicacion se comporta de manera
diferente ante una modificacion de la consulta como por ejemplo mostrando un mensaje de texto de bienvenida. Con esto se puede llegar a "jugar" para averiguar
cierta informacion para revelar datos de otras tablas , o realizar ataques mediante Burp.

