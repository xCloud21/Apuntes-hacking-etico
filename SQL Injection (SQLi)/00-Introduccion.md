# ¿Que es una SQLi? #
Una inyeccion SQL (SQLi) es una vulnerabilidad de seguridad web que permite a un atacante interferir en las queries que una aplicacion realiza a su Base de Datos. Esto puede permitir al atacante acceder a datos que normalmente no podria
recuperar. Entre ellos, **pueden figurar datos** que pertenecen a otros usuarios o cualquier otro dato al que la aplicacion tenga acceso. En muchos casos, el atacante puede modificar o eliminar estos datos, provocando
cambios persistentes en el contenido o el comportamiento de la aplicacion.
##

:warning: En algunas situaciones, un atacante puede escalar un ataque de inyeccion SQL para comprometer el servidor subayecente u otra infraestura de red de backend. Tambien, puede permitirle realizar ataques de Denegacion de Servicios (DDoS)
###

Todo ello, se puede detectar mediante un conjunto sistematico de pruebas en todos los puntos de entrada de la aplicacion. Lo habitual es:

* **El caracter de comilla simple '** **(buscar errores u otras anomalias**
* Sintaxis especifica de SQL que devuelva el valor base (original) del punto de entrada y un valor diferente. Esto es para **buscar diferencias sistematicas en las respuestas de la aplicacion**
* Condiciones booleanas como OR 1=1 y OR 1=2 . Para **(diferencia en las respuestas de la aplicacion)**
* Payloads diseñados para provocar retrasos cuando se ejecuta dentro de una consulta SQL. Para **(buscar diferencias en el tiempo de respuesta)**

###

✴️ La mayoria de vulnerabilidades se producen en la clausula WHERE de una consulta SELECT. Algunos ejemplos mas comunes son: **Recuperacion de datos ocultos, subvertir la logica de la aplicacion, ataques UNION, SQL Blind**

#

:dart: SQL Injection cheat sheets: https://portswigger.net/web-security/sql-injection/cheat-sheet
