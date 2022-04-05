(estilo de código rr)=
# Code Style and Formatting

A coding style is a set of conventions on how to format code. For instance, what do you call your variables? Do you use spaces or tabs for indentation? ¿Dónde ponen sus comentarios? El uso consistente del mismo estilo a lo largo de su código hace que sea más fácil de leer. Consistently using the same style throughout your code makes it easier to read. Code that is easy to read is easier to understand by you as well as by potential collaborators. Therefore, adhering to a coding style reduces the risk of mistakes and makes it easier to work together on software. [Why Coding Style Matters](http://coding.smashingmagazine.com/2012/10/25/why-coding-style-matters/) is a nice article on why coding styles matter and how they increase software quality.

For example, [PEP8](https://www.python.org/dev/peps/pep-0008/) is the most widely used Python coding style and [ECMAScript 6](http://es6-features.org/) aka [ES6](http://es6-features.org/) is the scripting-language specification standardized by ECMA International for programming in Javascript.

For commonly used style guides for various programming languages see the [Language Guides](https://guide.esciencecenter.nl/best_practices/language_guides/languages_overview.html). Google also has a [style guide](https://code.google.com/p/google-styleguide/) for many languages that are used in open source projects originating out of Google.

(rr-código-estilo-y-formato)=
## Automatic formatting

Existen numerosas herramientas para formatear automáticamente el código de tal forma que siga un estilo determinado. El formato automático permite una mayor calidad de código, especialmente cuando estás colaborando en un equipo y otras personas necesitan mirar el código que has escrito. Muchos desarrolladores y organizaciones mantienen estándares de formato de código como **2 espacios** o **4 espacios de sangría**. El uso de estos es altamente recomendable, ya que la probabilidad de encontrar errores (si los hay) aumenta múltiple.

[EditorConfig](https://editorconfig.org) es una herramienta independiente de lenguaje que ayuda a mantener estilos consistentes de espacios en blanco para varias personas que trabajan en el mismo proyecto en varios editores. La mayoría de los editores soportan EditorConfig ya sea nativamente o a través de un plugin. Casi todos los IDEs y editores de texto ampliamente utilizados soportan el formato automático de código al teclear. Por ejemplo: [JetBrains IDE Suite](https://www.jetbrains.com/products.html#), [VSCode](https://code.visualstudio.com/) y [Atom](https://atom.io/).

Además de eso, hay muchas herramientas específicas de lenguaje para formatear código de forma automática de acuerdo a un estilo particular. Tenga en cuenta que los editores a menudo soportan el uso de estas herramientas directamente desde el entorno de edición.

| Language   | Formatter Tool                                                                                              |
| ---------- | ----------------------------------------------------------------------------------------------------------- |
| C/C++      | [GNUIndent](http://www.gnu.org/software/indent/), [GreatCode](http://sourceforge.net/projects/gcgreatcode/) |
| Python     | [Black](https://black.readthedocs.io), [yapf](https://pypi.org/project/yapf/)                               |
| Javascript | [beautifier.io](https://beautifier.io/)                                                                     |
| Java       | [Google Java format](https://github.com/google/google-java-format), [JIndent](http://www.jindent.com/)      |
| PHP        | [phpStylist](http://sourceforge.net/projects/phpstylist/)                                                   |
| Perl       | [PerlTidy](http://perltidy.sourceforge.net/)                                                                |
| Shell/Bash | [ShellIndent](http://www.bolthole.com/AWK.html)                                                             |
| CSS        | [CSSTidy](http://csstidy.sourceforge.net/)                                                                  |
| HTML       | [Tidy](http://tidy.sourceforge.net/)                                                                        |

**Consejo rápido**: Si utiliza el código VS como su editor de texto principal, puede habilitar el formato automático de código directamente en su navegador. Abre tu página de preferencias en modo JSON y añade la siguiente línea:

```
"editor.formatOnSave": true,
```

(rr-código-servicio-estilo)=
## Online services providing software quality checks

Existen varios servicios web que analizan código y hacen visible la calidad del código. Generalmente estos servicios ejecutan una o más herramientas estáticas de análisis de código que también pueden ser usadas desde la línea de comandos o integradas en su editor en su propio equipo. El uso de un servicio de calidad de código que se integra con un repositorio de GitHub/GitLab es altamente recomendable, ya que puede detectar y comunicar problemas de calidad en solicitudes de extracción.

Los servicios de análisis de calidad de código son sitios web que a menudo ofrecen las siguientes características:

- Automatically analyse your code after pushing it to GitHub/GitLab
- Usually free for open source projects
- Support multiple programming languages, but not every language will have the same level of features
- Grade or score for the quality of all of the code in the repository
- List of issues with the code, grouped by severity
- Drill down to location of issue
- Default list of checks which the service provider finds the best practice
- Can be configured to make the list of checks more strict or relaxed
- Can be configured to ignore files or extensions
- Can read a configuration file from repository
- Track issues over time and send alerts when quality deteriorates
- Optionally reports on code coverage generated by a CI build
- Automatically deploy the repository and generates a preview build for review before final release.

Para una lista de opciones vea [shields.io](https://shields.io/category/analysis) o [esta lista de servicios gratuitos para proyectos de código abierto](https://github.com/ripienaar/free-for-dev#code-quality).
