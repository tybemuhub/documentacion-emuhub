<h1>APACHE GUACAMOLE</h1>

<h3>FEATURES</h3>
· Allows to access remote desktop sessions from a web browser. No other software needs to be installed on the client-side.
· Supports standard protocols like VNC, RDP, SSH and Kubernetes.
· VNC sessions can be recorded graphically.
· Has Wake-on-LAN
· Easily manage multiple remote desktop sessions with browser GUI (listens :8080)
· Supports TOTP two-factor authentication.
· Supports clipboard (copy and paste) and file transfer via SFTP.
· Grant or revoke permissions anytime from the administrator dashboard (:8080)

<p>Guacamole puede ser desplegado dentro de LXC y utilizarlo como destino de conexiones remotas y gestionado como pasarela central de acceso remoto. 
  Esta implementación es una práctica mucho más eficiente, segura y escalable, casi obligada; instalar el cliente guacd  en cada VM es un gasto innecesario
  de recursos y espacios. Apache Guacamole puede configurarse tanto desde sus archivos de configuración como desde una interfaz, similar a proxmox, accesible 
  por el navegador. Agregamos usuarios específicos por máquina y conexión ; aunque tuvimos que limitar los accesos a las máquinas a uno concurrente cada una.
</p>
