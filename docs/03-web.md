<h1>LAMP y WEB</h1>

<h3>EL TRIDENTE LAMP</h3>
  <h4>
    · APACHE2
    <br><br>
    · PHPMYADMIN
    <br><br>
    · MARIADB
    <br><br>
  </h4>

  <h5>CONFIGURACIÓN EN EL VIRTUALHOST</h5>
  
  ```bash

    sudo nano /etc/apache2/sites-available/emubub.conf
  
  ```

  - Redirigir todo el tráfico HTTP (puerto 80) a HTTPS, asegurando seguridad en las comunicaciones.
  <br>
  - Configurar el servidor para responder en HTTPS (puerto 443) con certificados SSL ubicados en /espacio/emubase/ssl/.
  <br>
  - Definir /espacio/emubase como la carpeta raíz de la web, donde está alojado todo el contenido estático y dinámico.
  <br>
  - Permitir overrides con .htaccess para mayor flexibilidad.
  <br>
  - Proxy inverso para redirigir todas las peticiones que lleguen a /guacamole/ hacia el cliente VNCserver local corriendo en el puerto 8080, incluyendo soporte para WebSocket, imprescindible para la funcionalidad de Guacamole
  <br>
  - Registro de logs para errores y accesos específicos del sitio.
  <br>
  - Este VirtualHost permite integrar la web y el acceso remoto VNCserver en un único punto centralizado, facilitando la gestión y el acceso desde internet.
  <br>
  - Dentro de /espacio/ (directorio de expansión destinado a añadir capacidad al contenedor LXC que gestiona la página web), carpeta /emubase, contiene toda la página web y los certificados SSL necesarios para HTTPS.
  <br>
  - Aunque no se configuraron reglas específicas de firewall para phpMyAdmin, el acceso a la herramienta está limitado al contenedor Guacamole y a la red interna Tailscale, restringiendo exposición externa directa. Lo protegimos con nuestra contraseña más férrea y un archivo .htpasswd delante.
  <br><br>
  </p>
<h3>ESTÉTICA Y ESTRUCTURA: HTML + CSS </h3>

<div>
  
  #### MAIN
  <img src="https://github.com/tybemuhub/documentacion-emuhub/blob/main/img/main.png">
  <img src="https://github.com/tybemuhub/documentacion-emuhub/blob/main/img/display_main.png">
  
  #### DISCLAIMER
  <img src="https://github.com/tybemuhub/documentacion-emuhub/blob/main/img/disclaimer.png">
  
  #### LOG IN
  <img src="https://github.com/tybemuhub/documentacion-emuhub/blob/main/img/login.png">
  
  #### SIGN UP
  <img src="https://github.com/tybemuhub/documentacion-emuhub/blob/main/img/signup.png">
  
  #### POSTS
  <img src="https://github.com/tybemuhub/documentacion-emuhub/blob/main/img/posts_main.png">
  
  #### EMUCHAT
  <img src="" alt="EMUCHAT">
  
  #### TIMELINE
  <img src="https://github.com/tybemuhub/documentacion-emuhub/blob/main/img/timeline.png">

  #### SETTINGS
  <img src="https://github.com/tybemuhub/documentacion-emuhub/blob/main/img/settings.png">
  <img src="https://github.com/tybemuhub/documentacion-emuhub/blob/main/img/settings_pfp.png">
  
  #### ABOUT
  <img src="https://github.com/tybemuhub/documentacion-emuhub/blob/main/img/about.png">
</div>

<h3>FUNCIONALIDADES: PHP + JAVASCRIPT</h3>

a) Puedes registrar tantos usuarios como desees.
<br><br>
b) Puedes iniciar sesión y disponer de un perfil personal donde
<br><br>
ajustar tus preferencias y publicar lo que desees compartir.
<br><br>
c) Puedes cambiar la contraseña tantas veces como quieras (las
contraseñas se cifran inmediatamente al ser introducidas).
<br><br>
d) Puedes publicar cualquier contenido que desees en texto plano.
<br><br>
e) Verás cómo tus amigos se agregan a tu lista cuando se registran
en la plataforma.
<br><br>
f) Puedes cerrar sesión y no es posible acceder al sitio web sin
volver a iniciarla previamente. Tus datos están protegidos.
<br><br>
g) El panel de administración es una característica que se encuentra
deshabilitada, y solo puede ser activada desde el menú de
phpmyadmin o editando los datos insertados en la propia base de
datos.
<br><br>
h) Como administrador, se autoriza acceso a un panel de control
donde podrás ver datos descriptivos de los usuarios, registros y
también otorgar o revocar privilegios de administrador.
<br><br>
i) Puedes visitar los perfiles de otros usuarios desde tu lista de
amigos. Solo necesitas hacer clic en el nombre o imagen de
alguno de ellos para ser redirigidos a su timeline. Para hacer las
conexiones al perfil de otro usuario independientes de la sesión
actual se usa el userid de los miembros registrados.
<br><br>
j) Puedes elegir una foto de perfil de una piscina predeterminada y
cambiarla en los ajustes. También es posible cambiar el nombre
de usuario, el correo eléctronico, incluso borrar la cuenta.
<br><br>
k) Se ha implementado un asistente de diálogo, para guíar a los
usuarios durante su primer login e indicarles qué posibilidades
existen en nuestra página web.
<br><br>
l) La navegación se ha implementado de la forma más accesible y
visual posible, con menús desplegables, animaciones y unos
estilos coherentes con los protagonistas del proyecto: las
consolas retro.
<br><br>
m) Puedes chatear con todos los usuarios. El emuchat proporciona
una interfaz de mensajería en diferido para comunicarse de forma
privada con otros usuarios. No contamos con un servicio de
mensajería instantánea al uso, pero nos pareció la solución más
eficiente en cuanto a optimización de los recursos restantes.
<br><br>
n) Añadido un disclaimer con información sensible sobre los
permisos legales del proyecto para advertir a los navegantes.
