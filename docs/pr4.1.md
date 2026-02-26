# Práctica 4.1 - Gestión de cuentas de usuario y dispositivos en Windows 11

## Descripción de la práctica

Imagina que tu máquina virtual de Windows 11 Pro es el equipo de un aula de informática. El equipo será utilizado por varios alumnos y por el profesor responsable del aula.

El objetivo es preparar el equipo para su uso en un entorno educativo controlado.

## Gestión de cuentas de usuario

**Ejercicio 1. Análisis inicial**

1.	Indica qué tipo de cuenta estás utilizando actualmente (local o Microsoft).
2.	Comprueba si tu cuenta es estándar o administrador.
3.	Explica brevemente por qué no es recomendable trabajar siempre con una cuenta de administrador.

**Ejercicio 2. Creación de cuentas**

Desde Administración de equipos → Usuarios y grupos locales:

1.	Crea una cuenta local con los siguientes datos:
    - Nombre de usuario: alumno_practica
    - Contraseña: Alumno123*
    - El usuario debe cambiar la contraseña en el siguiente inicio de sesión: NO
    - La contraseña nunca expira: SÍ
2.	Crea otra cuenta:
    - Nombre: profesor_practica
    - Contraseña: Profesor123*
    - Añádela al grupo Administradores.
3.	Comprueba que ambas cuentas aparecen en la lista de usuarios.

**Ejercicio 3. Modificación de cuentas**

1.	Cambia el tipo de cuenta de alumno_practica a estándar (si no lo está).
2.	Modifica la contraseña de alumno_practica.
3.	Deshabilita temporalmente la cuenta alumno_practica.
4.	Intenta iniciar sesión con esa cuenta y explica qué ocurre.
5.	Vuelve a habilitarla.

**Ejercicio 4. Eliminación de cuentas**

1.	Elimina la cuenta alumno_practica.
2.	Indica qué opción elegiste respecto a los archivos del usuario (conservar o eliminar).
3.	Explica la diferencia entre deshabilitar y eliminar una cuenta.

## Perfil de usuario

**Ejercicio 5. Ubicación del perfil**

1.	Accede a C:\Users.
2.	Identifica las carpetas correspondientes a los usuarios creados.
3.	Explica qué contiene el perfil de usuario.

**Ejercicio 6. Redirección de carpeta**

1.	Inicia sesión con una cuenta estándar.
2.	Cambia la ubicación de la carpeta Documentos a otra ubicación (por ejemplo, una carpera en el escritorio).
3.	Comprueba que los archivos existentes se han movido.
4.	Explica por qué esta técnica es más segura que mover completamente C:\Users desde el registro.

## Gestión de dispositivos

**Ejercicio 7. Dispositivos e impresoras**

1.	Accede a Panel de control → Hardware y sonido → Dispositivos e impresoras.
2.	Haz una captura o describe:
    - Dispositivos externos conectados.
    - Impresoras instaladas.
3.	Indica qué dispositivos no aparecen en esta ventana y por qué.

**Ejercicio 8. Administrador de dispositivos**

1.	Abre el Administrador de dispositivos.
2.	Localiza:
    - Adaptadores de red.
    - Controladoras de almacenamiento.
    - Dispositivos de interfaz humana.
3.	Comprueba el estado de uno de los dispositivos.
4.	Explica qué indica el apartado “Estado del dispositivo”.

**Ejercicio 9. Gestión de controladores**

1.	Desde un dispositivo cualquiera:
    - Consulta la pestaña Controlador.
    - Indica versión y proveedor.
2.	Comprueba si hay actualizaciones de controladores desde:
    - Configuración → Windows Update → Opciones avanzadas → Actualizaciones opcionales.
3.	Explica qué diferencia hay entre:
    - Controlador.
    - Información del dispositivo.

## Caso práctico de diagnóstico

Un ratón USB deja de funcionar tras conectarlo al equipo.

1.	Indica los pasos que seguirías para diagnosticar el problema.
2.	Comprueba en el Administrador de dispositivos si aparece con advertencia.
3.	Explica qué harías si:
    - No aparece el dispositivo.
    - Aparece con un icono de advertencia.
4.	Describe cómo usarías el solucionador de problemas.

## Entrega

Crea un documento PDF, a partir de un Word o Google Docs, con las siguientes consideraciones:

- El nombre del archivo a entregar en la plataforma Moodle Centros debe tener el siguiente formato: `Apellido1Apellido2_Nombre_SOM_UD4_P1.pdf`.
- Portada con imagen, nombre del alumno, título y curso.
- Encabezado con nombre de la práctica y materia.
- Pie de página con nombre, número de página insertado, curso, año escolar, instituto.
- Índice o tabla de contenidos generada automáticamente.
- Tipo de letra: Times New Roman 12 o similar, interlineado sencillo, espaciado anterior 6p.
- Uso correcto de la ortografía.
- Texto justificado con uso de salto de páginas correcto.
- Enlaces web de referencia cuando se coge información de un sitio web.
- Las fotos que se puedan ver correctamente al ampliarlas y que no ocupen mucho espacio.
- Insertar Título de foto que haga referencia al apartado y ejercicio correspondiente.
- Para las capturas de pantalla de las máquinas virtuales:
    - Se captura todo el escritorio de la máquina virtual donde se pueda leer el nombre de la máquina, con el fondo de su plataforma Moodle, donde se pueda ver imagen de perfil. Toda aquella práctica que no cumpla este requisito no será evaluada.
    - Al igual que en los Títulos de las fotos, en el Título de la captura de pantalla irá referenciado el apartado y ejercicio al que corresponde.