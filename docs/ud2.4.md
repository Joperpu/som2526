# Unidad 2 - Instalación de una máquina virtual dual

Al trabajar con máquinas virtuales, es posible instalar más de un sistema operativo en un mismo entorno, creando lo que se conoce como un sistema dual. Una de las combinaciones más habituales es contar con Windows y Linux en la misma máquina, lo que permite aprovechar las ventajas de ambos sistemas según las necesidades del usuario.

Para evitar problemas con el arranque y la gestión del gestor de inicio, es recomendable instalar primero Windows y posteriormente Linux. Esto se debe a que el instalador de Windows sobrescribe el gestor de arranque existente, mientras que las distribuciones Linux, mediante GRUB, detectan automáticamente otros sistemas instalados y permiten seleccionarlos en el inicio.

En los siguientes apartados veremos, paso a paso, cómo crear una máquina virtual con un entorno dual Windows/Linux de forma sencilla y segura.

## Proceso de instalación

El primer paso será crear una máquina virtual con Windows 11 ya creada, o clonar una ya existente. Si deseamos clonarla lo podemos hacer desde el propio VirtualBox. Para ello, seleccionamos la máquina virtual de Windows 11, hacemos clic derecho en ella -> *Clonar*.

![Clonar](assets/images/ud2/img74.png)

Introducimos el nombre de la nueva máquina, dejamos el resto de parámetros tal y como se nos muestran y hacemos clic en *Terminar*. De esta forma comenzará el proceso de clonación de la máquina, el cual puede durar varios minutos.

![Clonar](assets/images/ud2/img75.png)

![Clonar](assets/images/ud2/img76.png)

![Clonar](assets/images/ud2/img77.png)

Una vez clonada debemos eliminar el cifrado del disco que por defecto crea Windows 11. Para ello iniciamos la máquina virtual que acabamos de clonar y abrimos la terminal *Powershell* como administrador.

![Powershell](assets/images/ud2/img78.png)

Procedemos ahora a descifrar el disco para lo que ejecutamos el siguiente comando:

```
Disable-BitLocker -MountPoint "C:"
```

![Powershell](assets/images/ud2/img79.png)

![Powershell](assets/images/ud2/img80.png)

Este proceso tardará unos minutos. Podemos comprobar el estado ejecutando el comando:

```
manage-bde -status
```

![Powershell](assets/images/ud2/img81.png)

![Powershell](assets/images/ud2/img82.png)

Una vez finalizado este proceso procedemos a apagar la máquina virtual y accedemos a la configuración de esta. Nos dirigimos a *Almacenamiento*, seleccionamos la unidad óptica y hacemos clic en el disco azul para seleccionar la imagen de Ubuntu. Si no la tenemos descargada previamente lo podemos hacer desde su [página oficial de descargas](https://ubuntu.com/download/desktop).

![Dual](assets/images/ud2/img83.png)

Hacemos clic en *Aceptar* y arrancamos nuestra máquina. 

![Dual](assets/images/ud2/img84.png)

Ahora debemos entrar en el Boot Manager de la máquina virtual, para ello, debemos pulsar *Escape* varias veces justo en el momento en el que se inicie esta. En este punto seleccionamos la opción *Boot Maintenance Manager* y pulsamos aceptar.

![Dual](assets/images/ud2/img85.png)

![Dual](assets/images/ud2/img86.png)

En el menú que se nos muestra deberemos seleccionar la opción de *UEFI VBOX CD* y pulsar *Enter*.

![Dual](assets/images/ud2/img87.png)

A continuación, pulsamos *Escape* para salir de esta configuración, y seguidamente pulsamos *Y*, para confirmar los cambios.

![Dual](assets/images/ud2/img88.png)

![Dual](assets/images/ud2/img89.png)

Finalmente, nos desplazamos hasta la opción *Reset* y pulsamos *Enter*.

![Dual](assets/images/ud2/img90.png)

En este punto, la máquina se quedará en negro. Hacemos clic en cerrar la ventana y apagamos la máquina virtual.

![Dual](assets/images/ud2/img91.png)

![Dual](assets/images/ud2/img92.png)

Volvemos a iniciar la máquina virtual y esta arrancará desde la ISO de Ubuntu. Seleccionamos la opción de *Try or Install Ubuntu* y pulsamos *Enter*.

![Dual](assets/images/ud2/img93.png)

Seguidamente se mostrará el asistente de instalación de Ubuntu. Seguimos los pasos tal y como se indica en las siguientes imágenes:

![Dual](assets/images/ud2/img94.png)
![Dual](assets/images/ud2/img95.png)
![Dual](assets/images/ud2/img96.png)
![Dual](assets/images/ud2/img97.png)
![Dual](assets/images/ud2/img98.png)
![Dual](assets/images/ud2/img99.png)
![Dual](assets/images/ud2/img100.png)
![Dual](assets/images/ud2/img101.png)
![Dual](assets/images/ud2/img102.png)

En el siguiente paso del asistente seremos preguntados sobre  cómo queremos instalar Ubuntu. Seleccionamos la opción de *Instalar Ubuntu junto a Windows Boot Manager* y hacemos clic en siguiente.

![Dual](assets/images/ud2/img103.png)

Seleccionamos el tamaño que queremos en nuestra instalación de Ubuntu y hacemos clic en *Siguiente*. Es importante señalar en este punto que todo aquel tamaño que asignemos será recortado de la instalación de Windows, ya que están usando el mismo "disco duro".

![Dual](assets/images/ud2/img104.png)

Continuamos con el resto de pasos del asistente de instalación.

![Dual](assets/images/ud2/img105.png)
![Dual](assets/images/ud2/img106.png)
![Dual](assets/images/ud2/img107.png)
![Dual](assets/images/ud2/img108.png)

Una vez finalice la instalación, reiniciamos y arrancará la máquina mostrando el menú de Grub, el gestor de arranque más utilizado en sistemas GNU/Linux, el cual nos dejará seleccionar entre iniciar Ubuntu o Windows (entre otras opciones).

<!-- Falta imagen -->