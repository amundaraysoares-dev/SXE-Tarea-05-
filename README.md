# Tarea 01

| Elemento | Lo que dice la documentación | Lo que necesita la VM | Otros | Fuente de info |
| :--- | :--- | :--- | :--- | :--- |
| **S.O.** | Nada especificado | Ubuntu 26.04.1 LTS | En la página oficial de WordPress no me especifica cuál necesito, así que yo elegí Ubuntu Server ya que lo he usado en otras ocasiones y a mi parecer es una muy buena distribución. | |
| **Servidor web** | Apache o Nginx (recomendados) | Apache | | [WordPress Requirements](https://wordpress.org/about/requirements/) |
| **Versión de PHP** | Versión 8.3 o superior | Versión 8.3 | | [WordPress Requirements](https://wordpress.org/about/requirements/) |
| **Gestor de BBDD** | MariaDB versión 10.11 o superior O MySQL versión 8.0 o superior. | MySQL 8.0 | | [WordPress Requirements](https://wordpress.org/about/requirements/) |
| **Memoria y Disco** | Para un sitio decente sin tener complicaciones luego: RAM = 2 - 4G / disco: 20G | RAM = 4G / Disco = 20G | En la página oficial de WordPress no me especifica cuánto es necesario, por eso le pregunté a Gemini cuáles serían las especificaciones. Al final terminé optando por estos valores ya que son los que veo más óptimos en cuestión de que no me dé fallo por falta de recursos a futuro. | **Prompt Gemini:** ¿Cuál es la memoria y disco que necesita WordPress para poder funcionar de la mejor manera? |

---

## Configuración de MV

Al final, en la máquina virtual terminé usando las siguientes especificaciones para que mi MV funcione de manera estable sin ningún tipo de problema:

* Para la memoria RAM usé: 4 GB (aunque yo pongo 4000 MB, quiero aclarar que es un error, ya que tendría que haber puesto 4096 MB).
* Para la cantidad de procesadores le he puesto 2.

![Foto](sex/Captura%20desde%202026-09-17%2011-18-22.png)

* Y para la memoria unos 20 GB.

![Foto](sex/Captura%20desde%202026-09-17%2011-20-36.png)

* Por último, desde ajustes de la MV vamos a asignar un adaptador puente para que se pueda conectar con la máquina anfitriona.

![Foto](sex/Captura%20desde%202026-09-17%2011-36-43.png)

---

## Instalación

* Antes de empezar me gustaría aclarar que en medio de la instalación de Ubuntu se encuentra un apartado muy importante a marcar, que sería el de instalación del OpenSSH, el cual es necesario para la práctica.

![Foto](sex/Captura%20desde%202026-09-17%2011-34-56.png)

* Una vez la máquina esté en funcionamiento, vamos a conectarnos mediante SSH desde nuestra máquina padre.

![Foto](sex/Captura%20desde%202026-09-21%2009-21-56.png)

* Ahora, para empezar con la instalación, debemos hacer un `update` para tener nuestro sistema actualizado e instalaremos las dependencias con el siguiente comando:

![Foto](sex/Captura%20desde%202026-09-21%2009-28-19.png)

* Vamos a hacer la instalación. Para ello, tendremos que ejecutar los siguientes comandos:
    * `mkdir -p`: Esto es para crear un directorio el cual será el `src/www`, y el `-p` sirve para crear una jerarquía de carpetas completa aunque las otras no existan.
    * `chown`: Es un comando para cambiar el dueño de la carpeta, y `www-data` es el grupo/usuario a quienes les asignaremos la propiedad. Por último, la ruta a la cual le daremos para que sea el propietario.
    * `curl` / (`-u tar -C`): La primera parte es la descarga del archivo comprimido y la segunda es para descomprimirlo.

![Foto](sex/Captura%20desde%202026-09-21%2009-44-36.png)

* Ahora haremos el siguiente comando para modificar el fichero de configuración de WordPress:

![Foto](sex/Captura%20desde%202026-09-21%2009-48-34.png)

* Ahora configuraremos WordPress para que haga lo siguiente:
    * Asignamos dónde se guardará nuestra web: `src/www/wordpress`.
    * Con qué dirección encontrarla; en este caso sería `localhost`.
    * Y por último, qué permisos tiene: El primero le da autorización para mostrar los archivos a los usuarios y permite a WordPress gestionar sus propios enlaces.

![Foto](sex/Captura%20desde%202026-09-21%2009-50-15.png)

* Ahora tendremos que usar el siguiente comando para publicar nuestro sitio web, haciéndolo visible en internet:

![Foto](sex/Captura%20desde%202026-09-21%2009-52-24.png)

* Tendremos que configurar la base de datos. Para ello, vamos a hacer lo siguiente:

![Foto](sex/Captura%20desde%202026-09-21%2009-55-23.png)

* Vamos a ejecutar los siguientes comandos (menos el primero, que sin querer creé un usuario que no quería):
    * El primer comando es para crear a nuestro usuario y una contraseña, que en mi caso es `seta`.
    * Le daremos todos los privilegios a nuestro usuario.
    * Y el último comando es para recargar los permisos y que se apliquen los cambios.

![Foto](sex/Captura%20desde%202026-09-21%2010-39-42.png)

* Aquí crearemos la base de datos de WordPress con el siguiente comando:

![Foto](sex/Captura%20desde%202026-09-21%2010-40-17.png)

* Ahora tendremos que iniciar sesión con nuestro usuario en nuestra base de datos (nos pedirá la contraseña):

![Foto](sex/Captura%20desde%202026-09-21%2010-42-16.png)

* El siguiente comando crea el archivo de configuración principal de mi sitio web de WordPress usando una plantilla por defecto, que es lo que especificamos al final con `wp-config-sample`:

![Foto](sex/Captura%20desde%202026-09-21%2010-50-51.png)

* Entraremos al fichero con `nano` y una vez dentro modificaremos los siguientes valores con los de nuestro usuario:

![Foto](../../Im%C3%A1genes/Capturas%20de%20pantalla/sex/Captura%20desde%202026-09-21%2010-56-17.png)

* Y ya lo tendríamos en funcionamiento. Ahora solo tenemos que buscar desde el navegador `localhost@la-ip-del-servidor` y entraríamos a nuestra web.
* Dentro habrá que hacer unas pequeñas configuraciones como pueden ser:
    * El idioma.

![Foto](../../Im%C3%A1genes/Capturas%20de%20pantalla/sex/Captura%20desde%202026-09-21%2010-57-39.png)

* El nombre del sitio junto a la creación de un usuario con su respectiva contraseña.
* Una vez acabado, ya podremos instalar nuestro WordPress.

![Foto](sex/Captura%20desde%202026-09-23%2013-38-48.png)

![Foto](sex/Captura%20desde%202026-09-23%2013-39-13.png)

---

## Resultado Final

![Foto](sex/Captura%20desde%202026-09-23%2013-40-15.png)

## Uso de IA

* He recurrido a la IA para que me haga una revisión de las faltas de ortografía y de los signos de puntuación, junto a la pretensión de que me ayude a decorar el Markdown para que no se vea feo.
* Promp: Sin modificar mi texto en el sentido de lo que escribí, solo quiero que me corrijas las faltas de ortografía, pongas bien los puntos y las comas en caso de que esten masl colocados y, por último, si puedes hacer que el Markdown quede mejor decorado: