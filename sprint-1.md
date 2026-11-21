# Sprint 1 · Montaje

**Grupo 5** · VMs: `g05-grafica` (Zorin OS) y `g05-consola` (Fedora Server)

## Video del sprint

<iframe width="560" height="315" src="https://www.youtube.com/embed/ID_DEL_VIDEO"
 title="Sprint 1" frameborder="0" allowfullscreen></iframe>

## 1. VM gráfica (g05-grafica)

**Qué hicimos:** [instalamos Zorin OS con particionado manual en un disco de 25 GB, con 2 CPU y X GB de RAM].

| Partición | Tamaño | Por qué ese tamaño |
|---|---|---|
| `/` | [14 GB] | [razón en una frase] |
| swap | [3 GB] | [razón en una frase] |
| `/home` | [8 GB] | [razón en una frase] |

**Comandos:**

```
lsblk
df -h
cat /etc/fstab
date
```

![Editor de particiones](img/grafica-particiones.png)
![lsblk, df y fstab](img/grafica-comandos.png)
![Navegadores y editores instalados](img/grafica-programas.png)

**Explicación:** [qué muestra cada captura y qué navegadores y editores instalamos].

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
