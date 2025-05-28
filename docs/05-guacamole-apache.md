<h1>APACHE GUACAMOLE</h1>

<h3>FUNCIONALIDADES</h3>
<h6>
· Permite acceder a sesiones de escritorio remoto desde un navegador web. No es necesario instalar ningún software en el cliente.
  <br><br>
· Compatible con protocolos estándar como VNC, RDP, SSH y Kubernetes.
  <br><br>
· Las sesiones VNC pueden grabarse gráficamente.
  <br><br>
· Incluye soporte para Wake-on-LAN.
  <br><br>
· Gestión sencilla de múltiples sesiones de escritorio remoto mediante una interfaz web (escucha en el puerto :8080).
  <br><br>
· Compatible con verificación en dos pasos (TOTP o 2FA).
  <br><br>
· Soporta portapapeles (copiar y pegar) y transferencia de archivos mediante SFTP.
  <br><br>
· Permite conceder o revocar permisos en cualquier momento desde el panel de administración (:8080).
  <br><br>
</h6>

<p>Guacamole puede ser desplegado dentro de LXC y utilizarlo como destino de conexiones remotas y gestionado como pasarela central de acceso remoto. 
  Esta implementación es una práctica mucho más eficiente, segura y escalable, casi obligada; instalar el cliente guacd  en cada VM es un gasto innecesario
  de recursos y espacios. Apache Guacamole puede configurarse tanto desde sus archivos de configuración como desde una interfaz, similar a proxmox, accesible 
  por el navegador. Agregamos usuarios específicos por máquina y conexión ; aunque tuvimos que limitar los accesos a las máquinas a uno concurrente cada una.
</p>

<h3>INSTALACIÓN</h3>

<p>Inicia sesión en tu servidor con Ubuntu 22.04 e instala los paquetes necesarios como dependencias del sistema. A continuación, descarga la versión estable 
  más reciente de Apache Guacamole en formato .tar (para el servidor) y el archivo .war correspondiente a la aplicación cliente. Descomprime el archivo .tar y 
  compílalo ejecutando los siguientes comandos:</p>
  
  ```bash
  sudo make
  ```
  ```bash
  sudo make install
  ```

<p>Una vez completada la instalación, habilita el servicio guacd. Si tienes pensado acceder al entorno Guacamole a través de red, recuerda editar el archivo de
configuración de direcciones escuchadas para que el servicio esté disponible externamente. Después de esto, puedes configurar manualmente los accesos y 
direcciones IP permitidas editando el archivo:</p>

  ```bash
  sudo nano /etc/guacamole/user-mapping.xml
  ```

<p>Este método es útil si prefieres un control directo sobre las conexiones permitidas. Como alternativa, también puedes realizar esta configuración de forma 
visual accediendo al panel de control web de Guacamole desde tu navegador, donde podrás añadir usuarios y conexiones mediante la interfaz gráfica. (:8080)</p>
