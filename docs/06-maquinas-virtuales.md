<h1>MÁQUINAS VIRTUALES y CONTENEDORES</h1>

<img src="https://github.com/tybemuhub/documentacion-emuhub/blob/main/img/1.JPG" alt="entorno pve completo">

<h4>
  a. VM ULTRALIGERA UBUNTU 22.04 LTS, PREPARAR LA MÁQUINA PARA QUE NO EXISTAN MÁS DATOS DE LOS NECESARIOS.
  <br><br>
  b. INSTALAMOS y CONFIGURAMOS XFCE y VNCSERVER según nuestras preferencias y especificaciones de hardware.
  <br><br>
  c. CONFIGURAMOS UN SERVICIO systemd vncservice QUE ARRANCA UNA INSTANCIA EN EL DISPLAY 1.
  <br><br>
  d. CONFIGURAMOS EL xstartup PARA ARRANCAR EL EMULADOR (Xstartup se ejecuta cuando hay una sesión VNC activa).
  <br><br>
  e. CONFIGURAMOS SCRIPTS AUTOMATIZADOS: launch-(emulador).sh y monitor_(emulador).sh MANEJADOS POR CRON. 
     Si detectan alguna irregularidad en el emulador, la VM se reinicia, así como sus servicios. Asegurando la 
     disponibilidad a las VM incluso si experimentan alguna interferencia o interrupción.
  <br><br>
    > launch-emulador.sh: SE INSERTA DENTRO DE /.vnc/xstartup, este programa define como se arrancan las sesiones XFCE (el desktop).<br><br>
    > monitor_emulador.sh: SE INSERTA DENTRO DE /usr/local/bin, CRON ejecuta este programa cada minuto para reiniciar la VM si el emulador se hubiese apagado).
    <br><br>
  
  ```bash
  #!/bin/bash

PROCESS_NAME="desmume"

if ! pgrep -x "$PROCESS_NAME" > /dev/null
then
    echo "$(date): $PROCESS_NAME no está funcionando. Reiniciando el sistema..." >> /var/log/monitor_desmume.log
    /sbin/reboot
fi
 ```

</h4>

---

## Servicios y Máquinas Virtuales Desplegadas

### SERVICIOS DESPLEGADOS

| ID        | SERVICIO         | FUNCIÓN                                                           |
|-----------|------------------|-------------------------------------------------------------------|
| 101       | APACHE GUACAMOLE | Cliente VNC/RDP accesible vía navegador                          |
| 102 (PVE) | DUPLICATI         | Solución código abierto para backups <br>-- Recurso de red compartido HDD |
| 103       | UPTIME KUMA       | Estado de salud y alertas sobre los servicios y equipos del PVE  |
| 104       | GRAFANA           | Monitorización y análisis de métricas, registros y accesos       |
| 105       | PROMETHEUS        | Recopilación de métricas para conversión legible                |

### VM EMULADOR DESPLEGADAS

| ID  | CONSOLA                   | EMULADOR  |
|------|----------------------------|-----------|
| 100  | GAMEBOY ADVANCE, 2001     | MGBA-QT   |
| 110  | NINTENDO DS, 2004         | DESMUME   |
| 120  | PLAYSTATION ONE, 1994     | PCSXR     |
| 130  | SEGA SATURN, 1994         | YABAUSE   |
| 140  | NINTENDO 64, 1996         | MUPEN64   |
| 150  | NES, 1983                 | FCEUX     |

## VM100-150: EMUHUB100 - EMUHUB150

| RECURSO            | VALOR               |
|--------------------|---------------------|
| MEMORIA            | 4 GB                |
| PROCESADOR         | 2 CPU               |
| BIOS               | SeaBIOS             |
| MÁQUINA            | i440fx              |
| CONTROLADORES      | VirtIO SCSI Single  |
| ALMACENAMIENTO     | LOCAL-LVM {20G}     |
| ADAPTADOR DE RED   | BRIDGED vmbr0       |

## LXC 101: LAMP + APACHE GUACAMOLE

| RECURSO            | VALOR               |
|--------------------|---------------------|
| MEMORIA RAM        | 2 GB                |
| MEMORIA SWAP       | 512 MB              |
| PROCESADOR         | 1 CPU               |
| ALMACENAMIENTO     | LOCAL-PVE {4G}      |
| ADAPTADOR DE RED   | BRIDGED vmbr0       |

## LXC 103: UPTIME KUMA

| RECURSO            | VALOR               |
|--------------------|---------------------|
| MEMORIA RAM        | 1 GB                |
| MEMORIA SWAP       | 512 MB              |
| PROCESADOR         | 1 CPU               |
| ALMACENAMIENTO     | LOCAL-PVE {4G}      |
| ADAPTADOR DE RED   | BRIDGED vmbr0       |

## LXC 104: GRAFANA

| RECURSO            | VALOR               |
|--------------------|---------------------|
| MEMORIA RAM        | 512 MB              |
| MEMORIA SWAP       | 512 MB              |
| PROCESADOR         | 1 CPU               |
| ALMACENAMIENTO     | LOCAL-PVE {2G}      |
| ADAPTADOR DE RED   | BRIDGED vmbr0       |

## LXC 105: PROMETHEUS

| RECURSO            | VALOR               |
|--------------------|---------------------|
| MEMORIA RAM        | 2 GB                |
| MEMORIA SWAP       | 512 MB              |
| PROCESADOR         | 1 CPU               |
| ALMACENAMIENTO     | LOCAL-PVE {4G}      |
| ADAPTADOR DE RED   | BRIDGED vmbr0       |
