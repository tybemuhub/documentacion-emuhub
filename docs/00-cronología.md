#Cronología del TFG

Una síntesis visual y técnica del proyecto TFG, desde el hardware y la infraestructura de red hasta la puesta en producción y defensa final. Cada punto resume una fase clave del desarrollo, implementación y securización de un entorno virtualizado autoalojado.
<img src="" alt="arquitectura">
---

## 1. Hardware recomendado para los recursos del proyecto

- Discos duros: cómo se conectan en Proxmox
- Carpeta de red compartida como almacenamiento
- Distribución de recursos por máquina y contenedor (LXC)
- Métricas de rendimiento y análisis

---

## 2. Proxmox

> Virtualización completa del entorno

- Virtualización de sistemas operativos:
  - Ubuntu 22.04 LTS Jammy Jellyfish
  - Solo se trabaja con el repositorio oficial UB22.04_LTS
- Virtualización de contenedores (KVM o LXC)
- Servicios configurados:
  - **Duplicati** (LXC - PVE): backups → carpeta de red (HDD Seagate)
  - **Apache Guacamole** (LXC - 101): cliente VNC/RDP vía navegador
  - **Kuma** (LXC - 103): estado de salud del sistema
  - **Grafana** (LXC - 104): visualización de métricas
  - **Prometheus** (LXC - 105): recopilación de logs

---

## 3. Máquinas virtuales

> Entorno de ejecución para emuladores

- Instalación de VNCServer (consultar guía PINGUINO)
- Instalación de XFCE (liviano, optimizado)
- Configuración de `vncservice` (puerto 5901/8443), `xstartup`
- Explicación técnica:
  - VNCServer proyecta GUI XFCE por protocolo VNC
  - XFCE adaptado → recursos mínimos, máximo rendimiento
  - Emuladores ejecutados desde sesión gráfica bloqueada
- Automatizaciones:
  - Script de arranque automático
  - CRON para reboot si falla el emulador
  - Transferencia de juegos + configuración personalizada
  - Clonado y gestión de red virtual

---

## 4. Apache Guacamole

> Acceso remoto desde navegador, full VNC

- Instalación LXC via scripts helper Proxmox
- Configuración avanzada de permisos y recursos
- Usuario administrador desde interfaz 8080/8443
- Conexión Guacamole ↔ VM emulador (vnc + xfce + guacd → navegador)
- Usuario por emulador con contraseña (12345678)
- Acceso remoto URL directo a la VM

---

## 5. Tailscale

> Red privada virtual portátil (VPN)

- Crear cuenta y unir máquinas a red `tybemuhub@gmail.com`
- Información de nodos (PC, PVE, etc.)
- Acceso Proxmox desde cualquier ubicación
- Comandos esenciales: `tailscaled` + `tailscale up`

---

## 6. Dominio + Cloudflare

> Seguridad y visibilidad web del proyecto

- Compra de dominio en Cloudflare (precio justo, sin intermediarios)
- Email Routing y configuración DNS
- Dominio: `emuhub.org`
- Apertura de puertos y permisos en router
  - Redirección: 443 interno → 8443 externo
- Seguridad:
  - UFW en Guacamole 101
  - Apache Proxy + `.htpasswd`
  - Blindaje de servicios: pruebas de SQL Injection
  - *Pendiente*: prueba de ataque DDoS
  - Certificados SSH

---

## 7. Servidor LAMP

> Infraestructura web y base de datos

- Instalación de Apache2, MariaDB y phpMyAdmin en LXC Guacamole
- Centralización de servicios RDP y web
- Configuración de VirtualHost
- Carpeta `/emubase` → `/espacio` (disco compartido)
- Acceso remoto a phpMyAdmin desde la red Tailscale

---

## 8. Página web

> Proyecto web completamente reciclado, rediseñado y funcional

- Reaprovechamiento del proyecto `mysocialweb.iaw`
- Reescritura completa:
  - **CSS**: nuevo, adaptado a estilo CRT
  - **HTML**: extendido, estructurado
  - **PHP**: nuevas funcionalidades
    - Signup con selector de imagen de perfil
    - Tabla `all_users`: imagen de perfil
    - Tabla `all_mssg`: mensajería instantánea (Emuchat)
    - Menús nuevos: amigos, consolas, timeline, etc.
    - Configuración completa del perfil: cambiar username, correo, foto, contraseña, borrar cuenta
- JavaScript con animaciones y mejoras visuales

---

## 9. Kuma + Prometheus + Grafana

> Trilogía de monitorización

- Supervisión completa del entorno
- Recopilación y análisis de:
  - Logs
  - Accesos
  - Errores
  - Estado general
- Representación visual clara del sistema

---

## 10. Copias de seguridad y almacenamiento

> Redundancia local y remota

- Backups automatizados en **Duplicati**
  - Guardados en `/mnt/pbemuhub` (HDD en casa de Tomeu)
- Acceso desde red Tailscale
- Copias desde el propio Proxmox
- Copias locales, en la nube y físicas

---

## 11. Defensa del proyecto

> Filosofía, formación y ejecución

- Enfoque **self-hosted**: autonomía total
- Síntesis formativa de todo ASIX
- Aprendizaje por iteración: prueba y error
- Mentalidad: **hazlo con propósito**

---
