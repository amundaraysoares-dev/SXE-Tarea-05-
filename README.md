# Tarea 01

| Elemento | Lo que dice la documentación | Lo que necesita la VM | Otros | Fuente de info |
| ------------ | ------------ | ------------ |------------ | ------------ |
| S.O. | Nada especificado | Ubuntu 26.04.1 LTS | en la pagina oficial de wordpress no me espesifica cual necesito, asi que yo elegi ubuntu server ya que lo he usado en otras ocaciones y a mi pareceres una muy buena distribucion||
| Servidor web|  Apache o Nginx (recomendados) | Apache |  | https://wordpress.org/about/requirements/ |
| Versión de PHP | version 8.3 o superior | version 8.3 |  | https://wordpress.org/about/requirements/| 
| Gestor de BBDD| MariaDB version 10.11 o superior O MySQL version 8.0 o superior.| MySQL 8.0 |  | https://wordpress.org/about/requirements/| 
| Memoria y Disco | para un sitio decente sin tener complicaciones luego: RAM = 2 - 4G / disco: 20G | RAM= 4G / Disco =20G |  en la pagina oficial de wordpress no me espesifica cuanto es necesario por eso le pregunte a gemini cuales serian las especificaiones, al final termine optando por estos valores ya que son los que veo mas optimos en cuestion de que no me de fallo por falta de recursos a futuro |  prompt-gemini: cual es la memoria y disco que necesita wordpress para poder funcionar de la mejor manera |

## Configuracion de MV

Al final en la maquina virtual termine usando las siguientes especificaciones para que mi MV funcione de manera estable sin ningun tipo de problema:

- Para la memoria ram use: 4GB (aun que yo pongo 4000mb, quiero aclarar que es un error ya que tendria que haber puesto 4096mb)
- Para la cantidad de procesadores le he puesto 2

![foto](sex/Captura%20desde%202026-09-17%2011-18-22.png))

- Y para  la memoria unos 20GB 

![foto](sex/Captura%20desde%202026-09-17%2011-20-36.png)

- Por ultimo, desde ajustes de la MV vamos asignar un conector puente para que se pueda conectar con la maquina anfrition 

![foto](sex/Captura%20desde%202026-09-17%2011-36-43.png)

## Instalacion 

- Antes de empezar me gutaria aclarar que en medio de la intalacion de ubunto se encuentra un apartado muy inportante a marcar, que seria el de instalacion del open ssh el cual es necesario para la practica.

![foto](sex/Captura%20desde%202026-09-17%2011-34-56.png)

- Una vez la maquina este en funcionamiento, vamos a conectarnos mediante ssh desde nuestra maquina padre

![fota](sex/Captura%20desde%202026-09-21%2009-21-56.png)

- Ahora para empezar con la instalacion, debemos hacer un update para tener nuestro sistema actualizado e instalaremos las dependencias con el siguiente comando:

![Foto](sex/Captura%20desde%202026-09-21%2009-28-19.png)

- Vamos a hacer la instalacion, para ello, tendremos que ejecutar los siguientes comandos:
- mkadir -p : esto es para crear un directorio el cual sera el 7src/www y el -p sirve para crea una jerarquia de carpetas completa aunque las otras no existan
- chown:  es un comando para cambiear el dueño de la carpeta y el www-data son el grupo/usuario a quines le asignaremos la propiedad, por ultimo la ruta la cual le daremos para que sea el propietario
- Curl / (-u tar -C): la primera parte es la descarga del archivo comprimido y el segundo es para descomprimirlo
![foto](sex/Captura%20desde%202026-09-21%2009-44-36.png)

- Ahora haremos el siguiente comando para modificar el fichero de configuracion de wordpress

![foto](sex/Captura%20desde%202026-09-21%2009-48-34.png)






