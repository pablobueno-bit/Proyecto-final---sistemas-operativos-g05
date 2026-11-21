# Sprint 2 · Servicios

**Grupo 5** · VM consola `g05-consola` (Fedora Server) · VM gráfica `g05-grafica` (Zorin OS)

## Video del sprint

<iframe width="560" height="315" src="https://www.youtube.com/embed/ID_DEL_VIDEO"
 title="Sprint 2" frameborder="0" allowfullscreen></iframe>

## 1. Usuarios y grupo

**Qué hicimos:** [un usuario por integrante, el grupo `proyecto` y la carpeta `/srv/proyecto`: el grupo lee y escribe, los demás no entran].

```
sudo groupadd proyecto
sudo useradd -m kevin && sudo passwd kevin
sudo usermod -aG proyecto pablo && sudo usermod -aG proyecto kevin
sudo mkdir -p /srv/proyecto
sudo chown root:proyecto /srv/proyecto
sudo chmod 770 /srv/proyecto
id pablo
getent group proyecto
ls -ld /srv/proyecto
date
```

![id, getent y ls -ld](img/s2-usuarios.png)
![Acceso permitido y acceso negado](img/s2-acceso.png)

**Explicación:** [qué muestra cada captura; quién puede entrar y por qué].

## 2. sudo y permisos

**Qué hicimos:** [un usuario con sudo (grupo `wheel` en Fedora), otro sin sudo al que se le niega; ejemplo de chmod y de chown].

```
sudo -l -U pablo
sudo -u invitado sudo -n true
chmod 640 archivo.txt && ls -l archivo.txt
chmod u+x archivo.txt && ls -l archivo.txt
sudo chown kevin:proyecto archivo.txt && ls -l archivo.txt
date
```

![sudo permitido y sudo negado](img/s2-sudo.png)
![chmod y chown](img/s2-permisos.png)

**Explicación:** [el grupo de administradores de Fedora es `wheel`; qué significa cada permiso].

## 3. Firewall

**Qué hicimos:** [firewalld activo con SSH permitido; servidor en el puerto 8080; curl desde la gráfica falla y luego responde al abrir el puerto].

```
sudo systemctl status firewalld
sudo firewall-cmd --list-all
python3 -m http.server 8080 &
curl -sI http://IP_DE_LA_CONSOLA:8080        # desde la VM gráfica: falla
sudo firewall-cmd --add-port=8080/tcp
curl -sI http://IP_DE_LA_CONSOLA:8080        # desde la VM gráfica: responde
date
```

![Estado del firewall](img/s2-firewall.png)
![curl que falla](img/s2-curl-falla.png)
![curl que responde](img/s2-curl-ok.png)

**Explicación:** [qué es un puerto y por qué antes no respondía].

## 4. Llave SSH y actualización

**Qué hicimos:** [generamos el par de llaves en la gráfica, copiamos la pública a la consola y entramos sin contraseña; actualizamos el sistema].

```
ssh-keygen -t ed25519
ssh-copy-id usuario@IP_DE_LA_CONSOLA
ssh usuario@IP_DE_LA_CONSOLA
sudo dnf upgrade
date
```

![Ingreso por llave](img/s2-llave.png)
![Actualización terminada](img/s2-upgrade.png)

**Explicación:** [diferencia entre llave pública y privada].

## 5. Script gráfico

**Qué hace:** [`organizar.sh` clasifica los archivos de una carpeta por tipo]. Código: [`scripts/organizar.sh`](scripts/organizar.sh) y [`scripts/organizar.desktop`](scripts/organizar.desktop).

![Ejecución desde el ícono](img/s2-script-grafico.png)

**Explicación:** [la función, el if y el ciclo, explicados con tus palabras].

## 6. Script de consola

**Qué hace:** [`respaldo.sh` crea un .tar.gz de una carpeta con validaciones]. Código: [`scripts/respaldo.sh`](scripts/respaldo.sh).

```
./respaldo.sh /srv/proyecto ~/respaldos ; echo "codigo: $?"
./respaldo.sh /noexiste ~/respaldos ; echo "codigo: $?"
date
```

![Caso que funciona y caso que falla](img/s2-script-consola.png)

**Explicación:** [qué códigos de salida usa y qué significa cada uno].

## 7. Procesos

```
ps -eo pid,stat,comm | head
top -b -n 1 | head -n 12
pstree | head
pgrep -l bash
sleep 300 &
renice -n 5 -p PID
kill -STOP PID ; kill -CONT PID ; kill PID
python3 zombi.py &
ps -eo pid,ppid,stat,comm
date
```

![Procesos R, S, T y Z](img/s2-procesos.png)

**Explicación:** [qué significa cada estado R, S, T y Z].

## 8. Docker Engine

```
docker version
docker run hello-world
docker info | grep "Docker Root Dir"
df -h /var/lib/docker
date
```

![docker version y hello-world](img/s2-docker.png)
![Docker Root Dir y df](img/s2-docker-datos.png)

**Explicación:** [por qué el grupo docker equivale a ser administrador; por qué los datos van en `/var`].

## Código del sprint

![codigo_sprint2.txt con cat y date](img/s2-codigo.png)

## Errores y soluciones

| Error | Causa | Solución |
|---|---|---|
| [ ] | [ ] | [ ] |
