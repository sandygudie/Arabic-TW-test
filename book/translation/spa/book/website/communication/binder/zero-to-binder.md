(z2b)=
# Cero a Binder

En este capítulo, crearemos un proyecto Binder desde cero: primero haremos un repositorio en GitHub y luego lo lanzaremos en mybinder.org. Las secciones en las que se espera que complete una tarea se deben a tres semáforos :vertical_trafficic_light: emojis. Algunos pasos te dan la opción de Python, Julia o R - haz clic en la pestaña de tu idioma preferido.

```{admonition} Attributions
Este tutorial se basa en los talleres _Zero-to-Binder_ de Tim Head, que se pueden encontrar aquí: <http://bit.ly/zero-to-binder> y <http://bit.ly/zero-to-binder-rise>

Gracias a Anna Krystalli y Oliver Strickson por su ayuda para desarrollar el contenido de R y Julia. respectivamente.
```

```{attention}
El Binder puede tardar mucho en cargarse, pero esto no significa necesariamente que el Binder falle en su lanzamiento.
Siempre puede actualizar la ventana si ve el mensaje "... está tardando más en cargar, ¡colgar fuerte!".
```

```{admonition} If you are using R...
Si estás siguiendo la ruta R, hemos incluido algunos pasos alternativos usando el [paquete `holepunch`](https://github. om/karthik/holepunch) que construirá tu entorno usando una [imagen base de rocker](https://github.com/rocker-org/rocker) y debería, en última instancia, ser más rápido de construir y lanzar.
```

(z2b-reqs)=
## Requisitos

Necesitarás:

- **Algún código y algunos datos.** El código debe tardar menos de **10 minutos en ejecutar**, y los datos deben ser menores de **10 MB**. Esto podría significar que sólo escoge un script de un proyecto más grande, o que traiga un subconjunto de sus datos. Ten en cuenta que es realmente importante que el código y los datos se puedan hacer **públicos** porque usaremos la instancia pública del enlace.
- **Una cuenta de GitHub.** Por favor regístrate para una si aún no tienes una: <https://github.com/join>

(z2b-step-1)=
## 1. Crear un repositorio para Binderizar

🚦🚦🚦

````{tabbed} Python
1) Crea un nuevo repositorio en GitHub llamado "my-first-binder"
   - Asegúrate de que el repositorio es **público**, _not private_!
   - ¡No olvides inicializar el repositorio con un README!
2) Crea un archivo llamado `hello.py` a través de la interfaz web con `print("Hola de Binder!")` en la primera línea y envía un commit a la rama `main`
````

````{tabbed} Julia
1) Crea un nuevo repositorio en GitHub llamado "my-first-binder"
   - Asegúrate de que el repositorio es **público**, _not private_!
   - ¡No olvides inicializar el repositorio con un README!
2) Crear un archivo llamado `hola. l` a través de la interfaz web con `println("Hola de Binder! )` en la primera línea y enviar un commit a la rama `main`
3) Crea un archivo llamado `Project. oml` (ADVERTENCIA: la capitalización es importante!) con el siguiente contenido y consagrarlo a `main`.
   Esto instalará Julia en el entorno Binder .

   ```Julia
   [compat]
   Julia = "1.3"
```
````

````{tabbed} R
1) Crea un nuevo repositorio en GitHub llamado "my-first-binder"
   - Asegúrate de que el repositorio es **público**, _not private_!
   - ¡No olvides inicializar el repositorio con un README!
2) Crear un archivo llamado `hola. ` a través de la interfaz web con `print("Hola de Binder! )` en la primera línea y confirmar a la rama `main`
3) Crea un archivo llamado `runtime. xt` con `r-2022-01-01` en la primera línea.
   Esta fecha representa la instantánea de [CRAN](https://cran.r-project.org/) alojada en [RStudio Package Manager](https://packagemanager.rstudio.com) que usaremos.
   Cometer este archivo a la rama `main`.

   ```{note}
   En R puedes usar `holepunch::write_runtime()` para crear un `runtime.txt` en el directorio `.binder/`; será configurado con la fecha de hoy.
   ```
````
(z2b-public-repo)=
### ¿Por qué el repo tiene que ser público?
mybinder.org no puede acceder a los repositorios privados, ya que esto requeriría un token secreto. El equipo de Binder decide no asumir la responsabilidad de manejar fichas secretas, ya que mybinder.org es un servicio público y prueba del concepto tecnológico. Si acceder a los repositorios privados es una característica que usted o su equipo necesitan, le recomendamos que busque construir su propio [BinderHub](https://binderhub.readthedocs.io).
(z2b-step-2)=
## 2. ¡Lanza tu primer repo!
🚦🚦🚦
1) Ve a **<https://mybinder.org>** 2) Escribe la URL de tu repositorio en el recuadro "GitHub repo o URL". Debería verse así:
> **https://github.com/YOUR-USERNAME/my-first-binder** 3) A medida que escribes, la página web genera un enlace en la "Copiar la URL a continuación. ." box Debería verse así: **https://mybinder. rg/v2/gh/YOUR-USERNAME/my-first-binder/HEAD** 4) Copiarlo, abrir una nueva pestaña del navegador y visitar esa URL - Verás un "girador" cuando Binder lance el repositorio
Si todo funcionó sin problemas, verás una interfaz de JupyterLab.
(z2b-fondo-1)=
### ¿Qué está pasando en segundo plano? - Parte 1
Mientras esperas, BinderHub (el backend de Binder) es:
- Obteniendo tu repositorio de GitHub
- Analizando el contenido
- Construir una imagen Docker basada en tu repositorio
- Iniciando esa imagen de Docker en la nube
- Conectándote a ella a través de tu navegador
(z2b-step-3)=
## 3. Ejecutar el script
🚦🚦🚦

````{tabbed} Python
1. En el panel de inicio, seleccione "Terminal"
2. En la nueva ventana de terminal, escribe `python hello.py` y presiona return
````

````{tabbed} Julia
1. En el panel de inicio, seleccione "Terminal"
2. En la nueva ventana de terminal, escriba `ulevia hello.jl` y presione return
````

````{tabbed} R
1. En el panel de inicio, seleccione "Terminal"
2. En la nueva ventana de terminal, escribe `Rscript -e 'source("hello.R")'` y luego presiona return
````

`Hola de Binder!` debe imprimirse en el terminal.

(z2b-step-4)=
## 4. Dependencias fijadas

Era fácil empezar, pero nuestro entorno es barebones - ¡Añadamos una **dependencia**!

🚦🚦🚦

````{tabbed} Python
1) En tu repositorio crea un archivo llamado `requirements.txt`
2) Añade una línea que dice: `numpy==1.14.5`
3) ¡Comprueba los errores tipográficos! Luego envía un commit a la rama `main`
4) Visita **https://mybinder.org/v2/gh/YOUR-USERNAME/my-first-binder/HEAD** de nuevo en una nueva pestaña
````

````{tabbed} Julia
1) En su reproducción, edite el `Project. oml` archivo
2) Agrega un nuevo bloque que dice:

   ```úlcera
   [deps]
   CSV = "336ed68f-0bac-5ca0-87d4-7b16caf5d00b"
   ```

3) Compruebe los errores tipográficos! Luego confirmar a `main`.
4) Visita **https://mybinder.org/v2/gh/YOUR-USERNAME/my-first-binder/HEAD** de nuevo en una nueva pestaña
````

````{tabbed} R
1) En tu repositorio crea un archivo llamado `install.R`
2) Añade una línea que dice: `install.packages("readr")`
3) ¡Comprueba los errores tipográficos! Luego commit a la rama `main`
4) Visita **https://mybinder. rg/v2/gh/YOUR-USERNAME/my-first-binder/HEAD** otra vez en una nueva pestaña

```{note}
Si usas `holepunch`, puedes crear una `instalación. ` y añade automáticamente el código para instalar todas las dependencias de tu proyecto usando `holepunch::write_install()`.
```
````
Esta vez, haga clic en "Build Logs" en la barra gris grande, horizontal, grande. Esto le permitirá observar el progreso de su construcción. Es útil cuando falla tu compilación o falta algo que piensas que _debería_ estar instalado.

```{note}
A veces los registros de construcción de Binder imprimen cosas en la fuente roja, tales como advertencias de que `pip` no está actualizado (`pip` está a menudo desactualizado porque se actualiza regularmente! o mensajes de instalación, especialmente si está usando R.
Estos mensajes rojos no necesariamente significan que haya un problema con tu construcción y fallará - ¡Es una desafortunada elección de color de fuente!
```

(z2b-fondo-2)=
### ¿Qué está pasando en segundo plano? - Parte 2

Esta vez, BinderHub leerá el archivo de configuración que agregó e instalará la versión específica del paquete que solicitó.

(z2b-dependencias)=
### Más sobre las dependencias fijadas

````{tabbed} Python
En el ejemplo anterior, usamos dos signos iguales (`==`) para fijar la versión de `numpy`.
Esto le dice a Binder que instale esa versión _specific_.

Otra manera de anclar un número de versión es usar el signo mayor o igual (`>=`) para permitir que cualquier versión superior a una determinada sea instalada.
Esto es útil cuando tienes muchas dependencias que pueden tener dependencias unas de otras y permite a Binder encontrar una configuración de tus dependencias que no entran en conflicto entre ellas, evitando cualquier versión anterior que pueda romper o cambiar tu código.

Por último, no se pudo proporcionar ningún número de versión (sólo el nombre de la librería/paquete) y Binder instalará la última versión de ese paquete.
````

````{tabbed} Julia
En el ejemplo anterior, copiamos un hash en nuestro archivo `Project.toml` que está relacionado con la versión del paquete que nos gustaría instalar.
Para una gráfica de dependencias completa, también necesitaríamos incluir un archivo `Manifest.toml` que documentara las dependencias de dependencias.
Entre estos dos archivos, somos capaces de instanciar una replicación exacta de un entorno Julia.

Por supuesto, podemos imaginar que, a medida que el entorno crece y las interdependencias se vuelven más complejas, se convertiría en muy gravoso escribir estos archivos a mano!
La verdad es que nunca lo harías manualmente, el gestor de paquetes integrado `Pkg` puede [generarlos automáticamente](https://ulevialang.github.io/Pkg.jl/v1/environments/).
````

````{tabbed} R
En el ejemplo anterior, especificamos que queremos usar R en nuestro proyecto incluyendo una fecha en `runtime.txt`.
La fecha le dice a Binder de qué captura de CRAN para el código fuente R y paquetes.
Estas instantáneas proceden del [gestor de paquetes de RStudio](https://packagemanager.rstudio.com) (RSPM).
En el ejemplo anterior, se utiliza la snapshot RSPM con fecha `r-2022-01-01` y la versión de R y `readr` disponible en esa fecha e instalado.
Para que el flujo de trabajo de ejemplo funcione correctamente, por favor asegúrese de no proporcionar una fecha anterior a esta fecha de ejemplo.

Esto proporciona algunas versiones rudimentarias de paquetes para usuarios R pero no es tan robusto como las versiones fijadas en un `requirements.txt` en Python.
Para un anclaje de versión más robusto y específico en R, eche un vistazo al paquete [`renv`](https://rstudio.github.io/renv/).
````

(z2b-step-5)=
## 5. Compruebe el Entorno

🚦🚦🚦

````{tabbed} Python
1) Desde el panel de lanzamiento, selecciona "Python 3" en la sección de Cuadernos para abrir un nuevo cuaderno
2) Escribe lo siguiente en una nueva celda:

   ```python
   import numpy
   print(numpy.__version__)
   numpy.random. andn()
   ```

   ```{attention}
   ¡Ten en cuenta que los dos guiones bajos a cada lado de `version`!
   ```

3) Ejecuta la celda para ver el número de versión y un número aleatorio impreso

   - Presiona SHIFT+RETURN o el botón "Ejecutar" en la barra de menú
````

````{tabbed} Julia
1) Desde el panel de lanzamiento, seleccione "Julia" en la sección de Cuadernos para abrir un nuevo Cuaderno de Julia
2) Escriba lo siguiente en una nueva celda:

   ```Mañana
   usando Pkg
   Pkg. tatus()
   ```

3) Ejecute la celda para ver el número de versión impreso

   - Presione SHIFT+RETURN o el botón "Ejecutar" en la barra de menú
````

````{tabbed} R
1) Desde el panel de lanzamiento, selecciona "R" en la sección de Cuadernos para abrir un nuevo cuaderno R
2) Escribe lo siguiente en una nueva celda:

   ```r
   library(readr)
   packageVersion("readr")
   read_csv(system. ile("extdata/mtcars. sv", package = "readr"))
   ```

3) Ejecute la celda

    - Presione SHIFT+RETURN o el botón "Ejecutar" en la barra de menú
    Debería ver la siguiente salida:
      - el número de versión de la versión instalada de `readr`
      - un martilo del contenido de los `mtcars. sv` que es un archivo csv incluido en el paquete `readr`
````

```{attention}
Si guardas este cuaderno, **no** se guardará en el repositorio de GitHub.
El envío de cambios de vuelta al repositorio de GitHub a través del contenedor no es posible con Binder.
**Los cambios que hayas realizado en los archivos dentro del Binder se perderán una vez que cierres la ventana del navegador.**
```

(z2b-step-6)=
## 6. Compartiendo tu trabajo

Binder trata de compartir tu trabajo fácilmente y hay dos maneras de hacerlo:

- Comparte la URL **https://mybinder.org/v2/gh/YOUR-USERNAME/my-first-binder/HEAD** directamente
- Visita **[https://mybinder. rg](https://mybinder.org)**, escribe la URL de tu repositorio y copia el fragmento de texto estructurado o Markdown en tu `README. d` archivo. Este fragmento renderizará una insignia que la gente puede hacer clic, que se ve así: ![Binda](https://mybinder.org/badge_logo.svg)

🚦🚦🚦

1) Añade el fragmento **Markdown** de **<https://mybinder.org>** al archivo `README.md` en tu repositorio
   - La barra gris que muestra una insignia se desplegará para revelar los fragmentos. Haga clic en el icono del portapapeles junto a la casilla marcada con "m" para copiar automáticamente el fragmento de Markdown. 2) ¡Haz clic en la insignia para asegurarte de que funciona!

(z2b-step-7)=
## 7. Accediendo a los datos en tu Binder

Otro tipo de dependencia para proyectos es **datos**. Hay diferentes maneras de hacer que los datos estén disponibles en tu Binder dependiendo del tamaño de tus datos y de tus preferencias para compartirlos.

(z2b-pequeño-archivos)=
### Archivos públicos pequeños

El método más simple para archivos pequeños de datos públicos es añadirlos directamente a su repositorio de GitHub. Luego se encapsulan directamente en el medio ambiente y se versionan junto con tu código.

Esto es ideal para archivos de hasta **10MB**.

(z2b-archivos medios)=
### Archivos públicos medios

Para acceder a archivos medios **desde unos 10 MB hasta unos cuantos cientos de MB**, puedes añadir un archivo llamado `postBuild` a tu repo. Un archivo `postBuild` es un script de shell que se ejecuta como parte de la construcción de la imagen y solo se ejecuta una vez que se construye una nueva imagen, no cada vez que el Binder es lanzado.

See [Binder's `postBuild` example](https://mybinder.readthedocs.io/en/latest/using/config_files.html#postbuild-run-code-after-installing-the-environment) for more uses of the `postBuild` script.

```{note}
Las imágenes nuevas sólo se construyen cuando Binder ve una nueva confirmación, no cada vez que hace clic en el enlace de Binder .
Por lo tanto, los datos sólo se descargan una vez cuando se construye la imagen de Docker, no cada vez que se lanza el enlace.
```

(z2b-i-files)=
### Grandes archivos públicos

No es práctico colocar archivos grandes en su repositorio de GitHub o incluirlos directamente en la imagen que construye Binder . La mejor opción para archivos grandes es utilizar una biblioteca específica al formato de datos para transmitir los datos a medida que lo estás usando o descargarlos bajo demanda como parte de tu código.

Por razones de seguridad, el tráfico saliente de su Binder está restringido únicamente a conexiones HTTP/S o GitHub. No podrá utilizar sitios FTP para obtener datos en mybinder.org.

(z2b-archivos-privados)=
### Archivos privados

No hay forma de acceder a archivos que no son públicos desde mybinder.org. Deberías considerar toda la información de tu Binder como pública, lo que significa que:

- no debería haber contraseñas, tokens, llaves, etc. en su repositorio de GitHub;
- no debería escribir contraseñas en un Binder corriendo en mybinder.org;
- no debería subir su clave SSH privada o token de API a un Binder en ejecución.

Con el fin de soportar el acceso a archivos privados, necesitarías crear un despliegue local de [BinderHub](https://binderhub.readthedocs.io) donde puedes decidir las compensaciones de seguridad tú mismo.

```{note}
Construir un BinderHub no es una tarea sencilla y generalmente es asumido por grupos de IT/RSE por razones relacionadas con la gestión de mantenimiento, seguridad y gobernanza.
Sin embargo, eso no quiere decir que sean los _sólo_ grupos de personas que deberían/podrían construir un BinderHub.
```

(z2b-step-8)=
## 8. Obtener datos con `postBuild`

🚦🚦🚦

````{tabbed} Python
1) Ve a tu repositorio de GitHub y crea un archivo llamado `postBuild`
2) En `postBuild`, añade una sola lectura en línea: `wget -q -O gapminder. sv http://bit.ly/2uh4s3g`
   - `wget` es un programa que recupera contenido de servidores web.
     Esta línea extrae el contenido de la bitly URL y lo guarda en el nombre de archivo indicado por la bandera `-O` (mayúsculas "O", no cero), en este caso `gapminder. sv`.
     La bandera `-q` le dice a `wget` que haga esto en silencio, lo que significa que no imprimirá nada en la consola.
3) Actualizar sus `requisitos. archivo xt` añadiendo una nueva línea con `pandas` en él y otra nueva línea con `matplotlib` en él
   - Estos paquetes no son necesarios para descargar los datos, pero los usaremos para leer el archivo CSV y hacer una gráfica
4) Haz clic en la insignia de enlace en tu README para lanzar tu Binder

Una vez que el Binder se haya lanzado, debería ver que ha aparecido un nuevo archivo que no era parte de su repositorio cuando hizo clic en la insignia.

Ahora visualice los datos creando un nuevo cuaderno (seleccionando "Python 3" en la sección Notebook) y ejecute el siguiente código en una celda.

```python
%matplotlib en línea

import pandas

data = pandas.read_csv("gapminder.csv", index_col="country")

años = datos. olumns.str.strip("gdpPercap_") # Extraer año de los últimos 4 caracteres de cada nombre de columna
data.columns = años. stype(int) # Convierte valores de año a enteros, guardar resultados de vuelta a dato

datos. oc["Junia"]. lot()
```

```{note}
Vea esta [lección de Carpintería de software](https://swcarpentry.github.io/python-novice-gapminder/09-plotting/index.html) para más información.
```
````

````{tabbed} Julia
1) Ve a tu repositorio de GitHub y crea un archivo llamado `postBuild`
2) En `postBuild`, añade una sola lectura en línea: `wget -q -O gapminder. sv http://bit.ly/2uh4s3g`
   - `wget` es un programa que recupera contenido de servidores web.
     Esta línea extrae el contenido de la bitly URL y lo guarda en el nombre de archivo indicado por la bandera `-O` (mayúsculas "O", no cero), en este caso `gapminder. sv`.
     La bandera `-q` le dice a `wget` que haga esto en silencio, lo que significa que no imprimirá nada en la consola.
3) Actualizar su `Project. oml` archivo añadiendo nuevas dependencias a `[deps]` con las siguientes líneas:

   ```ucaramia
   DataFrames = "a93c6f00-e57d-5684-b7b6-d8193f3e46c0"
   Plots = "91a5bcdd-55d7-5caf-9e0b-520d859cae80"
   ```

   - Estos paquetes no son necesarios para descargar los datos pero los usaremos para leer el archivo CSV y hacer una trampa
4) Haga clic en la insignia del binder para lanzar su Binder

Una vez que el Binder haya iniciado, debería ver que ha aparecido un nuevo archivo que no era parte de su repositorio cuando hizo clic en la insignia.

Ahora visualice los datos creando un nuevo cuaderno (seleccionando "Julia" en la sección Notebook) y ejecute el siguiente código en una celda.

```Thursia
using DataFrames
using CSV
using Plots

data = CSV.read("gapminder. sv", DataFrame)

# Extrae la fila correspondiente a Australia
aus_gdp = data[data[:, :country] . = "Ninguna", :]
aus_gdp = MATIx(aus_gdp[:, :end])[:] # as vector

# Extraer los años como Ints de los nombres de las columnas
años = [x[end-3:end] for x in names(data)[2:end]]
años = análisis. Int, años)

# Trazar
parcela (años, aus_gdp)
```
````

````{tabbed} R
1) Ve a tu repositorio de GitHub y crea un archivo llamado `postBuild`
2) En `postBuild`, añade una sola lectura en línea: `wget -q -O gapminder. sv http://bit.ly/2uh4s3g`
   - `wget` es un programa que recupera contenido de servidores web.
     Esta línea extrae el contenido de la bitly URL y lo guarda en el nombre de archivo indicado por la bandera `-O` (mayúsculas "O", no cero), en este caso `gapminder. sv`.
     La bandera `-q` le dice a `wget` que haga esto en silencio, lo que significa que no imprimirá nada en la consola.
3) Actualiza tu archivo `install.R` para instalar dos dependencias adicionales, `"tidyr"` y `"ggplot2"`. Para ello, proporcione un vector de caracteres de los paquetes requeridos a `install.packages()` en lugar de una única cadena de caracteres. El comando de instalación ahora debería verse así:

   ```r
   install. ackages(c("readr", "tidyr", "ggplot2"))
   ```

    - Estos paquetes no son necesarios para descargar los datos, pero los usaremos para leer el archivo CSV, procesarlo y hacer una parcela
4) Haga clic en la insignia del binder en su README para lanzar su Binder

Una vez que el Binder se haya lanzado, debería ver que ha aparecido un nuevo archivo que no era parte de su repositorio cuando hizo clic en la insignia.

Ahora visualice los datos creando un nuevo cuaderno (seleccionando "R" en la sección Notebook) y ejecutando el siguiente código en una celda.

```r
library(readr)
library(tidyr)
library(ggplot2)

datos <- read_csv("gapminder. sv") %>%
    pivot_longer(-country,
                 nombres_to = "año",
                 valores_to = "gdpPercap",
                 names_prefix = "gdpPercap_",
                 nombres_transformacin = lista(año = as. nteger))

data[data$country == "Corealia", ] %>%
    ggplot(aes(x = año, y = gdpPercap)) +
    geom_line()
```
````
(z2b-o-notebooks)=
## Cambiando la interfaz
A lo largo de este tutorial hemos estado utilizando la interfaz de JupyterLab. Esta es la interfaz por defecto para las nuevas instancias de Binder creadas. Sin embargo, esta no es la única interfaz disponible en mybinder.org, la vista Classic Notebook y RStudio también están disponibles. (Debe instalarse un entorno R para que RStudio esté disponible.)
Puede acceder a las diferentes interfaces de diferentes maneras. La forma más fácil es usar los botones en el JupyterLab Launcher, pero usted puede proporcionar parámetros de URL para abrir directamente una interfaz específica (o archivo! cuando la instancia de Binder se ejecuta. Ahora cubriremos tres maneras en que puedes manipular tu URL de Binder para navegar entre interfaces.
### desde dentro de un Binder en ejecución
Esta es la estructura de la URL dentro de una instancia de Binder en ejecución ejecutando JupyterLab:
> **https://<some-prefix>.mybinder.org/user/<a composite of your username, repo name and a hash>/lab**
You can change the interface from JupyterLab to either the Classic Notebook or RStudio by changing the `/lab` part of the URL to:
- **Classic Notebook:** `/tree`
- **RStudio:** `/rstudio`
### by changing the mybinder.org launch link
Here is the launch link you have been using throughout this tutorial:
> **https://mybinder.org/v2/gh/YOUR-USERNAME/my-first-binder/HEAD**
You can access each interface by appending once of the following to the end of you URL:
- **Jupyter Notebook:** `?urlpath=tree`
- **JupyterLab:** `?urlpath=lab`
- **RStudio:** `?urlpath=rstudio`
### by using the mybinder.org form
You can also set the interface when constructing your launch link on the mybinder.org website (instead of editing the URL directly) as demonstrated in the below gif.

```{figure} https://user-images.githubusercontent.com/1448859/53651127-4dabe900-3c46-11e9-8684-2cfde840d4ce.gif
---
name: changing_interfaces
alt: A gif demonstrating how to change the interface of a Binder on the mybinder.org website
---
Use the "URL to open" option on the mybinder.org site to select your interface
```

(z2b-over-to-you)=
## Now over to you!

Now you've binderized (bound?) this demo repo, it's time to binderize the example script and data you brought along!

**Some useful links:**

- Choosing languages:
  - **<https://mybinder.readthedocs.io/en/latest/howto/languages.html>**
- Configuration files:
  - **<https://mybinder.readthedocs.io/en/latest/using/config_files.html>**
- Example Binder repos:
  - **<https://mybinder.readthedocs.io/en/latest/sample_repos.html>**
- Getting data:
  - With `wget`: **<https://github.com/binder-examples/getting-data>**
  - With `quilt`: **<https://github.com/binder-examples/data-quilt>**
  - From remote storage: **<https://github.com/binder-examples/remote_storage>**

**Advanced usage patterns:**

- Separating content from envorinment with `nbgitpuller` to reduced rebuilds:
  - **<https://discourse.jupyter.org/t/tip-speed-up-binder-launches-by-pulling-github-content-in-a-binder-link-with-nbgitpuller/922>**
- Tips for reducing the start-up time of your repository:
  - **<https://discourse.jupyter.org/t/how-to-reduce-mybinder-org-repository-startup-time/4956>**
