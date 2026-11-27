# Sprint 1 · Montaje

**Grupo 5** · VMs: `g05-grafica` (Zorin OS) y `g05-consola` (Fedora Server)

## Video del sprint

<iframe width="560" height="315" src="https://www.youtube.com/embed/ID_DEL_VIDEO"
 title="Sprint 1" frameborder="0" allowfullscreen></iframe>

## 1. VM gráfica (g05-grafica)

**Qué hicimos:** [instalamos Zorin OS con particionado manual en un disco de 25 GB, con 4 CPU y X GB de RAM].

| Partición | Tamaño | Por qué ese tamaño |
|---|---|---|
| `/` | [14 GB] | Aloja el sistema operativo, librerías y aplicaciones instaladas con margen para actualizaciones. |
| swap | [2 GB] | Respalda la memoria física en disco para evitar cierres por falta de RAM sin quitar demasiado espacio. |
| `/home` | [9 GB] | Guarda los archivos y configuraciones del usuario aprovechando todo el espacio libre restante del disco. |

**Comandos:**

```
lsblk
df -h
cat /etc/fstab
date
```
En esta imagen mostramos el particionado manual de la maquina grafica (aclaramos que se ve así porque lastimosamente perdimos la imagen que había antes del recuadro emergente) 

![Particionado manual](<sprint-1/sprint-1/img/zorin/particionado manual.jpeg>)

En esta imagen mostramos el particionado por medio del comando lsblk

![lsblk](<sprint-1/sprint-1/img/zorin/maquina grafica.jpeg>)

En esta imagen muestra cuánto espacio libre/usado tiene cada partición montada en formato legible (GB/MB) con el comando df -h y  luego se puede apreciar el comando cat /etc/fstab el cual muestra cómo quedan configuradas las particiones para montarse automáticamente al iniciar el sistema.

![df y fstab](<sprint-1/sprint-1/img/zorin/2 terminal.jpeg>)



**Instalación de los navegadores y editores de texto:**

**Comandos:**

```
sudo apt update
sudo apt install -y chromium-browser firefox
sudo apt install -y geany vim nano
sudo dnf install -y make rsync curl git wget
which make rsync curl git wget

```
En la siguiente imagen se puede apreciar el uso del sudo apt update el cual descarga y actualiza la lista local de paquetes disponibles desde los repositorios configurados en el sistema.

![Navegadores2](<sprint-1/sprint-1/img/zorin/4a018a04-daa4-495e-b787-2a878e326c7f.jpg>)

En esta se realizo la instalación de los navegadores con el comando sudo apt install -y chromium-browser firefox

![Navegadores1](<sprint-1/sprint-1/img/zorin/Captura de pantalla 2026-11-26 101358.png>)

Aquí se ven a los 2 navegadores instalados ya abiertos y funcionando 

![Navegadores2](<sprint-1/sprint-1/img/zorin/navegadores.jpeg>)

en la siguiente se instalaron los editores de texto/codigo con sudo apt install -y geany vim nano

![Navegadores2](<sprint-1/sprint-1/img/zorin/Captura de pantalla 2026-11-26 102415.png>)

Verificación de las rutas de los navegadores y editores ejecutando: which brave-browser firefox geany vim nano 

![Navegadores3](<sprint-1/sprint-1/img/zorin/Captura de pantalla 2026-11-26 105035.png>)

Ahora se pueden apreciar los 3 editores de texto abiertos

![Editores de textos](<sprint-1/sprint-1/img/zorin/editores de textos.jpeg>)


**Aqui damos por finalizado el proceso de instalar los mavegadores y los editores de texto/codigo para la maquina g05-grafica**.

## 2. VM consola (g05-consola)

**Qué hicimos:** [instalamos Fedora Server con particionado manual, 25 GB, 2 CPU, X GB de RAM].

| Partición | Tamaño | Por qué ese tamaño |
|---|---|---|
| `/` | [7 GB] | [razón] |
| swap | [2 GB] | [razón] |
| `/var` | [12 GB] | [razón] |
| `/home` | [4 GB] | [razón] |

**Comandos:**

```
lsblk
df -h
cat /etc/fstab
which make rsync curl git wget
date
```

![Editor de particiones](img/consola-particiones.png)
![lsblk, df y fstab](img/consola-comandos.png)
![Herramientas instaladas](img/consola-herramientas.png)

**Explicación:** [qué muestra cada captura].

## 3. Red

**Qué hicimos:** [adaptador 1 en NAT y adaptador 2 en solo anfitrión en las dos VMs].

```
ip a
ping -c 2 IP_DE_LA_OTRA_VM
date
```

![ip a y ping desde la gráfica](img/red-grafica.png)
![ip a y ping desde la consola](img/red-consola.png)

**Explicación:** [IP que recibió cada VM en cada interfaz y por qué con solo NAT no se verían].

## 4. SSH

**Qué hicimos:** [entramos desde la gráfica a la consola].

```
ssh usuario@IP_DE_LA_CONSOLA
date
```

![Sesión SSH abierta](img/ssh.png)

**Explicación:** [qué es SSH y qué se ve en la captura].

## 5. Instantáneas

**Qué hicimos:** [una instantánea llamada `instalacion-limpia` por VM, con la VM apagada].

![Instantánea de g05-grafica](img/snap-grafica.png)
![Instantánea de g05-consola](img/snap-consola.png)

**Explicación:** [para qué sirve una instantánea].

## Código del sprint

![codigo_sprint1.txt con cat y date](img/codigo-sprint1.png)

## Errores y soluciones

| Error | Causa | Solución |
|---|---|---|
| [ej: pantalla negra en Zorin] | [controlador gráfico] | [cambiamos a VBoxSVGA] |
