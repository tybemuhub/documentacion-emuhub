# 3. Dominio

Para que nuestra web fuera accesible desde cualquier lugar, compramos un dominio **.org** llamado **emuhub.org** a través de Cloudflare. Cloudflare nos ofrece la gestión del DNS y otros servicios que hemos aprovechado para simplificar la configuración.

El dominio apunta directamente a nuestra IP pública, que es la que nos proporciona el proveedor de Internet en casa. Esto nos permite que cualquiera pueda acceder a la web escribiendo emuhub.org:8443, es importante añadir el puerto al final ya que sino no se puede entrar en el navegador.

Para asegurar las conexiones, usamos los certificados SSL que Cloudflare nos facilita de forma automática, así conseguimos que la web funcione con HTTPS sin complicaciones adicionales.

Un reto importante fue configurar el router para que la página fuera visible desde internet. Al principio intentamos usar los puertos estándar 80 y 443, pero no funcionaba. Finalmente descubrimos que teníamos que redirigir esos puertos al 8443 en la máquina donde está alojada la web. Además, fue clave entender que lo realmente importante es la IP pública, no la privada, para que el tráfico externo llegue correctamente a nuestro servidor.

Gracias a estos ajustes, nuestra web está accesible y segura, y la gestión del dominio se realiza sin complicaciones gracias a Cloudflare.
