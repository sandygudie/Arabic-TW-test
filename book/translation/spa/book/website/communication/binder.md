(binder)=
# Binda

En este capítulo, discutiremos Project Binder y mybinder.org como un medio para compartir la investigación de manera transparente e interactiva.

(binder-compartir)=
## ¿Por qué debería compartir su trabajo?

La motivación para compartir los resultados de la investigación está explorada más profundamente en el capítulo {ref}`rr-open`.

En pocas palabras, compartir tu código de investigación puede ayudar a proporcionar contexto a los resultados que presentas al ilustrar el proceso por el que fuiste para alcanzarlos. Al compartir código, también evitamos reinventar la rueda para poder avanzar en un tema de investigación ya que las herramientas anteriores están disponibles para ser construidas encima de.

Sin embargo, la mayor barrera para compartir código a menudo es instalar paquetes y configurar el entorno computacional, como veremos en la siguiente sección. Al compartir tu trabajo a través de plataformas como mybinder.org:

- Instalar paquetes de software ya no es un desafío
- Las personas que usan diferentes sistemas operativos tienen experiencias similares desde que el cálculo está ocurriendo en la plataforma, no en su máquina local
- Su trabajo puede ser distribuido a un público más amplio ya que la barrera técnica ha sido reducida

(binder-qué)=
## ¿Qué es Project Binder?

Hemos discutido por qué es importante compartir tu trabajo y hemos llegado a un punto en el que hemos decidido publicar algunos Notebooks de Jupyter con código de análisis en una plataforma colaborativa, como GitHub.

GitHub es una gran plataforma para compartir código _estáticamente_. Si el repositorio es público, cualquiera puede navegar a su Cuadro de notas y leer el contenido. Sin embargo, _ejecutar código_ es mucho más complicado que mostrarlo como lo hace GitHub. Se requieren muchas partes interdependientes para ejecutar código, como:

- una copia del código en sí;
- el software apropiado para ejecutarlo;
- cualquier paquete extra del que el código depende que no se envía como parte del software del núcleo;
- cualquier dato de entrada que el análisis requiere;
- y también necesita algún hardware (¡una computadora!) para ejecutarlo también.

Además de adquirir todas esas partes, también tiene que instalarlos correctamente y de tal manera que no estén influenciados ni entren en conflicto con otros programas que puedan estar ejecutándose en su máquina. ¡Es mucho trabajo!

¿Cuánto más fácil sería si pudiéramos **ejecutar código en el navegador**, similar a como se muestra? Esto es lo que pretende conseguir el proyecto Binder .

Project Binder proporciona al usuario la siguiente infraestructura:

- algún hardware para ejecutar código, generalmente un servidor alojado en la nube pero también puede ser hardware local;
- un entorno computacional que contiene:
  - el software de aprendizaje,
  - cualquier dependencia extra del paquete,
  - cualquier dato de entrada requerido,
  - y una copia del código mismo (Notebooks o scripts);
- una URL a donde se está ejecutando el entorno para que el código pueda ser interactuado por usted o sus colaboradores.

Project Binder ha empaquetado juntos todas las partes en movimiento que hacen difícil compartir trabajo computacional en una interfaz sencilla de usar. Hay una versión **gratuita y pública** de esta interfaz ejecutándose en [**mybinder.org**](https://mybinder.org).

La caricatura siguiente, de Juliette Taka, demuestra un flujo de trabajo que el científico que utiliza Binder podría adoptar.

```{figure} ../figures/binder-comic.png
---
name: binder_comic
alt: Una ilustración de los pasos que una persona puede tomar para crear un proyecto binderizado.
---
Crédito de la Figura: [Juliette Taka, Logilab y el proyecto OpenDreamKit](https://opendreamkit.org/2017/11/02/use-case-publishing-reproducible-notebooks/)
```

Puede obtener más información sobre Project Binder y mybinder.org en su página [Acerca de mybinder.org](https://mybinder.readthedocs.io/en/latest/about/about.html).

(binder-disam)=
### Disambiguación

En esta sección hay algunos términos relacionados, que se esbozarán aquí para mayor claridad:

- **Project Binder**: Una comunidad abierta que permite crear entornos compartibles, interactivos y reproducibles. La salida tecnológica de este proyecto es un {ref}`rr-binderhub`.
- **BinderHub**: Una infraestructura basada en la nube para generar Binders. El más utilizado es [mybinder.org](https://mybinder.org), que es mantenido por el equipo de Project Binder. Está construido sobre un rango de herramientas de código abierto, incluyendo [JupyterHub](https://z2jh.jupyter.org), para proporcionar recursos de computación en la nube a los usuarios a través de un navegador; y [`repo2docker`](https://repo2docker.readthedocs.io/), para construir imágenes docker a partir de proyectos. Dado que es un proyecto abierto, es posible crear otros BinderHubs que puedan soportar configuraciones más especializadas. Una de esas configuraciones podría incluir autenticación para permitir que los repositorios privados sean compartidos entre colaboradores cercanos.
- **A Binder**: Una versión compartible de un proyecto que puede ser visto e interactuado dentro de un entorno computacional reproducible corriendo en la nube a través de un navegador web. Al automatizar la instalación del entorno de computación (como se explica en el capítulo {ref}`rr-renv` ), Project Binder transforma la sobrecarga de compartir dicho entorno en el acto de compartir una URL.
- **[mybinder.org](https://mybinder.org)**: Un BinderHub público y gratuito. Debido a que es público, no debes usarlo si tu proyecto requiere información personal o confidencial (como contraseñas).
- **Binderize**: El proceso de hacer un Binder a partir de un proyecto.

(binder-apropiado)=
## ¿Cuándo es apropiado usar mybinder.org?

Mantener un servicio gratuito y anónimo en la nube es mucho trabajo voluntario y cuesta mucho dinero. Para reducir un poco los costos de ejecución, mybinder.org coloca restricciones computacionales en cada instancia de Binder en funcionamiento. Estas restricciones son:

- 1 CPU, y
- 1 GB de RAM.

Por lo tanto, mybinder.org no es **** un lugar apropiado para realizar replicaciones de los flujos de trabajo de aprendizaje de máquinas, ¡por ejemplo!

Y esta es la razón principal por la que este capítulo sobre Binder ha sido colocado en la "Guía para la comunicación". Con estas restricciones computacionales, mybinder.org se presta muy bien a albergar demostraciones interactivas y recursos de aprendizaje para paquetes de software o análisis de investigación. En este escenario, la gente que hace clic en el enlace Binder probablemente quiera aprender algo, y sentarse a través de un largo proceso de entrenamiento de modelos probablemente no les ayudará a lograrlo. En su lugar, podrías proporcionar modelos o instrucciones preformados sobre cómo entrenar los modelos en su propio hardware y _volver_ al Binder para el resto del tutorial interactivo.

Entonces, ¿cuándo es apropiado usar mybinder.org?

- Cuando quieras _comunicar_ algo de forma interactiva, como análisis cortos, tutoriales o incluso blogs! Echa un vistazo al blog de [Achintya Rao alimentado por mybinder.org](https://blog.achintyarao.in/about/)!
- Cuando el código y los datos asociados (si es relevante) están disponibles públicamente
- Cuando el código que desea ejecutar interactivamente no requiere muchos recursos o recursos especializados (por ejemplo, GPUs)

(binder-faqs)=
## FAQs

Muchas preguntas comunes se responden en la página [Acerca de mybinder.org](https://mybinder.readthedocs.io/en/latest/about/about.html).

### ¿Cómo guardo mis cambios de vuelta a mi repositorio?

Desgraciadamente, no pueden. Al menos, no desde la línea de comandos en una instancia de Binder en ejecución.

Escribiendo de nuevo a un repositorio alojado, ya sea en GitHub o alguna otra plataforma, requerirá una credencial de algún tipo para autorizarte a escribir en ese repositorio. Y como ya se ha mencionado, mybinder. rg es un servicio completamente público y no debe proporcionar ninguna información sensible a una instancia de Binder que se ejecute bajo ninguna circunstancia.

Sin embargo, mybinder. rg ejecuta un complemento llamado [`jupyter-offlinenotebook`](https://github.com/manics/jupyter-offlinenotebook) que proporciona un botón de descarga para guardar sus cuadernos localmente, _¡incluso si tu navegador ha perdido su conexión con la infraestructura de la nube que proporciona el ordenador!_ Esto significa que puede guardar su progreso localmente, actualizar su repositorio con sus cuadernos guardados y volver a abrir su Binder con los cuadernos actualizados.

```{figure} ../figures/binder_notebook_banner.jpg
---
nombre: binder_notebook_banner
alt: Una captura de pantalla del panel de control de un Cuadro de Jupyter con un botón de descarga resaltado por un rectángulo morado.
---
Utilizando este botón de "Descargar" en un Cuadro de notas de Jupyter corriendo en mybinder. rg le permitirá guardar sus cuadernos localmente, incluso después de que la instancia de Binder haya sido desconectada de los recursos computacionales.
```

### ¿Cómo puedo colaborar con mis pares en mybinder.org?

No es imposible, pero definitivamente hay espacio para desarrollar esta característica en comparación con otros servicios de "computación en la nube gratuita".

Quienes están interesados en esto, puede encontrar más en [esta publicación de discurso](https://discourse.jupyter.org/t/collaborating-on-one-binder-instance/407) y en [`jupyterlab-link-share` repository](https://github.com/jtpio/jupyterlab-link-share).

### ¿Cómo es mybinder.org diferente a Google Colab?

Google Colab proporciona un entorno computacional "lavabo de cocina" con muchos de los paquetes de software de ciencia de datos más populares preinstalados. En contraste, mybinder.org construye imágenes bespoke para cada repositorio lanzado, específicamente instalando los paquetes listados en sus archivos de configuración.

### ¿Puedo conectar con `INSERT DATA PROVIDER AQUÍ`?

Las conexiones de red en mybinder.org están bastante limitadas por motivos de seguridad y prevención de abusos. Dicho esto, debería ser capaz de conectarse a un proveedor de datos externo siempre que satisfaga los dos criterios siguientes:

- Se puede acceder mediante una conexión HTTP/HTTPS
- No necesita credenciales para acceder a los datos

Recuerde que mybinder.org es un servicio completamente público y bajo ninguna circunstancia debe proporcionar información confidencial, como credenciales, a una instancia de Binder .

(segue-binder)=
## Cómo crear un proyecto listo para Binder

El siguiente capítulo contiene un [tutorial de cero-a-Binder](z2b) que te guiará a través de la creación de tu primer proyecto listo para Binder en GitHub.
