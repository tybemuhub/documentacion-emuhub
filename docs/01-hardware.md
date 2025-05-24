# 1. Hardware

Para llevar a cabo este proyecto de final de grado hemos utilizado un único equipo físico: el ordenador personal de uno de los integrantes del grupo. Aunque no se trata de un servidor profesional, este equipo ha demostrado ser más que suficiente para las necesidades del entorno de virtualización, y su uso responde principalmente a criterios de disponibilidad y presupuesto.

## 1.1 Especificaciones del equipo

El ordenador utilizado cuenta con los siguientes componentes:

- **Procesador:** AMD Ryzen 5 5600X (6 núcleos / 12 hilos), que ofrece un buen rendimiento tanto en tareas multihilo como monohilo, lo que lo hace ideal para ejecutar varias máquinas virtuales de forma fluida.
- **Memoria RAM:** 32 GB DDR4, cantidad que nos ha permitido trabajar cómodamente con varios servicios en paralelo sin cuellos de botella.
- **Almacenamiento:** SSD de 240 GB dedicado exclusivamente a Proxmox y a las máquinas virtuales. No se ha configurado ningún sistema RAID, ya que hemos priorizado la simplicidad y la rapidez de acceso a disco para este entorno.
- **Tarjeta gráfica:** NVIDIA RTX 4060 Ti. Aunque no forma parte activa de las máquinas virtuales, está disponible para futuras pruebas con emulación o tareas que requieran potencia gráfica.
- **Conectividad:** El equipo está conectado mediante una tarjeta de red integrada a una conexión doméstica de 1 Gbps simétrica, sin VLANs ni configuraciones de red avanzadas.

## 1.2 Entorno y condiciones

El servidor está montado localmente en casa del compañero, con un disco dedicado solo para Proxmox. No se han implementado medidas de redundancia eléctrica o de red, ya que el objetivo principal es ofrecer un entorno de pruebas funcional para desarrollar y demostrar los distintos servicios del proyecto.

## 1.3 ¿Por qué este hardware?

La elección se ha basado principalmente en la accesibilidad: este equipo estaba disponible y ofrecía la mejor combinación de potencia y estabilidad dentro de nuestras posibilidades. Aunque no es un servidor profesional, su rendimiento ha sido más que suficiente para desplegar y gestionar todas las máquinas virtuales necesarias. Esta decisión también nos ha permitido centrar los esfuerzos en el desarrollo técnico del proyecto sin depender de una infraestructura externa o con costes adicionales.
