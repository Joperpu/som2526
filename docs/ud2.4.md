# Unidad 2 - Instalación de una máquina virtual dual

Al trabajar con máquinas virtuales, es posible instalar más de un sistema operativo en un mismo entorno, creando lo que se conoce como un sistema dual. Una de las combinaciones más habituales es contar con Windows y Linux en la misma máquina, lo que permite aprovechar las ventajas de ambos sistemas según las necesidades del usuario.

Para evitar problemas con el arranque y la gestión del gestor de inicio, es recomendable instalar primero Windows y posteriormente Linux. Esto se debe a que el instalador de Windows sobrescribe el gestor de arranque existente, mientras que las distribuciones Linux, mediante GRUB, detectan automáticamente otros sistemas instalados y permiten seleccionarlos en el inicio.

En los siguientes apartados veremos, paso a paso, cómo crear una máquina virtual con un entorno dual Windows/Linux de forma sencilla y segura.

## Proceso de instalación

El primer paso será crear una máquina virtual con Windows 11 ya creada, o clonar una ya existente. Si deseamos clonarla lo podemos hacer desde el propio VirtualBox. Para ello, seleccionamos la máquina virtual de Windows 11, hacemos clic derecho en ella -> *Clonar*.

[Clonar](assets/images/ud2/img74.png)

Introducimos el nombre de la nueva máquina, dejamos el resto de parámetros tal y como se nos muestran y hacemos clic en *Terminar*. De esta forma comenzará el proceso de clonación de la máquina, el cual puede durar varios minutos.

[Clonar](assets/images/ud2/img75.png)

Una vez clonada deberemos añadir a la unidad óptica la ISO de Lubuntu 24.04. Para ello, Para ello, seleccionamos la máquina virtual dual, hacemos clic derecho en ella -> *Configuración*. A continuación, hacemos clic en *Almacenamiento* y seleccionamos la unidad óptica de nuestra máquina virtual. Hacemos clic en el botón del CD azul y podremos seleccionar la imagen ISO de Lubuntu. 

[Clonar](assets/images/ud2/img76.png)

Seguidamente, hacemos clic en el apartado *Sistema* del menú izquierdo y desmarcamos la opción *UEFI*. Hacemos clic en el botón *Aceptar* e iniciamos nuestra máquina virtual dual.

[Clonar](assets/images/ud2/img77.png)

Puesto que en el orden de arranque de la configuración BIOS la unidad óptica se encuentra por encima del disco duro, la máquina virtual arrancará desde la ISO de Lubuntu.

[Clonar](assets/images/ud2/img78.png)

Realizamos la instalación de Lubuntu tal y como hicimos anteriormente, hasta llegar al paso de selección de particiones. En este punto, y ya que queremos crear un sistema dual Windows-Linux, debemos respetar las particiones de Windows y no instalar Lubuntu en todo el disco.

