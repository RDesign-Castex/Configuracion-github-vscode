# Configuración de Git y GitHub en macOS

Este documento te guiará paso a paso para configurar Git y GitHub en tu computadora macOS. Git es un sistema de control de versiones ampliamente utilizado, mientras que GitHub es una plataforma de alojamiento de repositorios remotos y colaboración en proyectos.

## Paso 1: Instalación de Git

Si aún no tienes Git instalado en tu Mac, puedes descargarlo e instalarlo desde el sitio web oficial de Git (https://git-scm.com/). Descarga la versión adecuada para macOS y sigue las instrucciones del instalador.

## Paso 2: Configuración de Git

Abre la terminal en tu Mac. Puedes encontrarla en la carpeta "Utilidades" dentro de la carpeta "Aplicaciones" o usar el atajo de teclado `Cmd + Espacio` para abrir Spotlight y buscar "Terminal".

### 2.1 Configura tu nombre de usuario

Ejecuta el siguiente comando para configurar tu nombre de usuario en Git. Reemplaza "Tu Nombre" con tu nombre real entre comillas:


git config --global user.name "Tu Nombre"

### 2.2 Configura tu dirección de correo electrónico
Ejecuta el siguiente comando para configurar tu dirección de correo electrónico asociada con tu cuenta de GitHub. Asegúrate de utilizar la misma dirección de correo electrónico que usaste para registrarte en GitHub:

git config --global user.email "tuemail@example.com"


### 2.3 Configura las opciones de formato
Si deseas que Git conserve los cambios de línea en tus archivos tal como los has escrito en tu editor, ejecuta el siguiente comando:

git config --global core.autocrlf input

Este comando asegura que los cambios de línea se conviertan en LF (Unix-style) en lugar de CRLF (Windows-style) cuando interactúas con repositorios remotos.

### 2.4 Verifica tu configuración
Para asegurarte de que tu configuración se haya realizado correctamente, puedes verificarla ejecutando:

git config --global --list

Esto mostrará una lista con tus configuraciones globales.

## Paso 3: Configuración de autenticación en GitHub
Para interactuar con repositorios remotos en GitHub, necesitarás autenticarte. GitHub admite tanto la autenticación mediante usuario y contraseña como mediante un token de acceso personal. Recomendamos el uso de tokens de acceso personal, ya que son más seguros.

### 3.1 Genera un token de acceso personal
Inicia sesión en tu cuenta de GitHub.
Haz clic en tu perfil de usuario en la esquina superior derecha y selecciona "Configuración" en el menú desplegable.
En el panel izquierdo, selecciona "Developer settings", y luego "Personal access tokens".
Haz clic en "Generate new token".
Asigna un nombre descriptivo para el token, selecciona los alcances (scopes) que necesitas (por ejemplo, "repo" para repositorios) y define una fecha de expiración si lo deseas.
Haz clic en "Generate token".
Importante: Copia y guarda el token en un lugar seguro, ya que no se mostrará nuevamente.
### 3.2 Configura el token en Git
De vuelta en la terminal, ejecuta el siguiente comando para configurar tu token de acceso personal en Git. Reemplaza TU_TOKEN con el token que copiaste en el paso anterior:

git config --global credential.helper store
git credential-store --file ~/.git-credentials store

Al ejecutar estos comandos, se almacenará tu token de acceso personal en un archivo seguro y Git lo usará automáticamente para la autenticación en GitHub.

## Paso 4: Verificación de la configuración
Ahora que has configurado Git y GitHub en tu Mac, puedes verificar si todo está en orden.

### 4.1 Verifica tu conexión a GitHub
Ejecuta el siguiente comando para verificar que tu configuración y autenticación sean correctas:

ssh -T git@github.com

Si todo está bien, recibirás un mensaje de saludo desde GitHub.


## 4.2 Crea un repositorio de prueba
Para probar la configuración, puedes crear un repositorio de prueba directamente desde la terminal:

mkdir repositorio-prueba
cd repositorio-prueba
echo "# Repositorio de prueba" >> README.md
git init
git add README.md
git commit -m "Primer commit"
git remote add origin https://github.com/tu-usuario/repositorio-prueba.git
git push -u origin master

Reemplaza tu-usuario con tu nombre de usuario de GitHub. Si todo funciona correctamente, deberías ver el archivo README.md en tu repositorio de GitHub.

¡Listo! Ahora tienes Git y GitHub configurados en tu Mac. Puedes comenzar a utilizar Git para controlar las versiones de tus proyectos y colaborar con otros desarrolladores en GitHub. ¡Diviértete codificando! 🚀