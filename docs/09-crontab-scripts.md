# 8. Crontab + Script

Para asegurarnos de que el emulador de la máquina virtual esté siempre funcionando, implementamos una tarea programada con **crontab** que se ejecuta cada minuto.

El script está escrito en **bash** y se encarga de comprobar si el proceso del emulador, llamado `"desmume"`, está activo. Si el script detecta que el emulador no está funcionando, registra el evento en un log y reinicia el sistema automáticamente para intentar solucionarlo.

```bash
#!/bin/bash

PROCESS_NAME="desmume"

if ! pgrep -x "$PROCESS_NAME" > /dev/null
then
    echo "$(date): $PROCESS_NAME no está funcionando. Reiniciando el sistema..." >> /var/log/monitor_desmume.log
    sudo reboot
fi
La ejecución de este script está configurada en crontab para que se ejecute cada minuto, asegurando así una supervisión constante.
```

Retos y soluciones
Uno de los principales retos que tuvimos fue encontrar una forma de mantener el emulador siempre activo, incluso si alguien lo cerraba manualmente o si por alguna razón dejaba de funcionar. Después de valorar diferentes opciones, optamos por esta solución sencilla pero efectiva: un script que vigila el proceso y reinicia el sistema si detecta que no está activo.

Gracias a esta medida, conseguimos mantener el emulador disponible sin necesidad de estar pendientes todo el tiempo, lo que mejora la estabilidad y la fiabilidad del proyecto.
