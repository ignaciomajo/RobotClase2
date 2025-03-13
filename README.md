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

Una vez abierto Rocketbot Studio:

![upload_db](https://github.com/user-attachments/assets/c0b82aab-74c6-4e61-954c-aa13e1a1fb35)


Presionamos en la casilla marcada con un recuadro rojo, y cargamos el archivo `robot.db` mencionado anteriormente.

Al seleccionar el proyecto, se abrirá la siguiente pantalla donde figuran todos los robots dentro de la base de datos cargada, aquí deberemos seleccionar **Facturacion**.

![robots_db](https://github.com/user-attachments/assets/8f4acb1f-9488-470d-9987-8ce7e57b4311)

Esto nos dirigirá a la siguiente instancia:

![pantalla_inicial](https://github.com/user-attachments/assets/01d2eaca-4692-434d-ba01-432fcb8bd08a)

Esta es la pantalla inicial una vez ingresamos al menú del robot. Para ejecutarlo, solo debemos presionar el botón marcado en un recuadro rojo que dice **Run**. Este ejecutará el robot con las variables predeterminadas.

A su vez, podemos visualizar las disintas agrupaciones de comandos encerradas en un recuadro azul. Esto puede considerarse como "bloques" que generalizan las acciones ejecutadas por el robot en cada uno de ellos y su orden. Esto nos permite entender la lógica que sigue el robot y ofrece un facilidad para su lectura.

Cuando existen pasos dentro de otro, vemos como se produce una pequeña indentación en el panel, y el contador empieza desde el número 1 nuevamente, esto nos dice que dichos pasos, son *hijos* de un paso *padre*. Esto es de suma importancia para poder entender como el robot ejecuta cada actividad.

En este caso, el robot está diseñado para separar registros de una planilla de `Excel` según el valor de una columna *(Condición de IVA)* y generar una hoja dentro del archivo para cada una de las clasificaciones existentes.

![planilla_inicial](https://github.com/user-attachments/assets/e53d9383-eb00-4ac3-9ef1-f8148df87da5)

Y copiará el encabezado y los formatos de celda en cada hoja creada:

![encabezados](https://github.com/user-attachments/assets/8c1953f9-925f-47fd-95de-374e2caae1d4)

Una vez realizado esto, el robot irá leyendo registro por registro, obteniendo el valor correspondiente a la columna mencionada anteriormente, y llevará dicho registro a la hoja que corresponda a dicha clasificación, como se puede ver en el siguiente ejemplo:

![clasificacion](https://github.com/user-attachments/assets/94fa941e-daf2-43ad-8b6f-9c606855a7c1)

Cuando el proceso agrupado en `Data Manipulation` haya terminado, se eliminará la hoja inicial (ya que esta la tenemos en un archivo separado, el cual fue utilizado para comenzar a trabajar) y solo conservará las hojas resultantes con los clientes clasificados en su correspondiente hoja de acuerdo a la columna seleccionada.

![eliminacion_hoja](https://github.com/user-attachments/assets/24d5ba42-09f9-47f0-a7f0-1fa056913ab7)

Finalmente, como se mencionó anteriormente, podremos ver el archivo resultante *(output)* en la carpeta `resources` 📁 con el nombre de `clasificacion_clientes.xlsx` 📊

## 4. Tecnologías utilizadas 🛠️

* `Rocketbot Studio (v.2025.01.06)`
* `Git and GitHub`
* `Microsoft Excel` (requerido para ejecutar el robot)
* `Python`
* ``

## 5. Colaboradores del proyecto 🏗️

Quiero agradecer a:

![BotSolutions](https://github.com/user-attachments/assets/4dda0262-5b97-4b60-a692-db5aa7825d4b)

#### BotSolutions

Por la capacitación en la herramienta y en la oportunidad de aprender de la mano de ellos.

------------------------------------------------------------------------------------------------------
![Rocketbot](https://github.com/user-attachments/assets/5e61e12c-8fe3-4505-8463-0cf648ecda96)

#### Rocketbot

Por desarrollar la herramienta y proveer cursos gratuitos para aprender a utilizarla.


## 6. Desarrollador del proyecto 👷

![imagen-readme](https://github.com/user-attachments/assets/133bc743-0424-4120-a7a6-7245d2f28f8c)

**| Ignacio Majo | Data Scientist Junior | Junior RPA Developer |**
