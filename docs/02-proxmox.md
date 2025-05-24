# 2. Proxmox VE

Para la parte de virtualización del proyecto, usamos Proxmox VE, concretamente la versión **8.4.1**. La instalación fue completamente limpia en un disco SSD dedicado, y para hacerlo usamos Ventoy, arrancando desde un USB con el instalador oficial.

## 2.1 Instalación y configuración inicial

Solo tenemos un nodo, que llamamos *pve*, instalado en un SSD de 240 GB exclusivamente para Proxmox y las máquinas virtuales. Elegimos ZFS para gestionar el almacenamiento porque es muy fiable, facilita la gestión de snapshots y recuperación, y al final fue la opción que nos funcionó bien tras varias pruebas.

Después de instalar, usamos un script de post-instalación para configurar cosas básicas y abrir los puertos 80 y 443 en el firewall, para poder acceder al panel web de Proxmox sin problemas desde cualquier dispositivo en la red.

## 2.2 Cómo lo usamos

Con este nodo manejamos tanto máquinas virtuales completas (KVM) como contenedores LXC, porque así podemos aprovechar lo mejor de ambos mundos. Tenemos varias VMs y contenedores que cumplen funciones distintas dentro del proyecto, y el sistema los maneja sin complicaciones.

## 2.3 Problemas y soluciones

Nos encontramos con algunos obstáculos que nos hicieron aprender bastante:

- Tuvimos que conseguir un SSD nuevo para dedicarlo solo a Proxmox, porque el disco anterior no daba la estabilidad necesaria.
- Activamos la virtualización en la BIOS del ordenador, que era un paso fundamental para que todo funcionase.
- Tras probar diferentes configuraciones, vimos que usar ZFS era la clave, ya que sin él no conseguíamos que Proxmox funcionara bien.

Gracias a estos ajustes y pruebas, conseguimos un entorno sólido y estable que nos ha permitido avanzar sin mayores problemas.
