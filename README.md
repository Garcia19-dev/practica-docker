# practica-docker

# Laboratorios

# Lab-Docker extrae una imagen del repositorio.

Comando 1: docker search alpine
Explicación:
Este comando busca en Docker Hub (como un "Google de imágenes Docker") todas las imágenes relacionadas con Alpine Linux.

Lo que muestra la pantalla:

Una lista de imágenes que tienen "alpine" en el nombre

La primera es la oficial alpine (la más usada, con 11473 estrellas)

Luego vienen variantes como alpine/git (para Git), alpine/curl, etc.

La columna "OFFICIAL" con [OK] indica que es la imagen oficial mantenida por Alpine

En palabras simples: Es como buscar "alpine" en una tienda de aplicaciones para ver qué opciones hay disponibles.
@Garcia19-dev ➜ /workspaces/practica-docker (main) $ docker search alpine
NAME                DESCRIPTION                                     STARS     OFFICIAL
alpine              A minimal Docker image based on Alpine Linux…   11473     [OK]
alpine/git          A  simple git container running in alpine li…   252       
alpine/socat        Run socat command in alpine container           115       
alpine/curl                                                         12        
alpine/helm         Auto-trigger docker build for kubernetes hel…   70        
alpine/k8s          Kubernetes toolbox for EKS (kubectl, helm, i…   65        
alpine/bombardier   Auto-trigger docker build for bombardier whe…   28        
alpine/httpie       Auto-trigger docker build for `httpie` when …   22        
alpine/terragrunt   Auto-trigger docker build for terragrunt whe…   18        
alpine/openssl      openssl                                         8         
alpine/kubectl      Kubernetes command-line tool for managing cl…   1         
alpine/flake8       Auto-trigger docker build for fake8 via ci c…   2         
alpine/psql         psql — The PostgreSQL Command-Line Client       4         
alpine/ansible      run ansible and ansible-playbook in docker      36        
alpine/jmeter       run jmeter in Docker                            9         
alpine/semver       Docker tool for semantic versioning             4         
alpine/java         Repo containing the build scripts to produce…   5         
alpine/xml          several xml tools to work on xml file as jq …   2         
alpine/mongosh      mongosh - MongoDB Command Line Database Tools   2         
alpine/openclaw     OpenClaw - Your own personal AI assistant. A…   65        
alpine/mysql        mysql client                                    7         
alpine/cfn-nag      Auto-trigger docker build for cfn-nag when n…   0         
alpine/gcloud       Auto-trigger docker build for gcloud (google…   0         
alpine/crane                                                        0         
alpine/bundle       This repository has been archived by the own…   1   

# Comando 2: docker pull alpine
Explicación:
Este comando descarga la imagen oficial de Alpine Linux a tu computadora.

Lo que muestra la pantalla:

Using default tag: latest → Como no especificaste versión, trae la más reciente

589002ba0eae: Pull complete → Descargó una "capa" de la imagen (las imágenes se componen de capas)

Digest: sha256:... → Es como la huella digital de la imagen para verificar que es auténtica

Status: Downloaded newer image for alpine:latest → Confirmación de que se descargó correctamente

En palabras simples: Es como descargar un instalador de Alpine Linux pero en formato "plantilla para contenedores".
@Garcia19-dev ➜ /workspaces/practica-docker (main) $ docker pull alpine
Using default tag: latest
latest: Pulling from library/alpine
589002ba0eae: Pull complete 
Digest: sha256:25109184c71bdad752c8312a8623239686a9a2071e8825f20acb8f2198c3f659
Status: Downloaded newer image for alpine:latest
docker.io/library/alpine:latest

# Comando 3: docker run -it --name alpine_container alpine /bin/sh
Explicación:
Este comando crea y arranca un contenedor usando la imagen que descargaste, y te mete dentro de él.

Partes del comando:

run → Crea y ejecuta un contenedor

-it → Te permite interactuar con el contenedor (como abrir una ventana dentro de él)

--name alpine_container → Le pone nombre "alpine_container" en lugar de uno aleatorio

alpine → La imagen que va a usar

/bin/sh → El programa que ejecuta (un shell, para poder escribir comandos)

Lo que pasa después:
El prompt cambia a / # indicando que ya estás DENTRO del contenedor. Luego ejecutas ls -a para ver qué archivos hay:

Lo que muestra ls -a:

. y .. → Directorios actual y padre

bin, etc, home, usr → Carpetas típicas de Linux

.dockerenv → Un archivo especial que indica que estás dentro de un contenedor Docker
@Garcia19-dev ➜ /workspaces/practica-docker (main) $ docker run -it --name alpine_container alpine /bin/sh
/ # ls -a
.           dev         media       root        sys
..          etc         mnt         run         tmp
.dockerenv  home        opt         sbin        usr
bin         lib         proc        srv         var

# Lab-Docker Run a Container
# Comando 1: sudo apt update y sudo apt install docker.io
Explicación:
Este comando instala Docker en el sistema.

Lo que muestra la pantalla:

Primero actualiza la lista de programas disponibles (apt update)

Luego instala docker.io (la versión de Docker para Ubuntu)

Durante la instalación:

Elimina versiones antiguas de Docker (moby-cli, moby-engine, moby-containerd)

Instala programas nuevos como containerd (el motor que corre los contenedores), bridge-utils (para redes), etc.

Descarga e instala unos 76.8 MB de archivos

En palabras simples: Es como preparar el taller: instalar Docker y todas sus herramientas necesarias para empezar a trabajar.


@Garcia19-dev ➜ /workspaces/practica-docker (main) $ sudo apt update
sudo apt install docker.io
Hit:1 https://packages.microsoft.com/repos/microsoft-ubuntu-noble-prod noble InRelease
Get:2 https://dl.yarnpkg.com/debian stable InRelease            
Hit:3 http://security.ubuntu.com/ubuntu noble-security InRelease
Hit:4 http://archive.ubuntu.com/ubuntu noble InRelease          
Hit:5 https://repo.anaconda.com/pkgs/misc/debrepo/conda stable InRelease
Err:2 https://dl.yarnpkg.com/debian stable InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 62D54FD4003F6525
Hit:6 http://archive.ubuntu.com/ubuntu noble-updates InRelease
Hit:7 http://archive.ubuntu.com/ubuntu noble-backports InRelease
Reading package lists... Done
W: GPG error: https://dl.yarnpkg.com/debian stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 62D54FD4003F6525
E: The repository 'https://dl.yarnpkg.com/debian stable InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following package was automatically installed and is no longer required:
  moby-tini
Use 'sudo apt autoremove' to remove it.
The following additional packages will be installed:
  apparmor bridge-utils containerd dns-root-data dnsmasq-base
  libapparmor1 libnftables1 moby-compose netcat-openbsd
  nftables ubuntu-fan
Suggested packages:
  apparmor-profiles-extra apparmor-utils ifupdown aufs-tools
  btrfs-progs cgroupfs-mount | cgroup-lite debootstrap
  docker-buildx docker-compose-v2 docker-doc rinse zfs-fuse
  | zfsutils firewalld
Recommended packages:
  moby-cli
The following packages will be REMOVED:
  moby-cli moby-containerd moby-engine
The following NEW packages will be installed:
  apparmor bridge-utils containerd dns-root-data dnsmasq-base
  docker.io libnftables1 netcat-openbsd nftables ubuntu-fan
The following packages will be upgraded:
  libapparmor1 moby-compose
2 upgraded, 10 newly installed, 3 to remove and 129 not upgraded.
Need to get 76.8 MB of archives.
After this operation, 107 MB disk space will be freed.
Do you want to continue? [Y/n] y
Get:1 https://packages.microsoft.com/repos/microsoft-ubuntu-noble-prod noble/main amd64 moby-compose amd64 5.1.0-ubuntu24.04u1 [8440 kB]
Get:2 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 libapparmor1 amd64 4.0.1really4.0.1-0ubuntu0.24.04.5 [50.5 kB]
Get:3 http://archive.ubuntu.com/ubuntu noble/main amd64 netcat-openbsd amd64 1.226-1ubuntu2 [44.3 kB]
Get:4 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 apparmor amd64 4.0.1really4.0.1-0ubuntu0.24.04.5 [638 kB]
Get:5 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 libnftables1 amd64 1.0.9-1ubuntu0.1 [359 kB]
Get:6 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 nftables amd64 1.0.9-1ubuntu0.1 [69.8 kB]
Get:7 http://archive.ubuntu.com/ubuntu noble/main amd64 bridge-utils amd64 1.7.1-1ubuntu2 [33.9 kB]
Get:8 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 containerd amd64 1.7.28-0ubuntu1~24.04.2 [38.4 MB]
Get:9 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 dns-root-data all 2024071801~ubuntu0.24.04.1 [5918 B]
Get:10 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 dnsmasq-base amd64 2.90-2ubuntu0.1 [376 kB]
Get:11 http://archive.ubuntu.com/ubuntu noble-updates/universe amd64 docker.io amd64 28.2.2-0ubuntu1~24.04.1 [28.3 MB]
Get:12 http://archive.ubuntu.com/ubuntu noble-updates/universe amd64 ubuntu-fan all 0.12.16+24.04.1 [34.2 kB]
Fetched 76.8 MB in 2s (31.0 MB/s)     
Preconfiguring packages ...
(Reading database ... 58629 files and directories currently installed.)
Preparing to unpack .../moby-compose_5.1.0-ubuntu24.04u1_amd64.deb ...
Unpacking moby-compose (5.1.0-ubuntu24.04u1) over (2.40.3-ubuntu24.04u1) ...
(Reading database ... 58627 files and directories currently installed.)
Removing moby-cli (28.5.1-ubuntu24.04u1) ...
Removing moby-engine (28.5.1-ubuntu24.04u1) ...
/usr/sbin/policy-rc.d returned 101, not running 'stop docker.service'
Unit /etc/systemd/system/docker.service is masked, ignoring.
The unit files have no installation config (WantedBy=, RequiredBy=, UpheldBy=,
Also=, or Alias= settings in the [Install] section, and DefaultInstance= for
template units). This means they are not meant to be enabled or disabled using systemctl.
 
Possible reasons for having these kinds of units are:
• A unit may be statically enabled by being symlinked from another unit's
  .wants/, .requires/, or .upholds/ directory.
• A unit's purpose may be to act as a helper for some other unit which has
  a requirement dependency on it.
• A unit may be started when needed via activation (socket, path, timer,
  D-Bus, udev, scripted systemctl call, ...).
• In case of template units, the unit is meant to be enabled with some
  instance name specified.
System has not been booted with systemd as init system (PID 1). Can't operate.
Failed to connect to bus: Host is down
Removing moby-containerd (1.7.29-ubuntu24.04u1) ...
/usr/sbin/policy-rc.d returned 101, not running 'stop containerd.service'
Unit /etc/systemd/system/containerd.service is masked, ignoring.
The unit files have no installation config (WantedBy=, RequiredBy=, UpheldBy=,
Also=, or Alias= settings in the [Install] section, and DefaultInstance= for
template units). This means they are not meant to be enabled or disabled using systemctl.
 
Possible reasons for having these kinds of units are:
• A unit may be statically enabled by being symlinked from another unit's
  .wants/, .requires/, or .upholds/ directory.
• A unit's purpose may be to act as a helper for some other unit which has
  a requirement dependency on it.
• A unit may be started when needed via activation (socket, path, timer,
  D-Bus, udev, scripted systemctl call, ...).
• In case of template units, the unit is meant to be enabled with some
  instance name specified.
System has not been booted with systemd as init system (PID 1). Can't operate.
Failed to connect to bus: Host is down
(Reading database ... 58590 files and directories currently installed.)
Preparing to unpack .../00-libapparmor1_4.0.1really4.0.1-0ubuntu0.24.04.5_amd64.deb ...
Unpacking libapparmor1:amd64 (4.0.1really4.0.1-0ubuntu0.24.04.5) over (4.0.1really4.0.1-0ubuntu0.24.04.4) ...
Selecting previously unselected package netcat-openbsd.
Preparing to unpack .../01-netcat-openbsd_1.226-1ubuntu2_amd64.deb ...
Unpacking netcat-openbsd (1.226-1ubuntu2) ...
Selecting previously unselected package apparmor.
Preparing to unpack .../02-apparmor_4.0.1really4.0.1-0ubuntu0.24.04.5_amd64.deb ...
Unpacking apparmor (4.0.1really4.0.1-0ubuntu0.24.04.5) ...
Selecting previously unselected package libnftables1:amd64.
Preparing to unpack .../03-libnftables1_1.0.9-1ubuntu0.1_amd64.deb ...
Unpacking libnftables1:amd64 (1.0.9-1ubuntu0.1) ...
Selecting previously unselected package nftables.
Preparing to unpack .../04-nftables_1.0.9-1ubuntu0.1_amd64.deb ...
Unpacking nftables (1.0.9-1ubuntu0.1) ...
Selecting previously unselected package bridge-utils.
Preparing to unpack .../05-bridge-utils_1.7.1-1ubuntu2_amd64.deb ...
Unpacking bridge-utils (1.7.1-1ubuntu2) ...
Selecting previously unselected package containerd.
Preparing to unpack .../06-containerd_1.7.28-0ubuntu1~24.04.2_amd64.deb ...
Unpacking containerd (1.7.28-0ubuntu1~24.04.2) ...
Selecting previously unselected package dns-root-data.
Preparing to unpack .../07-dns-root-data_2024071801~ubuntu0.24.04.1_all.deb ...
Unpacking dns-root-data (2024071801~ubuntu0.24.04.1) ...
Selecting previously unselected package dnsmasq-base.
Preparing to unpack .../08-dnsmasq-base_2.90-2ubuntu0.1_amd64.deb ...
Unpacking dnsmasq-base (2.90-2ubuntu0.1) ...
Selecting previously unselected package docker.io.
Preparing to unpack .../09-docker.io_28.2.2-0ubuntu1~24.04.1_amd64.deb ...
Unpacking docker.io (28.2.2-0ubuntu1~24.04.1) ...
Selecting previously unselected package ubuntu-fan.
Preparing to unpack .../10-ubuntu-fan_0.12.16+24.04.1_all.deb ...
Unpacking ubuntu-fan (0.12.16+24.04.1) ...
Setting up libapparmor1:amd64 (4.0.1really4.0.1-0ubuntu0.24.04.5) ...
Setting up libnftables1:amd64 (1.0.9-1ubuntu0.1) ...
Setting up nftables (1.0.9-1ubuntu0.1) ...
Setting up netcat-openbsd (1.226-1ubuntu2) ...
update-alternatives: using /bin/nc.openbsd to provide /bin/nc (nc) in auto mode
Setting up moby-compose (5.1.0-ubuntu24.04u1) ...
Setting up dnsmasq-base (2.90-2ubuntu0.1) ...
Setting up dns-root-data (2024071801~ubuntu0.24.04.1) ...
Setting up apparmor (4.0.1really4.0.1-0ubuntu0.24.04.5) ...
Created symlink /etc/systemd/system/sysinit.target.wants/apparmor.service → /usr/lib/systemd/system/apparmor.service.
Reloading AppArmor profiles 
Setting up bridge-utils (1.7.1-1ubuntu2) ...
Setting up containerd (1.7.28-0ubuntu1~24.04.2) ...
Created symlink /etc/systemd/system/multi-user.target.wants/containerd.service → /usr/lib/systemd/system/containerd.service.
Setting up ubuntu-fan (0.12.16+24.04.1) ...
Created symlink /etc/systemd/system/multi-user.target.wants/ubuntu-fan.service → /usr/lib/systemd/system/ubuntu-fan.service.
invoke-rc.d: could not determine current runlevel
invoke-rc.d: policy-rc.d denied execution of start.
Setting up docker.io (28.2.2-0ubuntu1~24.04.1) ...
Created symlink /etc/systemd/system/multi-user.target.wants/docker.service → /usr/lib/systemd/system/docker.service.
Created symlink /etc/systemd/system/sockets.target.wants/docker.socket → /usr/lib/systemd/system/docker.socket.
invoke-rc.d: unknown initscript, /etc/init.d/docker not found.
invoke-rc.d: could not determine current runlevel
Processing triggers for dbus (1.14.10-4ubuntu4.1) ...
Processing triggers for libc-bin (2.39-0ubuntu8.6) ...
Processing triggers for man-db (2.12.0-4build2) ...

# Comando 2: sudo systemctl start docker
Explicación:
Intenta encender el servicio de Docker (el motor que hace funcionar todo).

Lo que muestra la pantalla:
Un mensaje de error que dice: "systemd no está corriendo en este contenedor". Esto pasa porque estamos trabajando dentro de un Codespace (que ya es un contenedor) y no podemos prender otro motor desde adentro.

En palabras simples: Es como querer prender el motor de un coche... pero estás dentro de otro coche. No se puede.
@Garcia19-dev ➜ /workspaces/practica-docker (main) $ sudo systemctl start docker

"systemd" is not running in this container due to its overhead.
Use the "service" command to start services instead. e.g.: 

service --status-al

# Comando 3: sudo usermod -aG docker $USER
Explicación:
Agrega tu usuario al grupo "docker" para poder usar Docker sin tener que escribir sudo cada vez.

Lo que hace:

usermod → Comando para modificar usuarios

-aG → Añadir (-a) a un grupo (-G)

docker → El grupo se llama "docker"

$USER → Tu nombre de usuario

En palabras simples: Es como darte la llave de acceso directo para que no tengas que pedir permiso cada vez que quieras usar Docker.


@Garcia19-dev ➜ /workspaces/practica-docker (main) $ sudo usermod -aG docker $USER

# Comando 4: sudo docker pull hello-world
Explicación:
Descarga una imagen de prueba llamada "hello-world" desde Docker Hub.

Lo que muestra la pantalla:

Descarga una capa diminuta (17eec7bbc9d7)

Muestra el "digest" (huella digital) de la imagen

Confirma que se descargó correctamente

En palabras simples: Es como bajar un "hola mundo" en formato contenedor, solo para probar que todo funciona.
@Garcia19-dev ➜ /workspaces/practica-docker (main) $ sudo docker pull hello-world
Using default tag: latest
latest: Pulling from library/hello-world
17eec7bbc9d7: Pull complete 
Digest: sha256:85404b3c53951c3ff5d40de0972b1bb21fafa2e8daa235355baf44f33db9dbdd
Status: Downloaded newer image for hello-world:latest
docker.io/library/hello-world:latest

# Comando 5: sudo docker run hello-world
Explicación:
Ejecuta un contenedor con la imagen hello-world que acabas de descargar.

Lo que muestra la pantalla:
Un mensaje de bienvenida de Docker que explica:

El cliente Docker contactó al motor (demonio)

El motor descargó la imagen desde Docker Hub

Creó un contenedor y ejecutó el programa

Envió la salida a tu terminal

En palabras simples: Es la prueba de fuego: si ves este mensaje, ¡Docker está funcionando perfectamente!


@Garcia19-dev ➜ /workspaces/practica-docker (main) $ sudo docker run hello-world

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/

# Comando 6: sudo docker ps -a
Explicación:
Muestra todos los contenedores que has creado (estén encendidos o apagados).

Lo que muestra la pantalla:

8374035aa9b7 → Contenedor hello-world (creado hace 1 minuto, ya está apagado/Exited)

e8dba9a1b12f → Contenedor alpine (creado hace 7 minutos, sigue encendido/Up)

En palabras simples: Es como mirar el historial de todos los contenedores que has creado, los que están corriendo y los que ya terminaron.
@Garcia19-dev ➜ /workspaces/practica-docker (main) $ sudo docker ps -a
CONTAINER ID   IMAGE         COMMAND     CREATED              STATUS                          PORTS     NAMES
8374035aa9b7   hello-world   "/hello"    About a minute ago   Exited (0) About a minute ago             friendly_goldberg
e8dba9a1b12f   alpine        "/bin/sh"   7 minutes ago        Up 7 minutes                              alpine_container

# Comando 7: sudo docker pull nginx
Explicación:
Descarga la imagen de Nginx (un servidor web muy popular).

Lo que muestra la pantalla:
Descarga 7 capas diferentes (cada una es una parte de Nginx):

206356c42440 → Capa base

75a1d70aee50 → Configuración

Y así sucesivamente hasta completar las 7 capas

En palabras simples: Estás bajando un servidor web profesional para poder usarlo en un contenedor.
@Garcia19-dev ➜ /workspaces/practica-docker (main) $ sudo docker pull nginx
Using default tag: latest
latest: Pulling from library/nginx
206356c42440: Pull complete 
75a1d70aee50: Pull complete 
a9d395129dce: Pull complete 
df9da45c1db2: Pull complete 
18a071c04bd1: Pull complete 
79697674b897: Pull complete 
9eef040df109: Pull complete 
Digest: sha256:bc45d248c4e1d1709321de61566eb2b64d4f0e32765239d66573666be7f13349
Status: Downloaded newer image for nginx:latest
docker.io/library/nginx:latest

# Comando 8: sudo docker run -d -p 80:80 nginx
Explicación:
Ejecuta Nginx en un contenedor con dos opciones importantes.

Lo que hace:

-d (detach) → Lo ejecuta en segundo plano (no ves lo que pasa, sigue trabajando)

-p 80:80 (publish) → Conecta el puerto 80 de tu computadora con el puerto 80 del contenedor

Devuelve un ID largo: 221743d107deb4948ba06a53a153128b5c2b7a87ac1be7706d68bb1fa50dcb74

En palabras simples: Es como prender un servidor web invisible que puedes visitar escribiendo "localhost" en tu navegador.
@Garcia19-dev ➜ /workspaces/practica-docker (main) $ sudo docker run -d -p 80:80 nginx
221743d107deb4948ba06a53a153128b5c2b7a87ac1be7706d68bb1fa50dcb74

# Comando 9: sudo docker ps
Explicación:
Muestra solo los contenedores que están encendidos AHORA MISMO.

Lo que muestra la pantalla:

221743d107de → Nginx (encendido hace 33 segundos, puerto 80 mapeado)

e8dba9a1b12f → Alpine (encendido hace 9 minutos)

En palabras simples: Es como mirar qué contenedores están trabajando actualmente.
@Garcia19-dev ➜ /workspaces/practica-docker (main) $ sudo docker ps
CONTAINER ID   IMAGE     COMMAND                  CREATED          STATUS          PORTS                                 NAMES
221743d107de   nginx     "/docker-entrypoint.…"   33 seconds ago   Up 32 seconds   0.0.0.0:80->80/tcp, [::]:80->80/tcp   relaxed_dijkstra
e8dba9a1b12f   alpine    "/bin/sh"                9 minutes ago    Up 9 minutes                                          alpine_container

# Comando 10: sudo docker logs 221743d107de
Explicación:
Muestra el registro de actividades (logs) del contenedor Nginx.

Lo que muestra la pantalla:
Todo lo que pasó cuando Nginx arrancó:

Scripts de configuración que se ejecutaron

Que habilitó IPv6

Que la configuración está completa y listo para usar

Los procesos trabajadores (workers) que inició (procesos 29 y 30)

La versión de Nginx (1.29.6)

En palabras simples: Es como leer el diario del contenedor para ver qué hizo cuando arrancó y si todo salió bien.
@Garcia19-dev ➜ /workspaces/practica-docker (main) $ sudo docker logs 221743d107de
/docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
/docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
/docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
10-listen-on-ipv6-by-default.sh: info: Getting the checksum of /etc/nginx/conf.d/default.conf
10-listen-on-ipv6-by-default.sh: info: Enabled listen on IPv6 in /etc/nginx/conf.d/default.conf
/docker-entrypoint.sh: Sourcing /docker-entrypoint.d/15-local-resolvers.envsh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/30-tune-worker-processes.sh
/docker-entrypoint.sh: Configuration complete; ready for start up
2026/03/12 20:52:54 [notice] 1#1: using the "epoll" event method
2026/03/12 20:52:54 [notice] 1#1: nginx/1.29.6
2026/03/12 20:52:54 [notice] 1#1: built by gcc 14.2.0 (Debian 14.2.0-19) 
2026/03/12 20:52:54 [notice] 1#1: OS: Linux 6.8.0-1044-azure
2026/03/12 20:52:54 [notice] 1#1: getrlimit(RLIMIT_NOFILE): 1024:524288
2026/03/12 20:52:54 [notice] 1#1: start worker processes
2026/03/12 20:52:54 [notice] 1#1: start worker process 29
2026/03/12 20:52:54 [notice] 1#1: start worker process 30

# Lab-Contenedores de listas de Docker
# 1
@Garcia19-dev ➜ /workspaces/practica-docker (main) $ docker container ls -a
CONTAINER ID   IMAGE         COMMAND                  CREATED          STATUS                      PORTS                                 NAMES
221743d107de   nginx         "/docker-entrypoint.…"   8 minutes ago    Up 8 minutes                0.0.0.0:80->80/tcp, [::]:80->80/tcp   relaxed_dijkstra
8374035aa9b7   hello-world   "/hello"                 10 minutes ago   Exited (0) 10 minutes ago                                         friendly_goldberg
e8dba9a1b12f   alpine        "/bin/sh"                17 minutes ago   Up 17 minutes                                                     alpine_container

# 2
@Garcia19-dev ➜ /workspaces/practica-docker (main) $ docker container inspect jenkins
[]
Error response from daemon: No such container: jenkins

# 3
@Garcia19-dev ➜ /workspaces/practica-docker (main) $ docker container ls -aq
221743d107de
8374035aa9b7
e8dba9a1b12f

# Lab-Contenedores en ejecución con listas de Docker
# Comando 1 
docker container ls -a: Muestra todos los contenedores que has creado (como un inventario), apareciendo el Nginx y Alpine que siguen encendidos y el hello-world que ya se apagó.
@Garcia19-dev ➜ /workspaces/practica-docker (main) $ docker ps
CONTAINER ID   IMAGE     COMMAND                  CREATED          STATUS          PORTS                                 NAMES
221743d107de   nginx     "/docker-entrypoint.…"   11 minutes ago   Up 11 minutes   0.0.0.0:80->80/tcp, [::]:80->80/tcp   relaxed_dijkstra
e8dba9a1b12f   alpine    "/bin/sh"                20 minutes ago   Up 20 minutes                                         alpine_container

# Comando 2 
docker container inspect jenkins: Intenta buscar los detalles técnicos de un contenedor llamado "jenkins", pero como no existe, Docker responde "No such container" (no encontrado).
@Garcia19-dev ➜ /workspaces/practica-docker (main) $ docker ps --filter "name=jenkins"
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
@Garcia19-dev ➜ /workspaces/practica-docker (main) $ 

# Comando 3 docker container ls -aq: Lista solamente los números de ID de todos tus contenedores, sin información adicional, útil para cuando quieres hacer algo con todos ellos de golpe.
@Garcia19-dev ➜ /workspaces/practica-docker (main) $ docker ps -a
CONTAINER ID   IMAGE         COMMAND                  CREATED          STATUS                      PORTS                                 NAMES
221743d107de   nginx         "/docker-entrypoint.…"   12 minutes ago   Up 12 minutes               0.0.0.0:80->80/tcp, [::]:80->80/tcp   relaxed_dijkstra
8374035aa9b7   hello-world   "/hello"                 15 minutes ago   Exited (0) 15 minutes ago                                         friendly_goldberg
e8dba9a1b12f   alpine        "/bin/sh"                21 minutes ago   Up 21 minutes                                                     alpine_container

# Laboratorio 4 : Configuración de un contenedor con la imagen mariadb

# Practicas-Retos

# Practica-Búsqueda de imágenes del repositorio
# Comando 1 
docker pull alpine: Intenta descargar Alpine Linux pero como ya lo teníamos descargado antes, Docker te avisa que "Image is up to date" (la imagen ya está actualizada) y no descarga nada nuevo, solo te confirma que tienes la última versión.

@Garcia19-dev ➜ /workspaces/practica-docker (main) $ docker pull alpine
Using default tag: latest
latest: Pulling from library/alpine
Digest: sha256:25109184c71bdad752c8312a8623239686a9a2071e8825f20acb8f2198c3f659
Status: Image is up to date for alpine:latest
docker.io/library/alpine:latest

# Comando 2 
docker pull ubuntu: Descarga la imagen de Ubuntu y algo interesante pasa: una capa dice "Already exists" (ya existe) porque Docker es inteligente y reutiliza partes que ya tenía guardadas de otras imágenes, ahorrando tiempo y espacio.

@Garcia19-dev ➜ /workspaces/practica-docker (main) $ docker pull ubuntu
Using default tag: latest
latest: Pulling from library/ubuntu
01d7766a2e4a: Already exists 
Digest: sha256:d1e2e92c075e5ca139d51a140fff46f84315c0fdce203eab2807c7e495eff4f9
Status: Downloaded newer image for ubuntu:latest
docker.io/library/ubuntu:latest

# Comando 3 
docker images: Muestra todas las imágenes que tienes guardadas en tu computadora como si fuera tu colección personal: Nginx (161MB), MariaDB (336MB), Ubuntu (78.1MB), Alpine (8.44MB) y el mini hello-world (solo 10kB), cada una con su ID, cuándo se creó y su tamaño.

@Garcia19-dev ➜ /workspaces/practica-docker (main) $ docker images
REPOSITORY    TAG       IMAGE ID       CREATED        SIZE
nginx         latest    99133eed2307   47 hours ago   161MB
mariadb       latest    2bb31c7c9ec5   3 weeks ago    336MB
ubuntu        latest    bbdabce66f1b   4 weeks ago    78.1MB
alpine        latest    a40c03cbb81c   6 weeks ago    8.44MB
hello-world   latest    1b44b5a3e06a   7 months ago   10.1kB

# Practica-Despliegue de batallas espaciales dockerizadas

# Comando 1 
docker pull nginx: Verifica que la imagen de Nginx está actualizada y te confirma que ya tienes la última versión guardada.

@Garcia19-dev ➜ /workspaces/practica-docker (main) $ docker pull nginx
Using default tag: latest
latest: Pulling from library/nginx
Digest: sha256:bc45d248c4e1d1709321de61566eb2b64d4f0e32765239d66573666be7f13349
Status: Image is up to date for nginx:latest
docker.io/library/nginx:latest

# Comando 2 
docker run -d -p 80:80 --name contenedor-nginx nginx: Lanza un servidor web Nginx en segundo plano, conecta el puerto 80 de tu compu con el del contenedor y le pone un nombre fácil de recordar "contenedor-nginx" en lugar de uno aleatorio.

@Garcia19-dev ➜ /workspaces/practica-docker (main) $ docker run -d -p 80:80 --name contenedor-nginx nginx
c3e87a3c4f630ceab3ab41473f17770a4d3fd84dd29181e2e3bccecaf4016f88

# Comando 3 
docker pull alpine: Confirma que Alpine Linux también está en su última versión, igual que con Nginx.

@Garcia19-dev ➜ /workspaces/practica-docker (main) $ docker pull alpine
Using default tag: latest
latest: Pulling from library/alpine
Digest: sha256:25109184c71bdad752c8312a8623239686a9a2071e8825f20acb8f2198c3f659
Status: Image is up to date for alpine:latest
docker.io/library/alpine:latest

# Comando 4 
docker run -dit --name contenedor-alpine alpine: Enciende Alpine en modo "sigiloso" pero dejando la puerta abierta: corre en segundo plano pero con terminal disponible para poder conectarte después cuando quieras.
@Garcia19-dev ➜ /workspaces/practica-docker (main) $ docker run -dit --name contenedor-alpine alpine
2fd383c10bab5f8d70ee6e1d0ed39cdad7b5ea98d5d492dc1646fc0fd755854c

# Comando 5 
docker ps: Muestra todos los contenedores que tienes activos en este momento: el recién creado contenedor-alpine, el contenedor-nginx, un mariadb de prácticas anteriores y el alpine_container del principio, todos funcionando al mismo tiempo como una pequeña flota espacial.

@Garcia19-dev ➜ /workspaces/practica-docker (main) $ docker ps
CONTAINER ID   IMAGE     COMMAND                  CREATED              STATUS              PORTS                                 NAMES
2fd383c10bab   alpine    "/bin/sh"                15 seconds ago       Up 15 seconds                                             contenedor-alpine
c3e87a3c4f63   nginx     "/docker-entrypoint.…"   About a minute ago   Up About a minute   0.0.0.0:80->80/tcp, [::]:80->80/tcp   contenedor-nginx
d14a4715a854   mariadb   "docker-entrypoint.s…"   20 minutes ago       Up 20 minutes       3306/tcp                              some-mariadb
e8dba9a1b12f   alpine    "/bin/sh"                44 minutes ago       Up 44 minutes                                             alpine_container
