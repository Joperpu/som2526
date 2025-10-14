# Unidad 2 - Creación de un pendrive de arranque con Rufus

Un pendrive booteable es un USB preparado para que el firmware del equipo (UEFI o BIOS) pueda arrancar desde él y cargar un gestor de arranque que, a su vez, inicia un instalador o un sistema “Live” (arranca sin instalar, típico en GNU/Linux).

¿Qué ocurre al pulsar el botón de encendido?

1. Firmware (UEFI/BIOS) busca el primer dispositivo arrancable según el orden de arranque (Boot Order).
2. Si es UEFI:
    - Lee la Partición del Sistema EFI (ESP) del USB (normalmente FAT32) y ejecuta un fichero .efi (p. ej., \EFI\BOOT\BOOTX64.EFI).
3. Si es BIOS/Legacy:
    - Carga el MBR del dispositivo (sector 0) y salta al código del cargador allí contenido.
4. El gestor de arranque (GRUB, Windows Boot Manager, Syslinux, Ventoy…) muestra un menú o lanza directamente el instalador/Live.

ISO, “Live” e instalador:

- Una ISO es una imagen del medio de instalación (antes CD/DVD). Muchas ISOs modernas son híbridas (arrancan tanto en BIOS como en UEFI).
- Modo Live (Linux): el sistema se ejecuta desde la RAM/USB sin tocar el disco.
- Persistencia (opcional): permite guardar cambios entre reinicios (archivos, paquetes, configuración).
- Instalador: guía para particionar, copiar el sistema y configurar el arranque en el disco interno.

## Rufus

Rufus es una utilidad para formatear y crear USB de arranque (pendrives, tarjetas de memoria, etc.) de forma rápida y segura.

Cuándo usar Rufus:

- Crear medios de instalación a partir de ISOs arrancables (Windows 10/11, Ubuntu/Debian/Fedora, utilidades UEFI, etc.).
- Soporta UEFI y BIOS/Legacy, GPT/MBR y maneja ISOs “grandes”: si algún archivo supera 4 GB, puede usar UEFI:NTFS para arrancar en UEFI aunque el USB esté en NTFS.
- Poner en marcha equipos sin sistema operativo, iniciando directamente un instalador o un sistema Live de Linux.
- Ejecutar utilidades de bajo nivel (diagnóstico, clonado, antivirus offline, gestores de particiones, MemTest, etc.).
- Actualizar firmware/BIOS desde DOS (FreeDOS) cuando el fabricante lo exige en equipos antiguos o herramientas legadas.

### Creación de un USB booteable de Windows 11

#### Con Rufus

Descargamos la última versión de Rufus desde su [página web](https://rufus.ie/es/) y la ejecutamos. En la ventana del programa podemos ver multitud de opciones para crear nuestro USB booteable. Seleccionamos la ISO que deseemos, en nuestro caso la de Windows 11, y hacemos clic ene l botón *Empezar*.

![Rufus](assets/images/ud2/img109.png)

A continuación, al detectar que se trata de una instalación de Windows seremos preguntados por diversas opciones. Marcamos las mismas que se muestran en la siguiente imagen y hacemos clic en el botón *Ok*.

![Rufus](assets/images/ud2/img110.png)

El programa comenzará a copiar archivos y nos informará cuando finalice.

##### Windows To Go

Rufus también nos permite crear un USB booteable con *Windows To Go*. Esta opción nos permite arrancar un sistema operativo Windows desde el pendrive sin necesidad de instalarlo (de la misma forma que algunas distribuciones GNU/Linux funcionan en modo *live*). Para ello, después de seleccionar la imagen de Windows 11 indicamos en el desplegable *Opciones de imagen* la opción de *Windows To Go*.

![Rufus](assets/images/ud2/img111.png)

En teste punto Rufus nos preguntará sobre la versión de Windows 11 que queremos utilizar y otras preguntas acerca de la instalación del SO.

![Rufus](assets/images/ud2/img112.png)
![Rufus](assets/images/ud2/img113.png)


#### Con el creador de medios de Windows 11

### Creación de un USB booteable de Linux

De la misma forma que hicimos con la ISO de Windows 11 seleccionamos la de Ubuntu y hacemos clic en el botón *Empezar*. Seremos preguntados acerca del modo de imagen, para lo que seleccionamos la opción recomendada y hacemos clic en *Ok*.

![Rufus](assets/images/ud2/img114.png)
![Rufus](assets/images/ud2/img115.png)

## Ventoy

