# 7. Monitorización: Grafana, Kuma y Prometheus

Para monitorizar el estado y rendimiento de nuestras máquinas virtuales y contenedores, desplegamos tres LXC separados: uno con **Grafana**, otro con **Prometheus** y un tercero con **Kuma**.

## 7.1 Arquitectura y métricas recogidas

Prometheus se encarga de recoger métricas básicas como CPU, memoria, red y disco de todas las máquinas virtuales y LXC. Para ello instalamos **node-exporter** en cada uno de ellos, que es el agente que facilita la extracción de estos datos.

Grafana se conecta a Prometheus para representar visualmente esta información. Usamos la plantilla estándar de Grafana con ID 1860, que ofrece paneles completos y fáciles de interpretar, incluyendo vistas rápidas de CPU, memoria y disco.

## 7.2 Uso de Kuma

Kuma lo hemos incorporado para explorar y probar otras capacidades de monitorización y gestión de servicios, aunque en este proyecto se usa más como herramienta complementaria para entender nuevas opciones de software en este ámbito.

## 7.3 Retos y aprendizaje

La mayor dificultad fue entender cómo funcionaba Prometheus, cómo configurar correctamente sus archivos de scraping para que recogiera la información que necesitábamos, y cómo Grafana se conecta a Prometheus para mostrar estos datos con los paneles adecuados. También nos llevó tiempo configurar el node-exporter en cada máquina para que el sistema fuera fiable y completo.

## 7.4 Acceso y seguridad

Todas estas herramientas se acceden a través de la red local, utilizando los puertos por defecto que requieren los LXC, lo que garantiza un acceso sencillo y seguro dentro del entorno de pruebas.

