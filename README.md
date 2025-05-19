Ir al contenido principal
Conéctate, escribe código y crece
Microsoft Build · 19–22 de may de 2025

Learn
Iniciar sesión
Windows
Buscar
Filtrar por título
Documentación de WPF
Instalación de WSL
Pasos de la instalación manual para versiones anteriores
Instalar en Windows Server
Preguntas más frecuentes
Solucionar problemas
Learn  Windows  Entorno de desarrollo  WSL 
Pasos de instalación manual para versiones anteriores de WSL
Artículo
05/12/2023
13 colaboradores
En este artículo
Paso 1: Habilitación del Subsistema de Windows para Linux
Paso 2: comprobación de los requisitos para ejecutar WSL 2
Paso 3: Habilitación de la característica Máquina virtual
Paso 4: Descarga del paquete de actualización del kernel de Linux
Mostrar 5 más
Por motivos de simplicidad, por lo general se recomienda usar wsl --install para instalar el Subsistema de Windows para Linux, pero si ejecuta una compilación anterior de Windows, es posible que no se admita. Hemos incluido los pasos de instalación manual a continuación. Si experimenta un problema durante el proceso de instalación, consulte la sección de instalación de la guía de solución de problemas.

Paso 1: Habilitación del Subsistema de Windows para Linux
Antes de instalar distribuciones de Linux en Windows, debe habilitar la característica opcional "Subsistema de Windows para Linux".

Abra PowerShell como administrador (menú Inicio > PowerShell > haga clic con el botón derecho en > Ejecutar como administrador) y escriba este comando:

PowerShell

Copiar
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
Ahora se recomienda continuar con el paso 2, Actualización a WSL 2, pero si solo quiere instalar WSL 1, ahora puede reiniciar el equipo y dirigirse al Paso 6: Instalación de la distribución de Linux que quiera. Para actualizar a WSL 2, espere para reiniciar la máquina y continúe con el paso siguiente.

Paso 2: comprobación de los requisitos para ejecutar WSL 2
Para actualizar a WSL 2, debe ejecutar Windows 10...

Para sistemas x64: versión 1903 o posterior, con la compilación 18362.1049 o posterior.
Para sistemas ARM64: versión 2004 o posterior, con la compilación 19041 o posterior.
o Windows 11.

 Nota

Las compilaciones anteriores a 18362 no admiten WSL 2. Use el Asistente para Windows Update para actualizar su versión de Windows. La compatibilidad con Windows versión 1903 también es solo para sistemas x64. Si usa una versión arm64 de Windows, deberá actualizar a Windows 10 versión 2004 o posterior para obtener acceso completo a WSL 2. Para obtener más información, consulta compatibilidad con WSL 2 que viene a Windows 10 versiones 1903 y 1909.

Para comprobar la versión y el número de compilación, seleccione la tecla del logotipo de Windows + R, escriba winver y seleccione Aceptar. Actualice a la versión más reciente de Windows en el menú Configuración.

 Nota

Si está ejecutando Windows 10, versión 1903 o 1909, abra "Configuración" en el menú de Windows, vaya a "Actualización y seguridad" y seleccione "Buscar actualizaciones". El número de compilación debe ser 18362.1049 o posterior o 18363.1049 o posterior, con la compilación secundaria posterior a .1049. Leer más: La compatibilidad con WSL 2 estará disponible en breve para las versiones 1903 y 1909 de Windows 10.

Paso 3: Habilitación de la característica Máquina virtual
Antes de instalar WSL 2, debe habilitar la característica opcional Plataforma de máquina virtual. La máquina necesitará funcionalidades de virtualización para usar esta característica.

Abre PowerShell como administrador y ejecuta:

PowerShell

Copiar
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
Reinicia la máquina para completar la instalación de WSL y la actualización a WSL 2.

Paso 4: Descarga del paquete de actualización del kernel de Linux
El paquete de actualización del kernel de Linux instala la versión más reciente del kernel de Linux de WSL 2 para ejecutar WSL dentro de la imagen del sistema operativo Windows. (Para ejecutar WSL desde Microsoft Store, con actualizaciones insertadas con más frecuencia, use wsl.exe --install o wsl.exe --update).

Descargue la versión más reciente:

Paquete de actualización del kernel de Linux en WSL 2 para máquinas x64
 Nota

Si estás usando una máquina ARM64, descarga el paquete ARM64 en su lugar. Si no está seguro de qué tipo de máquina tiene, abra el símbolo del sistema o PowerShell y escriba: systeminfo | find "System Type". Advertencia: En versiones de Windows que no están en inglés, es posible que tenga que modificar el texto de búsqueda, traduciendo la cadena "System Type" (Tipo de sistema). Es posible que también tenga que escapar las comillas del comando find. Por ejemplo, en alemán, systeminfo | find '"Systemtyp"'.

Ejecuta el paquete de actualización que descargaste en el paso anterior. (Haga doble clic para ejecutarlo. Se le pedirán permisos elevados. Seleccione "Sí" para aprobar esta instalación).

Una vez completada la instalación, vaya al paso siguiente: configuración de WSL 2 como versión predeterminada al instalar nuevas distribuciones de Linux. (Omita este paso si quiere que las nuevas instalaciones de Linux se establezcan en WSL 1).

 Nota

Para obtener más información, consulta el artículo cambios en la actualización del kernel de Linux en WSL2, disponible en el blog de la línea de comandos de Windows.

Paso 5: Definición de WSL 2 como versión predeterminada
Abra PowerShell y ejecute este comando para establecer WSL 2 como versión predeterminada al instalar una nueva distribución de Linux:

PowerShell

Copiar
wsl --set-default-version 2
Paso 6: Instalación de la distribución de Linux que quiera
Abre Microsoft Store y selecciona tu distribución de Linux favorita.

Vista de las distribuciones de Linux en Microsoft Store

En los vínculos siguientes se abrirá la página de Microsoft Store para cada distribución:

Ubuntu 18.04 LTS
Ubuntu 20.04 LTS
Ubuntu 22.04 LTS
OpenSUSE Leap 15.1
SUSE Linux Enterprise Server 12 SP5
SUSE Linux Enterprise Server 15 SP1
Kali Linux
Debian GNU/Linux
Fedora Remix for WSL
Pengwin
Pengwin Enterprise
Alpine WSL
Raft (prueba gratuita)
Alma Linux
En la página de la distribución, selecciona "Obtener".

Distribuciones de Linux en Microsoft Store

La primera vez que inicies una distribución de Linux recién instalada, se abrirá una ventana de la consola y se te pedirá que esperes un minuto o dos para que los archivos se descompriman y se almacenen en tu equipo. Todos los inicios posteriores deberían tardar menos de un segundo en completarse.

Tendrás que crear una cuenta de usuario y una contraseña para la nueva distribución de Linux.

Desempaquetado de Ubuntu en la consola de Windows

¡ENHORABUENA! Ha instalado y configurado correctamente una distribución de Linux completamente integrada con el sistema operativo Windows.

Solución de problemas de instalación
Si experimenta un problema durante el proceso de instalación, consulte la sección de instalación de la guía de solución de problemas.

Descarga de distribuciones
Hay varios escenarios en los que quizás no pueda (o no quiera) instalar distribuciones de Linux de WSL a través de Microsoft Store. Es posible que esté ejecutando una SKU de sistema operativo de escritorio de Windows Server o de mantenimiento a largo plazo (LTSC) que no sea compatible con Microsoft Store, o que sus administradores o directivas de red corporativa no permitan el uso de Microsoft Store en su entorno. En estos casos, aunque WSL esté disponible, es posible que tenga que descargar las distribuciones de Linux directamente.

Si la aplicación Microsoft Store no está disponible, puede descargar e instalar manualmente distribuciones de Linux a través de estos vínculos:

Ubuntu
Ubuntu 24.04
Ubuntu 22.04 LTS
Ubuntu 20.04
Ubuntu 20.04 ARM
Ubuntu 18.04
Ubuntu 18.04 ARM
Ubuntu 16.04
Debian GNU/Linux
Kali Linux
SUSE Linux Enterprise Server 12
SUSE Linux Enterprise Server 15 SP2
SUSE Linux Enterprise Server 15 SP3
openSUSE Tumbleweed
openSUSE Leap 15.3
OpenSUSE Leap 15.2
Oracle Linux 8.5
Oracle Linux 7.9
Fedora Remix for WSL
Al hacerlo, los paquetes de <distro>.appx se descargarán en una carpeta de tu elección.

Si lo prefiere, también puede descargar sus distribuciones preferidas a través de la línea de comandos y puede usar PowerShell con el cmdlet Invoke-WebRequest. Por ejemplo, para descargar Ubuntu 20.04:

PowerShell

Copiar
Invoke-WebRequest -Uri https://aka.ms/wslubuntu2004 -OutFile Ubuntu.appx -UseBasicParsing
 Sugerencia

Si la descarga tarda mucho tiempo, establece $ProgressPreference = 'SilentlyContinue' para desactivar la barra de progreso.

También tiene la opción de usar la utilidad de línea de comandos curl para la descarga. Para descargar Ubuntu 20.04 con curl:

Consola

Copiar
curl.exe -L -o ubuntu-2004.appx https://aka.ms/wslubuntu2004
En este ejemplo, se ejecuta curl.exe (no solo curl) para garantizar que, en PowerShell, se invoque el ejecutable de curl real, no el alias de curl de PowerShell para Invoke-WebRequest.

Una vez descargada la distribución, vaya a la carpeta que contiene la descarga y ejecute el siguiente comando en ese directorio, donde app-name es el nombre del archivo .appx de la distribución de Linux.

Powershell

Copiar
Add-AppxPackage .\app_name.appx
Una vez que el paquete Appx haya terminado de descargarse, puede empezar a ejecutar la nueva distribución haciendo doble clic en el archivo appx. (El comando wsl -l no mostrará que la distribución está instalada hasta que se complete este paso).

Si usa Windows Server, o tiene problemas para ejecutar el comando anterior, puede encontrar instrucciones de instalación alternativas en la página de la documentación de Windows Server para instalar el archivo .appx cambiándolo a un archivo zip.

Una vez instalada la distribución, siga las instrucciones para crear una cuenta de usuario y una contraseña para la nueva distribución de Linux.

Instalación de Terminal Windows (opcional)
Terminal Windows permite abrir varias pestañas o varios paneles para mostrar y cambiar rápidamente entre varias distribuciones de Linux u otras líneas de comandos (PowerShell, símbolo del sistema, PowerShell, CLI de Azure, etc.). Puede personalizar completamente el terminal con combinaciones de colores únicas, estilos de fuente, tamaños, imágenes de fondo y métodos abreviados de teclado personalizados. Más información.

Instalación de Terminal Windows.

Terminal Windows

 Colaborar con nosotros en GitHub
El origen de este contenido se puede encontrar en GitHub, donde también puede crear y revisar problemas y solicitudes de incorporación de cambios. Para más información, consulte nuestra guía para colaboradores.

Comentarios de Windows Subsystem for Linux

Windows Subsystem for Linux es un proyecto de código abierto. Selecciona un vínculo para proporcionar comentarios:

 Abrir incidencia con la documentación
 Enviar comentarios del producto
Recursos adicionales
Eventos

Únete al desafío del AI Skills Fest

8 abr, 10 a.m. - 28 may, 2 a.m.

Perfecciona tus habilidades de IA y participa en el sorteo para ganar un examen de certificación gratuito

¡Regístrese ahora!
Formación

Módulo

Desarrollo en el Subsistema de Windows para Linux con Visual Studio Code - Training

En este módulo, aprenderá a usar el Subsistema de Windows para Linux (WSL) con Visual Studio Code (VS Code). Exploraremos el proceso de instalación y los conceptos básicos del uso del WSL. Además, instalaremos y utilizaremos la extensión WSL de Visual Studio Code. Por último, mostraremos cómo depurar y ejecutar código de Python en VS Code en nuestro entorno de WSL.

Documentación

Pasos de instalación manual para versiones anteriores de WSL

Instrucciones paso a paso para instalar manualmente WSL en versiones anteriores de Windows, en lugar de usar el comando wsl install.

Solución de problemas del subsistema de Windows para Linux

Proporciona información detallada sobre los errores comunes y los problemas que se producen al ejecutar Linux en el Subsistema de Windows para Linux.

Instalación del subsistema Linux en Windows Server

Obtenga información sobre cómo instalar el subsistema Linux en Windows Server. WSL está disponible para su instalación en Windows Server 2019 (versión 1709) y versiones posteriores.

Mostrar 5 más
Versiones anteriores
Blog
Colaborar
Privacidad
Términos de uso
Marcas comerciales
© Microsoft 2025