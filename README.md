1. ¿Por qué el frontend no necesita conectarse a PostgreSQL?

Porque el frontend se comunica con el backend y es el backend quien se encarga de acceder a la base de datos. Así evitamos que los usuarios puedan acceder directamente a los datos y a las contraseñas de PostgreSQL.

2. ¿Por qué el backend pertenece a dos redes?

Porque necesita comunicarse tanto con el frontend como con PostgreSQL. Por eso está conectado a las dos redes y puede hacer de intermediario entre ambos servicios.

3. ¿Qué servicio necesita publicar un puerto en el anfitrión?

El frontend, porque necesitamos acceder a la aplicación desde nuestro navegador, utilizando un puerto de nuestro ordenador.

4. ¿Por qué publicar PostgreSQL hacia fuera no es la solución adecuada para un fallo de comunicación interno?

Porque el problema está en la comunicación entre los contenedores, no en el acceso desde fuera. Además, publicar PostgreSQL puede ser un riesgo de seguridad porque dejamos la base de datos más expuesta.

5. ¿Qué ventaja ofrece Docker Compose respecto a ejecutar los tres contenedores manualmente?

Que podemos iniciar y gestionar los tres contenedores desde un solo archivo. Así no tenemos que configurar y arrancar cada uno por separado y es mucho más cómodo y rápido.

6. ¿Por qué hemos dividido la arquitectura en dos redes?

Para tener mejor organización y seguridad. Una red sirve para conectar el frontend con el backend y la otra para conectar el backend con PostgreSQL. Así el frontend no puede acceder directamente a la base de datos.

7. ¿Por qué el backend utiliza `db` como dirección de PostgreSQL?

Porque Docker Compose reconoce el nombre del servicio y lo utiliza como dirección dentro de la red. Así el backend puede encontrar PostgreSQL usando db sin tener que conocer su dirección IP.

8. ¿Qué diferencia existe entre detener un proyecto y eliminar sus volúmenes?

Que al detener el proyecto los contenedores dejan de funcionar, pero los datos siguen guardados. En cambio, si eliminamos los volúmenes, también borramos los datos almacenados en la base de datos.

9. ¿Qué consecuencias tendría para la empresa perder el volumen de PostgreSQL?

La empresa podría perder información muy importante, como los clientes, pedidos, facturas y otros datos. Esto podría causar pérdidas económicas y problemas en el funcionamiento de la empresa. Por eso es importante guardar los datos en volúmenes y hacer copias de seguridad para no perderlos.