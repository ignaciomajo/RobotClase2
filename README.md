# Rocketbot :rocket: - Clasificación de clientes

![rpa_excel](https://github.com/user-attachments/assets/c3b66107-ca77-4e0d-a534-f27053b96409)

## Índice 📋

1. Descripción del proyecto.
2. Acceso al proyecto
3. Demostración del funcionalidades y aplicaciones.
4. Tecnologías utilizadas.
5. Colaboradores.
6. Desarrollador del proyecto.

## 1. Descripción del proyecto 📚

Este proyecto permite observar las ventajas de automatizar un proceso de data manipualtion con tencología RPA (Robot Process Automation), en particular **Rocketbot** 🚀. En él, se puede ver como es posible acceder a un archivo `.xlsx` que buscamos analizar, y manipular los datos contenidos en este, recorriendo cada registro y, en este caso, hacer una clasificación de clientes dependiendo de su condición impositiva.
Por supuesto las cantidad de acciones aplicables a nuestros datos en un archivo `.xlsx` es extensa, en este caso solo se dará este ejemplo para demostrar como funciona el proceso de RPA.

## 2. Acceso al proyecto 📂

Para obtener el proyecto tienes dos opciones:

1. Clonar el repositorio utilizando la línea de comandos. Solo debes dirigirte al directorio donde deseas clonar el mismo e ingresar el comando:
   `git clone https://github.com/ignaciomajo/RobotClase2`

2. O puedes descargarlo directamente desde el repositorio en GitHub en el siguiente enlace:
   <p><a href="https://github.com/ignaciomajo/RobotClase2">https://github.com/ignaciomajo/RobotClase2</p>

   Esto te llevará a la siguiente pantalla, donde deberás seguir los siguientes pasos:
   
![image](https://github.com/user-attachments/assets/298a8a20-b727-45cc-add5-41d43055d60a)

Esto descargará un archivo comprimido `.zip`, que podras alojar en el directorio que desees.


## 3. Demostración de funcionalidades y aplicaciones 📝

Una vez hayamos descargado o clonado el repositorio completo, encontraremos la carpeta **main**📁, y dentro de esta, el siguiente conjunto de archivos y carpetas:

![carpeta_main](https://github.com/user-attachments/assets/e3426b89-d0c5-4fc9-b09d-06c97a540e93)

* *Logs* 📁: La carpeta `logs` contiene el registro de todos los logs del robot, cada acción realizada por el mismo quedara almacenada en un archivo `.txt` dentro de esta carpeta.

* *main* 💾: El archivo bash llamado `main` es el que permite poner el robot en producción, para esto se necesita una licencia paga proporcionada por Rocketbot. Puedes consultar el siguiente enlace: <p><a href="https://rocketbot.com/es/pricing-desktop-rpa/">https://rocketbot.com/es/pricing-desktop-rpa/</p>

* *robot.db* 🤖: El archibo `robot.db` es la base de datos SQLite que contiene las automatizaciones desarrolladas dentro del proyecto. Este será el archivo que deberemos cargar a Rocketbot Studio. *Nota: se verá más adelante*

* *resources* 📁: La carpeta `resources` contendrá los archivos que vemos a continuación.

Esta, contiene cuatro archivos:

**1. clasificacion_clientes 📊**

Este es el output del robot, archivo que contiene las distintas hojas de cálculo con los clientes clasificados según su condición frente al IVA

**2. Archivo `config.ini` 🔧:**

![config.ini](https://github.com/user-attachments/assets/4f8d183e-9104-461e-bbb8-0cb2c7f09133)


Este, contiene algunas configuraciones iniciales para el robot.

En la sección `[paths]` están definidas las rutas donde el robot buscará y/o guardará los archivos generados por el mismo o necesarios para su ejecución:

*Nota: en todas las instancias es necesario cambiar la ruta hacia donde está alojado el robot en tu computadora*

`path_git` nos dirige hacia la carpeta inicial `main` 📁 que fue mostrada anteriormente.<br><br>
`path_log` es una ruta destinada a la creación de un custom log aparte del que genera el mismo robot, ya que este suele tener demasiada información. Contiene también la extensión `.txt` para el formato en el que se guardará el archivo.<br><br>
`path_archivo` es la ruta utilizada para abrir el archivo inicial con el que debemos trabajar. En caso utilizar una planilla de Excel propia, será necesario tener el archivo dentro de la carpeta resources, y solo se deberá cambiar la última instancia del path `C:/Users/TuUsuario/CarpetaDelRobot/RobotClase2/main/resources/NombreDeTuArchivo.xlsx`<br><br>

Sección `[clasificacion_clientes`:

En este caso, los parámetros definidos representan dos cosas:

* El criterio de clasificación por el que serán divididos los clientes de la hoja inicial.
* El nombre que tendran las distintas Hojas donde quedarán almacenados los clientes, representando la clasificación correspondiente

**3. log** 📄

Archivo con logs sencillos y fáciles de leer para una rápida interpretación de lo sucedido en el proceso.

**4. Planilla de facturacion - ACONCAGUA 02-2025 📊**

Este es el archivo sobre el cual el robot estará trabajando inicialmente. Debe mantenerse dentro de la carpeta `resources`.


#### Ahora veremos la ejecución dentro de Rocketbot Studio 🚀


