# Unidad 3 - Configuración y administración de sistemas basados en Linux

Esquema

- Introducción a Lubuntu
    - Interfaz
    - Escritorio
- Introducción al uso de comandos
    - Comandos iniciales 

- Gestión de archivos
- Montaje de dispositivos de almacenamiento
- Gestión de archivos y directorios en CLI

- Usuarios y grupos
- Permisos de archivo
- Dispositivos hardware y controladores
- Instalación de aplicaciones
- Red
- Discos y particiones
- Procesos
- Administrador de impresión

## Introducción a Lubuntu

Lubuntu es un *sabor oficial* de Ubuntu orientado a equipos ligeros y a quienes prefieren un entorno sencillo y eficiente. Hereda la base tecnológica de Ubuntu/Debian (mismos repositorios y ciclo de publicación), pero utiliza el entorno de escritorio LXQt, que consume menos recursos que escritorios más pesados.
Históricamente Lubuntu usó LXDE; desde Lubuntu 18.10 el proyecto adopta LXQt como entorno por defecto. LXQt no es un “shell” sobre GNOME: es un entorno de escritorio completo (panel, gestor de archivos, configuración, etc.) construido con Qt, independiente de GNOME y de su shell. Esta elección da a Lubuntu una identidad propia: arranque rápido, baja huella de memoria y una experiencia limpia sin renunciar a las herramientas habituales del ecosistema Ubuntu.

### Versiones de Lubuntu

Lubuntu sigue el mismo calendario de lanzamientos que Ubuntu:

- Versiones regulares: cada 6 meses. Aportan novedades y cambios incrementales. Su soporte típico es de 9 meses.
- Versiones LTS (Long Term Support): cada 2 años. Priorizan estabilidad.
- En Ubuntu “base” el soporte LTS es de 5 años.
- En los sabores oficiales (como Lubuntu), el soporte LTS suele ser de 3 años.

Si quieres lo último en software y escritorio, puedes ir actualizando entre versiones regulares. Si buscas estabilidad a medio plazo y menos cambios, lo habitual es instalar una LTS y actualizar a la siguiente LTS cuando corresponda.

Cada lanzamiento tiene número de versión y nombre en clave:

- Número de versión: año.mes. Por ejemplo, 24.04 corresponde a abril de 2024.
- Nombre en clave: un adjetivo + un animal con la misma letra inicial, siguiendo orden alfabético (compartido con Ubuntu).
- Es posible actualizar desde una versión a otra sin reinstalar, usando las herramientas de actualización del sistema.

La LTS vigente en el ecosistema Ubuntu es 24.04 LTS; en Lubuntu, como sabor oficial, esa LTS se ofrece con el soporte propio del proyecto (habitualmente 3 años), mientras que las versiones regulares mantienen el ciclo de 9 meses.

### El software de Lubuntu

Lubuntu incluye una colección de aplicaciones gráficas para configurar el sistema y cubrir las tareas habituales, y se beneficia de los mismos repositorios que Ubuntu. El escritorio predeterminado es LXQt y su ciclo de publicación se sincroniza con el de Ubuntu.
Además de Lubuntu, existen otros sabores oficiales que ofrecen distintos escritorios: Kubuntu (KDE Plasma), Xubuntu (Xfce), Ubuntu MATE, Ubuntu Budgie, etc. En cualquier sistema basado en Ubuntu puedes instalar otros escritorios desde los repositorios si lo prefieres.

Aplicaciones de Lubuntu (orientadas a ligereza y uso cotidiano):
	
- Navegación web: Mozilla Firefox.
- Ofimática: LibreOffice (suele incluir al menos Writer y Calc).
- Multimedia: VLC como reproductor versátil.
- Gestión de archivos: PCManFM-Qt.
- Imágenes/PDF: LXImage-Qt y visor PDF ligero (p. ej., qpdfview).
- Terminal y editor: QTerminal y FeatherPad.
- Gestión de software: centro de software y/o gestor de paquetes (según versión, se ofrece una tienda gráfica y herramientas APT).

### Interfaz de usuario

Lubuntu utiliza como interfaz predeterminada el entorno de escritorio LXQt, pensado para ofrecer una experiencia ligera, rápida y con bajo consumo de recursos. Históricamente, Lubuntu empleó LXDE; desde Lubuntu 18.10 el proyecto migró a LXQt, manteniendo la base de Ubuntu pero con un escritorio basado en Qt (no en GNOME).

LXQt proporciona panel, menú de aplicaciones, área de notificación e integraciones básicas, con un diseño sencillo y eficiente orientado a equipos modestos y a usuarios que buscan un entorno sin distracciones. A diferencia de “shells” como GNOME Shell o Unity, LXQt es un entorno completo independiente de GNOME, con sus propias herramientas de configuración y utilidades.

Elementos principales:

- Panel: por defecto en la parte inferior; contiene el menú, lanzadores, gestor de tareas, bandeja del sistema (red, sonido, energía…) y reloj.
- Menú de aplicaciones: clasifica el software por categorías y permite buscar escribiendo.
- Lanzadores (Quick Launch): accesos directos a tus apps favoritas fijados en el panel.
- Gestor de tareas: lista y agrupa ventanas abiertas; permite cambiar rápidamente entre ellas.
- Espacios de trabajo (workspaces): escritorios virtuales para organizar ventanas.
- LXQt Runner: ejecutor rápido para abrir aplicaciones o lanzar comandos (tipo “Alt+F2”).

Vamos a ver con detalle los equivalentes en Lubuntu a los apartados clásicos.

#### Panel y lanzadores (Quick Launch)

El panel de LXQt muestra tus lanzadores junto al gestor de tareas y a la bandeja del sistema.

- Puedes anclar aplicaciones arrastrándolas desde el menú al panel (o con clic derecho → Añadir al panel).
- Es posible ocultar automáticamente el panel (auto-ocultar) o usar modo siempre visible.
- Los lanzadores abren la aplicación asociada; si arrastras un archivo a la ventana de una app, se abre con esa app (el arrastre al lanzador puede variar según el plugin: lo habitual es lanzar la app, no “soltar” archivos sobre el botón).
- Incluye accesos típicos: gestor de archivos (PCManFM-Qt), navegador, ofimática, papelera, etc. Puedes añadir/quitar elementos desde Configuración del panel.

#### Menú de aplicaciones 

En Lubuntu no existe el “Tablero” de Unity; su equivalente práctico es el Menú de aplicaciones de LXQt y el ejecutor (Runner).

- Abrir el menú: clic en el icono de Lubuntu (panel) o tecla Super (suele estar mapeada para abrir el menú; si no, puedes asignarla).
- Buscar: basta con escribir en el menú para filtrar aplicaciones y herramientas del sistema.
- Favoritos y recientes: el menú permite fijar apps y acceder rápidamente a las usadas recientemente.

#### Búsqueda integrada y LXQt Runner

Además del buscador del menú, Lubuntu incluye LXQt Runner (ejecutor rápido, tipo Alt+F2):

- Abrir Runner: normalmente Alt+F2 (o la combinación que hayas configurado).
- Escribe el nombre de una app o un comando (p. ej., lxqt-config, pcmanfm-qt, htop) y Enter.
- Runner y el buscador del menú cubren la mayoría de casos de “buscar y abrir” sin necesidad de navegar por categorías.

#### Panel (detalle)

El panel en la parte superior o inferior (por defecto, inferior) se organiza así:

- Izquierda: icono del menú y lanzadores fijados.
- Centro: gestor de tareas (ventanas abiertas, con agrupación opcional).
- Derecha: bandeja del sistema (red/sonido/energía/notificaciones), selector de teclado, reloj/calendario y, si quieres, cambiador de espacios de trabajo (Pager).

A diferencia de Unity, no hay “menú global”: los menús de cada aplicación se muestran en su propia ventana.

#### Espacios de trabajo (workspaces)

Lubuntu soporta escritorios virtuales para separar tareas:

- Activa el cambiador de espacios (plugin Pager) en el panel si no está visible.
- Mueve ventanas entre escritorios con clic derecho en la barra de título → Mover a escritorio.
- También puedes usar atajos (ver abajo) para cambiar de workspace.

#### Atajos de teclado (personalizables)

Los atajos se gestionan en Preferencias de LXQt → Atajos de teclado. Algunos habituales (pueden variar según imagen y versión):

- Abrir menú: Super
- Runner (ejecutor rápido): Alt+F2
- Cambiar ventana: Alt+Tab
- Cambiar de espacio de trabajo: Ctrl+Alt+←/→
- Captura de pantalla: Impr Pant (herramienta por defecto, p. ej., Screengrab; puedes cambiarla)
- Bloquear sesión: asignable (p. ej., Super+L)
- Abrir gestor de archivos: asignable (p. ej., Super+E)

Si alguna combinación no funciona como esperas, asígnala de nuevo en Atajos o revisa conflictos en el gestor de ventanas.

### Escritorio LXQt

Lubuntu utiliza LXQt como escritorio predeterminado. Es un entorno ligero y modular, orientado a equipos con pocos recursos y a usuarios que prefieren una experiencia rápida y sin distracciones. Aunque pueden instalarse otros escritorios (Xfce, KDE Plasma, GNOME…), no es lo habitual, ya que mantener varios consume más espacio en disco y memoria.

A diferencia de Unity o GNOME Shell, LXQt no es un “shell” sobre otro escritorio, sino un entorno completo: panel, menú, gestor de tareas, área de notificación, utilidades de configuración y componentes propios. Funciona bien sin aceleración 3D dedicada, por lo que no exige una GPU potente para mostrar su interfaz.

Elementos destacados del escritorio LXQt:

- Panel (por defecto, inferior): menú, lanzadores, lista de ventanas, bandeja del sistema y reloj.
- Menú de aplicaciones con búsqueda integrada.
- Lanzadores rápidos fijados en el panel.
- Espacios de trabajo (escritorios virtuales).
- LXQt Runner (tipo Alt+F2) para abrir aplicaciones/comandos al vuelo.
- Herramientas de configuración propias (apariencia, teclado/ratón, sesión, energía…).

## Introducción al uso de comandos

En sus orígenes, GNU/Linux se utilizaba sin interfaz gráfica, a través de una interfaz de línea de comandos (CLI, Command-Line Interface) heredada de Unix. Las tareas de administración (usuarios, servicios, archivos, procesos, red, etc.) se realizaban mediante comandos ejecutados en una shell.

Con los escritorios gráficos llegaron utilidades de configuración pensadas para el usuario final. Muchas son front-ends que internamente lanzan comandos o editan archivos por ti. Aun así, para administrar un sistema GNU/Linux con soltura, sigue siendo imprescindible conocer los comandos básicos y entender la estructura del sistema (archivos, permisos, procesos, servicios, dispositivos…).

En Lubuntu (escritorio LXQt) abrirás la terminal con QTerminal. Desde ahí podrás ejecutar todos los comandos del sistema.

### El intérprete de comandos

Una shell es el intérprete de comandos: la interfaz textual tradicional de los sistemas tipo Unix (como GNU/Linux). Recibe líneas de texto, las interpreta y ejecuta.

- Windows
	- Símbolo del sistema (cmd.exe): consola clásica.
	- PowerShell: consola moderna con scripting basado en objetos; existe PowerShell 7 multiplataforma.
- GNU/Linux (varias shells disponibles)
	- bash (Bourne Again SHell): estándar de facto y predeterminada en Ubuntu/Lubuntu.
	- zsh: muy popular por autocompletado y personalización.
	- fish: enfoque interactivo con sugerencias.
	- ksh, csh/tcsh: históricas, hoy menos comunes.

En Lubuntu la shell interactiva por defecto es bash, y será la que utilicemos en estos apuntes.

### Consolas de texto

Cuando Lubuntu arranca lo hace, por defecto, en sesión gráfica (LXQt). Aun así, el sistema también habilita varias consolas de texto (TTY) para abrir sesiones sin entorno gráfico.
Puedes acceder a ellas con Ctrl+Alt+F1…F6 (en algunos equipos la GUI queda en otra TTY, ver nota más abajo).

Para iniciar sesión en una consola texto, introduce usuario y contraseña. Si la autenticación es correcta aparecerá el prompt (indicador de órdenes). Para cerrar la sesión, usa el comando exit.

Puedes mantener varias sesiones texto simultáneas (una por TTY), que consumen muy pocos recursos. También puedes alternar entre texto y GUI en cualquier momento.

El prompt suele terminar en $ (usuario normal) o # (superusuario). En Ubuntu/Lubuntu, por defecto se muestra así:

```bash
usuario@equipo:directorio_actual$
```
El carácter ~ indica tu carpeta personal (abreviatura de /home/usuario).

### Ventana de terminal

Desde la sesión gráfica también puedes ejecutar comandos en una terminal (equivalente al “Símbolo del sistema” en Windows). En Lubuntu la aplicación por defecto es QTerminal.

Abrir QTerminal:

1. Menú LXQt (icono de Lubuntu en el panel).
2. Busca “QTerminal” o ve a Sistema → QTerminal.
3. Haz clic para abrir.

Ventajas de la terminal gráfica (frente a una TTY):

- Barra de desplazamiento para revisar el historial de salida.
- Pestañas (varias terminales en una sola ventana).
- Personalización de aspecto (tema, color de fondo, fuente, tamaño).
- Copiar/pegar fácilmente (clic derecho o atajos como Ctrl+Shift+C / Ctrl+Shift+V).
- Búsqueda en el contenido de la terminal (Ctrl+Shift+F).

### Usuario administrador y usuario root

En GNU/Linux (y por tanto en Lubuntu) el usuario creado durante la instalación puede realizar tareas administrativas. El superusuario con acceso total es root, y en Ubuntu/Lubuntu está deshabilitado por defecto.

Cuando una aplicación vaya a modificar la configuración del equipo, aparecerá un cuadro pidiendo la contraseña del usuario administrador. En la línea de comandos, para ejecutar acciones con privilegios se antepone sudo:

```bash
sudo comando
```

Tras introducir la contraseña, el comando se ejecutará como si fuera root.

También es posible habilitar la cuenta root y abrir sesión con ella, pero por defecto en Ubuntu/Lubuntu no se permiten sesiones gráficas con root (solo texto), y no se recomienda habilitarla salvo necesidad.

### Documentación de comandos

La documentación en GNU/Linux es abundante, aunque puede resultar difícil de localizar por la gran cantidad de programas incluidos en una distribución. Aun así, todo está documentado y existen múltiples fuentes accesibles en línea, gracias al espíritu colaborativo del proyecto.

#### Documentación de Lubuntu/Ubuntu

Desde el portal oficial de Ubuntu/Lubuntu puedes acceder a la documentación del sistema: elige la versión con la que trabajas y consulta guías de tareas administrativas organizadas por categorías. Además, hay foros y sitios comunitarios donde encontrar soluciones y ejemplos prácticos.

#### Manual universal de comandos: man

En GNU/Linux (incluido Lubuntu) casi cada programa tiene su página de manual (man page). Son la referencia básica para aprender sintaxis y opciones de los comandos que se ejecutan en terminal. Las man pages se instalan junto con los paquetes del sistema, por lo que solo verás la documentación de aquello que tengas instalado y en la versión correspondiente.

Además de man existen las páginas de información de GNU (accesibles con info), que a menudo son más explicativas, con índice e hipervínculos internos. En algunos casos, info re-formatea el contenido de man, pero en proyectos GNU suele incluir guías y ejemplos más extensos.

Cómo usar man:

```bash
man concepto
```

donde concepto es el nombre del comando, programa, fichero o tema que quieres consultar.

El manual está dividido en secciones (1: comandos de usuario, 5: formatos/archivos, etc.). Puede haber más de una página con el mismo nombre en secciones distintas. Si escribes solo man concepto, se abre la primera coincidencia. Para una sección concreta:

```bash
man 5 crontab    # Sección 5: formato del fichero crontab
man crontab      # Normalmente sección 1: comando crontab
```

Para saber qué sección estás leyendo, fíjate en la primera línea de la página de manual: aparece el nombre y, entre paréntesis, el número de sección (p. ej., CRONTAB(1) o CRONTAB(5)).

### Comandos iniciales

Para familiarizarnos con la línea de comandos, veremos órdenes básicas para obtener información del sistema. Indicamos sintaxis y opciones más habituales (las completas están en man).

#### Mostrar identificador de usuario

##### whoami

Muestra el nombre del usuario con la sesión actual.

Sintaxis

```bash
whoami [OPCIONES]
```

Opciones:

- --help Muestra la ayuda del comando.
- --version Muestra la versión del comando.

##### id

Muestra información del usuario, incluyendo UID, GID y grupos.

Sintaxis

```bash
id [OPCIONES] [USUARIO]
```

Opciones (más comunes):

- -u Muestra solo el UID.
- -g Muestra solo el GID.
- -G Muestra todos los grupos (IDs numéricos).
- -n Muestra nombres en lugar de IDs (combina con -u, -g o -G).
- -r Muestra IDs reales (no efectivos), si aplica.
- --help, --version Ayuda y versión.

```bash
id
id -u            # Solo UID
id -un           # Nombre de usuario
id -G            # IDs de grupos
id -Gn           # Nombres de grupos
id nombre_usuario
```

#### Mostrar directorio activo

##### pwd

Muestra la ruta del directorio de trabajo (donde estás ahora).

Sintaxis

```bash
pwd [OPCIONES]
```

Opciones más comunes:

- -L, --logical Muestra la ruta lógica (sin resolver enlaces simbólicos).
- -P, --physical Muestra la ruta física (resolviendo enlaces simbólicos).
- --help Ayuda del comando.
- --version Versión.

Ejemplos

```bash
pwd           # Ruta actual
pwd -L        # Ruta lógica (tal y como navegas)
pwd -P        # Ruta física (resuelve symlinks)
```

#### Mostrar el histórico de comandos

El comando history muestra la lista de órdenes ejecutadas en la sesión de la shell.

Sintaxis

```bash
history [N]
history -c | -d POS | -a | -r | -w
```

Opciones (más usadas):

- 	N Muestra solo los N últimos comandos.
- -c Borra el histórico en memoria.
- -d POS Elimina la entrada en la posición indicada.
- -a / -w / -r Añadir / escribir / leer el histórico al/desde el fichero (~/.bash_history).

#### Limpiar la pantalla

El comando clear limpia el contenido visible de la terminal (no borra el histórico).

Sintaxis

```bash
clear
```

#### Información de la conexión de red

##### ip (recomendado)

Sintaxis básica

```bash
ip addr show [INTERFAZ]   # Direcciones (IPv4/IPv6)
ip link show [INTERFAZ]   # Enlaces (estado, MAC, MTU…)
ip route show             # Tabla de rutas
```

Ejemplos

```bash
ip a            # Resumen de direcciones de todas las interfaces
ip a s enp3s0   # Dirección de una interfaz concreta
ip r            # Rutas
hostname -I     # (rápido) direcciones IP del host
```

##### ifconfig

Sintaxis

```bash
ifconfig [-a] [-s] [INTERFAZ]
```

Opciones

- -a Muestra todas las interfaces.
- -s Muestra un resumen estadístico.

#### Mostrar la fecha del sistema

##### date

Muestra (y puede establecer) la fecha y hora del sistema.

Sintaxis

```bash
date [OPCIONES] [+FORMATO]
date [-u|--utc|--universal] [MMDDhhmm[[CC]YY][.ss]]
```

Argumentos:

- +FORMATO Cadena de formato de salida (ver man date).
- -u|--utc|--universal Muestra la hora UTC.
- MMDDhhmm[[CC]YY][.ss] Establece fecha/hora (mes, día, hora, min, siglo/año, segundos).

Ejemplos

```bash
date                    # Fecha y hora actuales
date -u                 # En UTC
date +"%Y-%m-%d %H:%M"  # Formato personalizado
```

##### cal

Muestra un calendario

Sintaxis

```bash
cal [-3hjy] [-A N] [-B N] [[mes] año]
```

Argumentos:

- [[mes] año] Mes y año de referencia.

Opciones:

- -A N Muestra N meses después del mes de referencia.
- -B N Muestra N meses antes.
- -3 Muestra mes anterior, actual y siguiente.
- -h No resalta el día actual.
- -j Días julianos (conteo desde 1 de enero).
- -y Año completo actual.

Ejemplos

```bash
cal          # Mes actual
cal -3       # Mes actual + anterior y siguiente
cal 12 2025  # Diciembre de 2025
```

#### Mostrar información del sistema

##### uname

Muestra datos básicos del sistema.

Sintaxis

```bash
uname [OPCIONES]
```

Opciones más útiles:

- -s Nombre del kernel (por defecto si no se indica nada).
- -n Nombre de red del equipo (hostname).
- -r Versión (release) del kernel.
- -v Compilación del kernel.
- -m Arquitectura de la máquina (p. ej., x86_64, aarch64).
- -p Tipo de procesador (puede devolver unknown).
- -i Plataforma de hardware (puede devolver unknown).
- -o Sistema operativo.
- -a Todo en una línea (equivale a combinar varias anteriores).

Ejemplos

```bash
uname        # kernel (equivale a -s)
uname -r     # versión del kernel
uname -a     # resumen completo
```

#### Mostrar nombres del equipo

##### hostname

Muestra (o establece de forma temporal) el nombre del equipo.

Sintaxis

```bash
hostname            # Muestra el nombre actual
sudo hostname NUEVO # Cambia el nombre hasta el próximo reinicio
```

Para cambiar el nombre de forma persistente en sistemas actuales (Lubuntu/Ubuntu con systemd), usa:

```bash
sudo hostnamectl set-hostname NUEVO_NOMBRE
```

#### Histórico de comandos

Escribir comandos largos es propenso a errores. bash guarda un histórico (por defecto suele ser 500 entradas) que permite reutilizar y editar órdenes ya escritas.

Navegación por el histórico:

- Flecha ↑ o Ctrl+P → muestra el comando anterior.
- Flecha ↓ o Ctrl+N → muestra el siguiente (si antes retrocediste).
- Flechas ← / → → editar dentro de la línea mostrada.

Autocompletado (Tab):

- Pulsa Tab para completar rutas/nombres de archivo a partir de lo tecleado.
- Si hay una única coincidencia, completa el nombre (en directorios añade /).
- Si hay varias, completa hasta la parte común; con Tab de nuevo suele listar opciones.

Ver el listado (recordatorio):

- history → muestra el histórico (más detalles en el apartado específico).
