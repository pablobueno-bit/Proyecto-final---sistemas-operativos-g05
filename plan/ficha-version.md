# Ficha de verificación de versión · Grupo 05

**Distribuciones del grupo 05: Zorin OS (gráfica), Fedora Server (consola) y Ubuntu (imagen base del Dockerfile).**

Aquí se encontraran las preguntas, respuestas y en enlace donde se comprobó los detalles y funcionamiento de cada herramienta usada en el proyecto.

## Zorin OS (VM gráfica)

| Pregunta | Respuesta | Enlace donde lo comprobamos |
|---|---|---|
| Versión elegida y fecha de lanzamiento | Zorin OS-core 18.1 lanzado el 15 de abril de 2026 | https://blog.zorin.com/2026/04/15/zorin-os-18.1-is-released/ |
| Hasta cuándo recibe actualizaciones de seguridad | 1 de junio de 2029 | https://zorin.com/os/details/ |
| Requisitos de hardware y si funciona en VirtualBox | Procesador 1 GHz Dual Core (64-bit), 1.5 GB de RAM (2 GB recomendados), 15 GB de almacenamiento y pantalla 1024×768. Sí funciona en VirtualBox (probado en g05-grafica). | https://help.zorin.com/docs/getting-started/system-requirements/ |
| ¿El instalador permite particionado manual? | Sí, mediante la opción «Más opciones» (*Something else*), que permite crear manualmente `/`, `swap` y `/home`. | https://help.zorin.com/docs/getting-started/install-zorin-os/ |
| Guía oficial para instalar Docker Engine en esa familia | Al pertenecer a la familia Ubuntu (24.04 LTS Noble), se utiliza la guía oficial de Docker para Ubuntu mediante el repositorio apt (docker-ce, docker-ce-cli, containerd.io). | https://docs.docker.com/engine/install/ubuntu/ |
| Imagen base del Dockerfile para esa versión | FROM ubuntu:24.04 (o FROM ubuntu:noble), ya que Zorin OS 18.1 está basado directamente en Ubuntu 24.04 LTS y no cuenta con imagen propia en Docker Hub. | https://hub.docker.com/_/ubuntu | 

RAM que le dimos a la VM y por qué: 4096 MB (4 GB). Aunque el requisito mínimo oficial de Zorin OS es de 2 GB, asignar 4 GB garantiza fluidez en el entorno gráfico (GNOME Shell), evita el uso excesivo de memoria de intercambio (swap) y deja margen suficiente para ejecutar el motor de Docker y contenedores sin degradar el rendimiento de la máquina virtual.

## Fedora Server (VM de consola)

| Pregunta | Respuesta | Enlace donde lo comprobamos |
|---|---|---|
| Versión elegida y fecha de lanzamiento | edora Server 45 (`x86_64`), lanzado el 3 de noviembre de 2026.| https://fedoraproject.org/es/server/download/ https://fedoraproject.org/wiki/Fedora_Linux_45_Release_Party_Schedule |
| Hasta cuándo recibe actualizaciones de seguridad | 8 de diciembre de 2027 (cada versión de Fedora tiene soporte activo durante aproximadamente 13 meses, hasta un mes después del lanzamiento de la versión X+2).  | https://docs.fedoraproject.org/en-US/releases/lifecycle/ |
| Requisitos de hardware y si funciona en VirtualBox | una CPU de 2 GHz Dual Core (64-bit x86_64 o ARM64). RAM: 2 GB mínimo (funciona técnicamente desde 1 GB en modo texto). Almacenamiento: 15 GB mínimo para instalación estándar con LVM (5 GB mínimo técnico). En VirtualBox funciona oficialmente (configurando tipo Linux y versión Fedora 64-bit).  | https://docs.fedoraproject.org/en-US/fedora-server/installation/ |
| ¿El instalador permite particionado manual? | Sí. El instalador Anaconda ofrece la opción "Personalizado" (Custom) o "Blivet-GUI" dentro de Destino de la instalación, permitiendo configurar manualmente particiones estándar, volúmenes lógicos (LVM), Btrfs o arreglos RAID. |https://docs.fedoraproject.org/en-US/fedora-server/installation/  |
| Guía oficial para instalar Docker Engine en esa familia | Al pertenecer a la familia Fedora / RPM, se instala mediante el gestor de paquetes dnf agregando el repositorio oficial de Docker (docker-ce, docker-ce-cli, containerd.io). | https://docs.docker.com/engine/install/fedora/ |
| Imagen base del Dockerfile para esa versión | FROM fedora:45 (o FROM fedora:latest), disponible como imagen oficial mantenida directamente por el Proyecto Fedora en Docker Hub. | https://hub.docker.com/_/fedora |

## Ubuntu (imagen base del Dockerfile)

| Pregunta | Respuesta | Enlace donde lo comprobamos |
|---|---|---|
| Versión elegida y fecha de lanzamiento | | |
| Hasta cuándo recibe actualizaciones de seguridad | | |
| Requisitos de hardware y si funciona en VirtualBox | | |
| ¿El instalador permite particionado manual? | | |
| Guía oficial para instalar Docker Engine en esa familia | | |
| Imagen base del Dockerfile para esa versión | | |
