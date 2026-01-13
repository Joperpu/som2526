

- Dispositivos hardware y controladores
- Instalación de aplicaciones
- Red
- Discos y particiones
- Procesos
- Administrador de impresión

# Unidad 3 - Administración de Ubuntu

## Introducción

La administración de un sistema GNU/Linux (Lubuntu) es amplia y no se centraliza en una sola herramienta. En la práctica se combinan comandos en terminal con utilidades gráficas. Mientras que las GUIs varían entre distribuciones y entornos (en Lubuntu, Centro de configuración de LXQt y herramientas afines), los comandos suelen ser comunes. De hecho, muchas GUIs actúan como front-end de utilidades CLI mediante PolicyKit (pkexec) para elevar privilegios cuando es necesario.

Las tareas de administración requieren privilegios elevados. En Linux el superusuario es root, cuya sesión directa suele estar deshabilitada por defecto. En su lugar, la administración se realiza con sudo: cualquier usuario perteneciente al grupo sudo puede ejecutar acciones administrativas.

Cuando una aplicación gráfica necesita permisos, el sistema mostrará un cuadro de autenticación (polkit) para introducir la contraseña del usuario autorizado. En terminal, se antepone sudo al comando que requiera privilegios. Tras autenticarse, sudo mantiene un “ticket” temporal (por defecto, unos 15 minutos) y no vuelve a pedir la contraseña hasta que caduque; este tiempo es configurable en /etc/sudoers (editar siempre con visudo).

Ejemplo (listar particiones del sistema):

```bash
sudo fdisk -l
```

## Usuario y grupos

Linux (y por extensión Lubuntu) es multiusuario: varias personas (o servicios) pueden iniciar sesión a la vez, localmente o por acceso remoto. Por eso, crear, mantener y auditar cuentas es una tarea habitual de administración. Además de personas, muchos servicios del sistema usan cuentas propias para acotar privilegios.

### Bases de datos de usuarios y grupos

La información de cuentas y grupos se almacena en ficheros de texto gestionados por la libc (consultables también con getent):

- /etc/passwd: usuarios (nombre, UID, GID principal, comentario, home, shell).
- /etc/shadow: contraseñas cifradas y políticas (solo legible por root).
- /etc/group: grupos y sus miembros.
- /etc/gshadow: contraseñas/administración de grupos (solo root).

### Tipos de cuentas

- root: superusuario (UID 0). Tiene control total del sistema. No se recomienda usarlo para trabajo diario; se opera con sudo desde cuentas normales.
- Cuentas del sistema: usadas por servicios y demonios (p. ej., daemon, lp, www-data, _apt, systemd-timesync, etc.). Suelen tener contraseña bloqueada y shell no interactiva (/usr/sbin/nologin), de modo que no están pensadas para iniciar sesión.
- Usuarios estándar: cuentas de personas que sí inician sesión y trabajan en el sistema.

### Identificadores de usuario y de grupo (UID/GID)

Cada cuenta tiene un UID único y cada grupo un GID. En Debian/Ubuntu/Lubuntu se emplean por defecto estos rangos (configurables en /etc/login.defs):

- UID 0 → root.
- 1–999 → cuentas del sistema.
- ≥ 1000 → usuarios estándar (valor por defecto de UID_MIN = 1000).
- El usuario nobody suele tener UID 65534 y el grupo nogroup GID 65534 (mínimos privilegios).

Cuando creas un usuario nuevo, el sistema suele crear también su grupo privado con el mismo número (UID=GID), lo que facilita la gestión de permisos.

### Archivo /etc/passwd

Contiene las cuentas de usuario registradas. Es un fichero de texto donde cada línea es un usuario y los campos están separados por dos puntos :.

Formato (7 campos):

1.	Login → nombre de la cuenta (único).
2.	Contraseña → normalmente x (la contraseña real está en /etc/shadow).
3.	UID → identificador numérico del usuario (único).
4.	GID → identificador del grupo principal del usuario.
5.	Comentario (GECOS) → suele incluir el nombre completo u otros datos.
6.	HOME → directorio personal.
7.	Shell → intérprete de comandos (p. ej., /bin/bash o /usr/sbin/nologin).

### Gestión de usuarios

#### Crear usuarios: useradd

useradd añade una nueva cuenta al sistema. Requiere privilegios y, por seguridad, la cuenta recién creada queda sin contraseña (bloqueada para inicio de sesión) hasta que se le asigne una con passwd.
En Debian/Ubuntu/Lubuntu suele recomendarse adduser (asistente interactivo). Aun así, useradd es la herramienta de bajo nivel estándar.

Sintaxis

```bash
useradd [opciones] login
```

Parámetros

- login  Nombre (único) de la nueva cuenta.

Opciones habituales

- -c, --comment "texto"
Comentario/GECOS (p. ej., nombre completo). Si hay espacios, entre comillas.
- -d, --home <directorio>
Ruta del HOME. Si no existe y usas -m, se crea y se puebla desde /etc/skel.
- -e, --expiredate <AAAA-MM-DD>
Fecha en la que la cuenta expira (queda deshabilitada).
- -f, --inactive <días>
Días de inactividad tras expirar la contraseña antes de desactivar la cuenta.
- -g, --gid <grupo|GID>
Grupo principal. Debe existir. Si no se indica, suele crearse un grupo privado con el mismo nombre que el usuario (según configuración).
- -G, --groups <g1,g2,...>
Grupos suplementarios a los que pertenecerá el usuario.
- -m, --create-home
Crea el directorio HOME si no existe (copiando plantillas de /etc/skel).
- -M
No crear el HOME (incluso si la configuración lo permitiría).
- -s, --shell <ruta_shell>
Shell de inicio (p. ej., /bin/bash, /usr/sbin/nologin).
- -u, --uid <UID>
UID explícito (único y no negativo).
- -r, --system
Crea una cuenta del sistema (UID en rango de sistema, sin login interactivo).

Ejemplos

```bash
# Alta básica con HOME y grupos suplementarios
sudo useradd -m -c "María López" -s /bin/bash -G sudo,lpadmin mlopez
sudo passwd mlopez                       # establecer contraseña (habilita login)

# Crear con HOME personalizado y caducidad de cuenta
sudo useradd -m -d /srv/apps/appuser -e 2026-12-31 -s /usr/sbin/nologin appuser

# Especificar grupo principal existente y UID concreto
sudo useradd -m -u 1501 -g docentes -G audio,video -s /bin/bash pserrano
sudo passwd -l pserrano                  # bloquear contraseña (sin login)
```

#### Modificar cuentas: usermod

usermod modifica propiedades de una cuenta existente (requiere privilegios). Úsalo para cambiar shell, grupos, HOME, caducidad, bloqueo, etc.

Sintaxis

```bash
usermod [opciones] login
```

Parámetros

- login  Nombre actual de la cuenta a modificar.

Opciones habituales

- -c, --comment "texto"  Cambia el campo GECOS (p. ej., nombre completo).
- -d, --home DIR        Establece nuevo HOME.
- -m, --move-home       Mueve el contenido del HOME actual a DIR (usar junto a -d).
- -e, --expiredate AAAA-MM-DD  Fecha en que la cuenta expira (queda deshabilitada).
- -f, --inactive DÍAS   Días de gracia tras caducar la contraseña antes de desactivar la cuenta.
- -g, --gid GRUPO|GID   Cambia el grupo principal (debe existir).
- -G, --groups g1,g2,... Sustituye los grupos suplementarios por la lista indicada.
- -a, --append          Añade a los grupos indicados en -G (sin reemplazar los existentes).
- -l, --login NUEVO     Renombra el login (no renombra el HOME salvo que uses -d -m).
- -s, --shell /ruta/shell Cambia la shell de inicio (p. ej., /bin/bash, /usr/sbin/nologin).
- -u, --uid UID         Cambia el UID (evita colisiones; revisa propiedad de archivos).
- -L, --lock            Bloquea la contraseña (añade ! al hash en /etc/shadow).
- -U, --unlock          Desbloquea la contraseña.

Ejemplos

```bash
# Añadir a grupos sin perder los actuales
sudo usermod -aG audio,video mlopez

# Cambiar shell
sudo usermod -s /bin/bash alumno1

# Cambiar grupo principal
sudo usermod -g docentes pserrano

# Mover HOME a nueva ruta
sudo usermod -d /srv/users/mlopez -m mlopez

# Caducar cuenta en una fecha
sudo usermod -e 2026-06-30 contratada

# Bloquear / desbloquear inicio por contraseña
sudo usermod -L temporal; sudo usermod -U temporal

# Renombrar login (y HOME a juego)
sudo usermod -l marta.lopez mlopez
sudo usermod -d /home/marta.lopez -m marta.lopez
```

#### Eliminar cuentas: userdel

userdel elimina una cuenta de usuario. Requiere privilegios. Por defecto no borra el directorio HOME ni otros archivos del usuario repartidos por el sistema.

Sintaxis

```bash
userdel [opciones] login
```

Parámetros

- login  Nombre de la cuenta a eliminar.

Opciones

- -r, --remove
Borra el HOME y el buzón del usuario (si existen).
- -f, --force
Fuerza el borrado aunque el usuario tenga sesión activa y elimina el HOME incluso si no es propiedad del usuario.

Ejemplos

```bash
# Borrado seguro (sin sesiones activas), conservando HOME
sudo userdel alumno1

# Borrar cuenta y su HOME
sudo userdel -r alumno1

# Si sigue con procesos abiertos, terminar y borrar
loginctl terminate-user alumno1   # o pkill -u alumno1
sudo userdel -r alumno1
```

#### Alta “amigable” y grupos: adduser y addgroup (Debian/Ubuntu/Lubuntu)

En Debian/Ubuntu, adduser y addgroup son front-ends más interactivos y seguros que useradd/groupadd. Preguntan los datos necesarios y crean HOME con las plantillas de /etc/skel (salvo que se indique lo contrario).

Modos de uso

- Crear usuario normal (interactivo):
sudo adduser login
- Crear usuario de sistema (sin login interactivo, sin contraseña):
sudo adduser --system [--no-create-home] [--home DIR] login
- Crear grupo:
sudo addgroup grupo
- Crear grupo de sistema:
sudo addgroup --system grupo
- Añadir usuario existente a grupo existente:
sudo adduser login grupo

Sintaxis

```bash
adduser [opciones] login
addgroup [opciones] grupo
adduser login grupo
```

Opciones habituales

- --home DIR            Establece HOME (lo crea y copia /etc/skel, salvo --no-create-home).
- --no-create-home      No crear HOME.
- --shell SHELL         Shell de inicio (p. ej., /bin/bash).
- --ingroup GRUPO       Grupo principal (en vez de crear uno privado).
- --gid GID             GID del grupo creado / asignado.
- --uid UID             UID específico para el usuario.
- --system              Crear usuario/grupo de sistema.

Ejemplos

```bash
# Usuario normal con HOME, shell bash y grupo adicional 'lpadmin'
sudo adduser mlopez
sudo adduser mlopez lpadmin

# Usuario normal con grupo principal existente y HOME personalizado
sudo adduser --ingroup docentes --home /srv/users/mlopez --shell /bin/bash mlopez

# Usuario de sistema para servicio, sin HOME ni login
sudo adduser --system --no-create-home --shell /usr/sbin/nologin appsvc
sudo addgroup --system appsvc
sudo adduser appsvc appsvc   # asegurarlo en su grupo

# Crear grupo y añadir varios usuarios
sudo addgroup proyectos
sudo adduser ana proyectos
sudo adduser juan proyectos
```

### Administración de contraseñas

#### Cambiar y gestionar contraseñas: passwd

passwd permite cambiar la contraseña de un usuario y ajustar sus políticas de caducidad.
Un usuario estándar solo puede cambiar su propia clave; root puede gestionar la de cualquier cuenta.

Al ejecutarlo, si cambias tu propia clave, pide la contraseña actual y luego solicita la nueva dos veces. Si las entradas coinciden y cumplen la política de PAM (longitud, complejidad, historial…), se actualiza en /etc/shadow.

Sintaxis

```bash
passwd [opciones] [login]
```

Parámetros

- login  Usuario cuyo secreto se gestiona. Si se omite, actúa sobre la cuenta en curso.

Opciones principales

- -d, --delete
Elimina la contraseña (deja la cuenta sin clave). Úsese con cautela.
- -e, --expire
Expira ahora la contraseña para forzar el cambio en el próximo inicio de sesión.
- -i, --inactive DÍAS
Días de gracia tras expirar la clave; después, la cuenta queda deshabilitada.
- -l, --lock
Bloquea la contraseña (antepone ! al hash en /etc/shadow). Impide login por contraseña.
- -u, --unlock
Desbloquea la contraseña (retira el bloqueo).
- -n, --mindays DÍAS
Mínimo de días entre cambios.
- -x, --maxdays DÍAS
Máximo de días que una contraseña puede permanecer sin cambiar.
- -w, --warndays DÍAS
Días de aviso antes de la expiración.
- -S, --status
Muestra el estado de la cuenta/clave de forma resumida.

Ejemplos

```bash
# Cambiar TU propia clave
passwd

# Forzar a un usuario a cambiar la contraseña en el próximo login
sudo passwd -e alumno1

# Bloquear y desbloquear contraseña de una cuenta
sudo passwd -l practicas
sudo passwd -u practicas

# Dejar una cuenta sin contraseña (solo en entornos controlados)
sudo passwd -d laboratorio

# Políticas de caducidad
sudo passwd -x 90 -w 7 -n 1 profesor1   # máx 90 días, aviso 7, mínimo 1 día

# Ver estado
sudo passwd -S profesor1
```

### Gestión de grupos

#### Crear grupos: groupadd

groupadd crea un nuevo grupo en el sistema.

Sintaxis

```bash
groupadd [opciones] grupo
```

Parámetros

- grupo  Nombre del grupo a crear.

Opciones

- -g, --gid GID  Establece el GID del grupo.
- -r, --system   Crea un grupo del sistema.

Ejemplos

```bash
sudo groupadd proyectos
sudo groupadd -g 1500 docentes
sudo groupadd -r _backup
```

#### Modificar grupos: groupmod

groupmod modifica los atributos de un grupo existente.

Sintaxis

```bash
groupmod [opciones] grupo
```

Parámetros

- grupo  Nombre actual del grupo.

Opciones

- -g, --gid GID               Cambia el GID.
- -n, --new-name nuevo_nombre Renombra el grupo.

Ejemplos

```bash
sudo groupmod -n profesores docentes
sudo groupmod -g 1600 profesores
```

#### Eliminar grupos: groupdel

groupdel borra un grupo.

Sintaxis

```bash
groupdel grupo
```

Parámetros

- grupo  Nombre del grupo a eliminar.

Ejemplos

```bash
sudo groupdel proyectos
```

#### Gestionar membresías/contraseñas: gpasswd

gpasswd administra grupos y sus contraseñas. Sin opciones, establece la contraseña del grupo (raro en estaciones de trabajo; se prefiere gestionar membresías).

Sintaxis

```bash
gpasswd [opciones] grupo
```

Parámetros

- grupo  Grupo a gestionar.

Opciones

- -a, --add login        Añade el usuario al grupo.
- -d, --delete login     Quita el usuario del grupo.
- -r, --remove-password  Elimina la contraseña del grupo.

Ejemplos

```bash
# Añadir/quitar miembros
sudo gpasswd -a ana proyectos
sudo gpasswd -d ana proyectos

# Establecer/eliminar contraseña de grupo (uso poco común)
sudo gpasswd proyectos
sudo gpasswd -r proyectos
```

#### Cambiar el grupo principal temporalmente: newgrp

newgrp inicia una nueva sesión de shell cambiando el grupo por defecto del usuario al indicado.

Sintaxis

```bash
newgrp [-] grupo
```

Parámetros

- grupo  Grupo al que unirse como principal.

Opciones

- -  Re-inicializa el entorno como si fuera un login shell.

Comportamiento

- Si el usuario no figura como miembro en /etc/gshadow, se pedirá la contraseña del grupo.
- Si ya es miembro (listado en /etc/gshadow), no se pedirá contraseña.

Ejemplos

```bash
# Cambiar grupo principal en una subshell
newgrp proyectos

# Con entorno de login
newgrp - docentes
```