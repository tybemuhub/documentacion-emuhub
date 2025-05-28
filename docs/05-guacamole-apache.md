<h1>APACHE GUACAMOLE</h1>

<h3>FEATURES</h3>
<h6>
· Allows to access remote desktop sessions from a web browser. No other software needs to be installed on the client-side.
  <br><br>
· Supports standard protocols like VNC, RDP, SSH and Kubernetes.
  <br><br>
· VNC sessions can be recorded graphically.
  <br><br>
· Has Wake-on-LAN
  <br><br>
· Easily manage multiple remote desktop sessions with browser GUI (listens :8080)
  <br><br>
· Supports TOTP two-factor authentication.
  <br><br>
· Supports clipboard (copy and paste) and file transfer via SFTP.
  <br><br>
· Grant or revoke permissions anytime from the administrator dashboard (:8080)
  <br><br>
</h6>

<p>Guacamole puede ser desplegado dentro de LXC y utilizarlo como destino de conexiones remotas y gestionado como pasarela central de acceso remoto. 
  Esta implementación es una práctica mucho más eficiente, segura y escalable, casi obligada; instalar el cliente guacd  en cada VM es un gasto innecesario
  de recursos y espacios. Apache Guacamole puede configurarse tanto desde sus archivos de configuración como desde una interfaz, similar a proxmox, accesible 
  por el navegador. Agregamos usuarios específicos por máquina y conexión ; aunque tuvimos que limitar los accesos a las máquinas a uno concurrente cada una.
</p>
