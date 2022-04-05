(rr-open-source)=
# Open Source Software

(rr-open-source-whatis)=
## What Is Open Source Software?

When a project is open-source [{term}`def<Open Source Software>`], anybody can view, use, modify, and distribute the project for any purpose. These permissions are enforced through an open-source licence. Open source is powerful because it lowers the barriers to adoption, allowing ideas to spread quickly. In its most basic form, open-sourcing your software means putting your code online where it can be viewed and reused by others.

Many of the most widely used research software is open source. Perhaps the paradigmatic example is the scikit-learn Python package for machine learning (Pedregosa et al., 2011), which, in the space of just over five years, has attracted over 500 unique contributors, 20,000 individual code contributions, and 2,500 article citations. Producing a comparable package using a traditional closed-source approach would likely not be feasible. It would, at the very least, require a budget of tens of millions of dollars. While scikit-learn is an outlier, hundreds of other open-source packages that support much more domain-specific needs depend similarly on unsolicited community contributions; for example, the NIPY (neuroimaging in Python) group of projects in neuroimaging (Gorgolewski et al., 2016). Notably, such contributions not only result in new functionality from which the broader community can benefit, but also regularly provide their respective authors with greater community recognition, and lead to new project and employment opportunities.

Researchers that make use of open-source software often make changes to them, such as adding features they need for their research, or fixing bugs. They can then contribute these improvements back to the main project so the wider community can take advantage of them.

(rr-open-source-benefitsyou)=
## How Running and Contributing to Open-Source Software Projects Benefits You

- _Improve existing skills_: Whether it is coding, user interface design, graphic design, writing, or organizing, if you are looking for practice, there is a task for you on an open-source software project. Further, open source necessitates cleaner, more maintainable code to enable collaboration between potentially thousands of people who may never meet. This helps to build and maintain good coding habits. Not to be underestimated are the people skills you can develop on open source software projects. Open source offers opportunities to practice leadership and management skills, such as resolving conflicts, organising teams of people, and prioritising work.
- _Advance your career_: By definition, all of your open source work is public, and this presents opportunities:
  - _Demonstrate technical ability_: Technical interviews traditionally involve working on a simulated problem that can be tackled in a set amount of time with little additional context. Such simulations, by definition, are not real-world use cases, nor do they show what working with an applicant would be like. Open source provides visibility into both how a candidate solves problems, and how they work with others. You make a much more appealing employee if an employer can see the quality of your work and see you working with others over a long period rather than taking a chance on a single short, high-stress case which may not play to your strengths.
  - _Reputation_: Becoming an active member of the open source community can gain you a favourable reputation which may bolster future job prospects.
- _Meet people with similar interests_: Open source software projects with warm, welcoming communities keep people coming back for years, and many people form lifelong friendships through their participation in open source.
- _Find mentors and teach others_: Working with others on a shared project means you will have to explain how you do things, as well as ask other people for help. The acts of learning and teaching can be a fulfilling activity for everyone involved.

### Making Your Work Open Source

- _Re-usability_: Making your work openly available for re-use makes it easier for others to incorporate into their research. If you make your software citeable, via a DOI [{term}`def<Digital Object Identifier>`] for example, this can increase your citations.
- _Contribution_: When you write closed source software, the only developers that can potentially detect, diagnose, triage, and resolve software bugs are those that have a copy of the code. If your project is open, the number of potential contributing developers and thus the potential knowledge pool is orders of magnitude larger.
- _Feedback_: Making your work open enables you to get feedback and improve your project in a way you may never have thought of alone.
- _Accountability_: There is an argument that any software developed using government money should be open source by default; if the public has paid for its development they have a right to make use of it. If your work is government-funded, making it open is a step you can take towards government openness and accountability.

### Contributing to Others' Open Source Software Projects

- _It is empowering to be able to make changes, even small ones_: You do not have to become a lifelong contributor to enjoy participating in open source. Have you ever seen a typo on a website, and wished someone would fix it? On an open source software project, you can do just that. Open source helps people feel agency over their lives and how they experience the world, and that in itself is gratifying.
- _Es divertido_: El código abierto proporciona un conjunto de cubos Rubix interminables y cambiantes para que puedas resolver los fines de semana. Just like puzzles, both crossword and jigsaw, open source provides bite-sized intellectual escapes.

(rr-open-source-benefitsresearch)=
## How Open Source Software Benefits Research

Hay varias maneras en las que el software de código abierto beneficia la investigación:

(rr-open-source-benefitsresearch-reusable)=
### Re-usable

Open source software projects allow researchers to take advantage of each others’ work. This enables researchers to apply their efforts to high-value work. It is sometimes said that “all the easy problems have already been solved”. Blogging, content management, and operating systems are all problems with established (and mainstream) open-source solutions, to name a few. While developers could spend their time reinventing wheels that the open-source community has already perfected, it is highly preferable to use the world’s best wheel, especially when that wheel comes at no cost to you. This reduces duplication of effort and allows researchers to focus on yet-unsolved challenges.

El {ref}`rr-code-reuse` proporciona una lista más profunda de diferentes aspectos a considerar para hacer tu código más reutilizable, si se trata de un pequeño script o una biblioteca.

(rr-open-source-benefitsresearch-checkable)=
### Checkable

Los proyectos de código abierto permiten a la comunidad investigadora más amplia leer y probar el código de los demás. De esta manera, los errores se pueden encontrar más rápidamente, y otros investigadores pueden validar los resultados.

(rr-open-source-benefitsresearch-colaborativo)=
### Collaborative
Trabajar abiertamente también permite que cualquier número de investigadores colaboren en proyectos que no puedan ser desarrollados por un único investigador/grupo de investigación. Algunos ejemplos incluyen sistemas operativos [Linux](https://www.linux.org/) , paquetes Python como [scipy](https://www.scipy.org/) y [numpy](http://www.numpy.org/), y la biblioteca de aprendizaje automático [TensorFlow](https://www.tensorflow.org/).

(rr-open-source-run)=
## How to Run Your Open Source Software Project

Usted puede abrir una idea, una obra en curso, o después de años de ser de código cerrado. En el nivel más básico, todo lo que necesitas hacer es poner tu código en línea en algún lugar que probablemente dure mucho tiempo. Puede hacer que su código sea citado asignándole un DOI [{term}`def<Digital Object Identifier>`] (como se explica en la sección de {ref}`rrr-rdm-sharing`). Esto ayuda a asegurar que obtenga el crédito adecuado si la gente utiliza o se basa en su trabajo.

Un lugar popular para que tu código esté disponible es GitHub [{term}`def<Github>`] (ver el capítulo {ref}`rrr-vcs`). Debe incluir un archivo de licencia indicando que cualquiera tiene permiso para usar, copiar y modificar su trabajo. Sin esto, nadie puede utilizar legalmente su trabajo, por lo que no es de código abierto. El capítulo de {ref}`rr-licensing` le ayudará a elegir la mejor licencia para su proyecto. También hay algunos otros archivos que debería incluir con su código, como se describe a continuación.

(rr-open-source-run-readme)=
### Welcome Users by Adding Information to Your README

Debe incluir un archivo README [{term}`def<README>`] donde incluya información útil sobre lo que es el proyecto. cómo usarla, y cómo contribuir a ella. Aquí hay una lista de las principales cosas que un README debe incluir:

- _The project name and what it is_: This will significantly help someone that comes across it to get an idea of the project. Include a few key points that describe the main features of the project and what features you are implementing. This helps to quickly compare other projects with yours and gives an idea of why the project exists in the first place.
- _Instructions on how to install the project_: The installer might be a collaborator, someone that comes across and is interested in the project, or even you - if you get a new machine and need to re-install your project. Nevertheless, it is a total waste of your resources to figure out how to get started with the project from scratch. The instructions should also include any prerequisites that will be needed to run the project. The best thing you can do is to write up the installation instructions when you first do them yourself, and you will quickly save hours of work in the future.
- _Instructions for how to run the code and any associated tests_: If you've been working on your project it may seem obvious how to run it, but this will likely not be the case for someone coming across it for the first time.
- _Links to related material_
- _List of authors/contributors to the project, possibly with contact information_
- _Acknowledgements_

Supongamos que tienes la intención de que otras personas colaboren en tu proyecto (en lugar de poner tu código disponible y considerarlo completo). En ese caso, debe incluir las Directrices de Contribución y lo más probable, un Código de Conducta.

(rr-open-source-run-guidelines)=
### Contributing Guidelines

Las Directrices de contribución [{term}`def<Contributing Guidelines>`] informan a su audiencia cómo participar en su proyecto. Por ejemplo, puede incluir información sobre:

- How to file a bug report
- How to suggest a new feature
- Your roadmap or vision for the project
- How contributors should (or should not) get in touch with you

Utilizando un tono cálido y amigable y ofreciendo sugerencias específicas para contribuciones (como escribir documentación, o hacer un sitio web) puede hacer un largo camino para que los recién llegados se sientan bienvenidos y entusiasmados de participar. Por ejemplo, [Admin Activo](https://activeadmin.info/index.html) inicia su [guía de contribución](https://github.com/activeadmin/activeadmin/blob/master/CONTRIBUTING.md) con: "En primer lugar, gracias por considerar contribuir a Active Admin. Son personas como tú quienes hacen del Admin Activo una herramienta tan genial".

En las primeras etapas de su proyecto, su archivo de Directrices de Contribución puede ser sencillo. Siempre debe explicar cómo reportar errores o problemas de archivo, y cualquier requerimiento técnico (como pruebas) para hacer una contribución. Con el tiempo, puede añadir otras preguntas frecuentes aquí o en su archivo Léame . Escribir esta información significa que menos personas le harán las mismas preguntas una y otra vez. También es una buena idea enlazar con el archivo de guías de contribución de tu README, para que más gente lo vea.

(rr-open-source-run-conduct)=
### Code of Conduct

Un código de conducta [{term}`def<Code of Conduct>`] ayuda a establecer reglas básicas para el comportamiento de los participantes de su proyecto. Esto es especialmente valioso si está lanzando un proyecto de código abierto para una comunidad o empresa. Un Código de Conducta le permite facilitar un comportamiento comunitario saludable y constructivo, lo que reducirá su estrés como mantenedor. Se comunica cómo esperas que los participantes se comporten y describe a quién se aplican estas expectativas, cuando se apliquen, y qué hacer si se produce una violación.

Al igual que las licencias de código abierto, también hay estándares emergentes para los códigos de conducta, por lo que usted no tiene que escribir los suyos. El [Pacto de Colaboradores](https://contributor-covenant.org/) es un código de conducta desplegable que es utilizado por [más de 40.000 proyectos de código abierto](https://www.contributor-covenant.org/adopters). Sea cual sea el texto que utilice, debe estar preparado para hacer cumplir su Código de Conducta cuando sea necesario.

Mantenga el archivo en el directorio raíz de su proyecto, por lo que es fácil de encontrar y enlazarlo desde su README.

(rr-open-source-contribute)=
## How to Contribute to Other's Open Source Software Projects

(rr-open-source-contribute-anatomía)=
### Anatomy of an Open Source Software Project

Cada comunidad de código abierto es diferente. Dicho esto, muchos proyectos de software de código abierto siguen una estructura organizacional similar. Entendiendo los diferentes roles de la comunidad y el proceso general le ayudará a orientarse rápidamente a cualquier nuevo proyecto.

Un proyecto típico de software de código abierto tiene los siguientes tipos de personas:

- _Author_: The person/s or organization that created the project.
- _Owner_: The person/s who has administrative ownership over the organization or repository (not always the same as the original author).
- _Maintainers_: Contributors who are responsible for driving the vision and managing the organizational aspects of the project. They may also be authors and/or owners of the project.
- _Contributors_: Everyone who has contributed something back to the project.
- _Community Members_: People who use the project. They might be active in conversations or express their opinion on the project's direction.

Los proyectos más grandes también pueden tener subcomités o grupos de trabajo enfocados en diferentes tareas, como herramientas, triples, moderación de la comunidad y organización de eventos. Busque en la página web de un proyecto una página de “equipo” o en el repositorio para documentación de gobernanza, para encontrar esta información.

Un gran número de proyectos de código abierto están alojados en GitHub (ver el capítulo sobre control de versiones para más detalles), que tiene facilidades como:

- _Issue tracker_: Where people discuss issues related to the project.
- _Pull requests_: Where people discuss and review changes that are in progress.
- _Discussion forums or mailing lists_: Some projects may use these channels for conversational topics (for example, "How do I..." or "What do you think about..." instead of bug reports or feature requests). Others use the issue tracker for all conversations.
- _Synchronous chat channel_: Some projects use chat channels (such as Slack or IRC) for casual conversation, collaboration, and quick exchanges.

(rr-open-source-contribute-changes)=
### Contribute Your Changes

Digamos que has añadido una característica o corregido un error y quieres contribuir con este trabajo al proyecto principal.

1. _Read the documentation_: The main project may have contributing guidelines or information in a README instructing prospective contributors on how to supply their changes.
2. _Make sure your conventions match the style and structure of the main project_: For example, if all the variables in a project are named in some particular way yours should be too. Consistent conventions make it much easier for someone who has not seen your piece of the project before to understand it rather than having to figure out your particular set of conventions *and* what the code is doing. The project's conventions may be outlined in its documentation, or may just be evident from inspection of the code itself.
3. _Break your changes up into manageable, well-defined chunks_: For example, if you have added two separate features, do not submit them together. Keeping things "clean" in this way makes your work simpler to understand and review.
4. _Test your changes_: If the project comes with tests, run them. Make sure you are testing against an up to date version of the project as it may have evolved considerably over time. Write specific tests for your changes and submit those too.
5. _Do not just submit code, update relevant documentation too_: If your changes are incorporated, it will have to be updated. If you do not do it, someone else will have to.
6. _Ask questions_: If there are things you are unsure about, there is no harm in asking. Many larger projects have dedicated forums or other venues for questions and discussion.
7. _Be clear_: When you submit your changes, clearly describe the changes you have made, why you have made them, and how they have been implemented. This makes it as easier for someone looking at your work and deciding whether to incorporate it into the main project to do so. In the likely case the main project is hosted on GitHub, you should put this in the pull request (see the chapter {ref}`rr-vcs` for more details).

(rr-open-source-contribute-looking)=
### Looking for Projects to Contribute to and How to Contribute to Them

No hace falta exagerar cuál será exactamente su primera contribución, o cómo se verá. En su lugar, comience por pensar en los proyectos que ya utiliza o quiere utilizar. Los proyectos a los que contribuirás activamente son los a los que te encuentras volviendo. Dentro de esos proyectos, cada vez que te encuentras pensando que algo podría ser mejor o diferente, actúa según tu instinto. Puede escanear un README y encontrar un enlace roto o un error tipográfico. Alternativamente, usted podría ser un nuevo usuario y notar que algo está roto, o encontrar un problema que usted cree que debería estar en la documentación. En lugar de ignorarlo y seguir adelante, o pedir a alguien más que lo arregle, vea si puede ayudar entrando en él. De eso es de lo que trata el código abierto.

También puedes utilizar uno de los siguientes recursos para ayudarte a descubrir y contribuir a nuevos proyectos:

- [Open Source Friday](https://opensourcefriday.com/)
- [First Timers Only](https://www.firsttimersonly.com/)
- [CodeTriage](https://www.codetriage.com/)

Si no estás seguro de cómo empezar, hay otras formas de hacerlo como encontrar un problema abierto para abordar o preguntar si puede ayudar a escribir una nueva función.

Una idea errónea común sobre cómo contribuir a código abierto es que necesitas contribuir con código. De hecho, a menudo son las otras partes de un proyecto que se descuidan o se pasan por alto. Vas a hacer un gran favor al proyecto ofreciéndote a este tipo de contribuciones. Puedes:

- Review code on other people's submissions.
- Write and improve the project's documentation.
- Curate a folder of examples showing how the project is used.
- Answer questions about the project on, for example, Stack Overflow,
- Keep things organized, for example, on GitHub by:
    - Linking to duplicate issues.
    - Suggesting new issue labels.
    - Going through open issues and suggesting closing old ones.
    - Ask clarifying questions on recently opened issues to move the discussion forward.

(rr-open-source-closed)=
## Closed Software

¿Qué pasa si está trabajando con personas que no utilizan el modelo de código abierto para su software? Esto puede parecer en un principio un inconveniente para todos los principios debatidos hasta ahora. Sin embargo, por lo general hay muy buenas razones para que las cosas sean como son (por ejemplo, razones legales, comerciales o de seguridad). A menudo, todavía será posible utilizar y contribuir, pero los detalles de cómo podría ser diferente. Los tipos de prácticas utilizadas en el software "cerrado" son generalmente las mismas, y los conceptos y herramientas que puedes aprender en el Camino de Turing todavía aplican.

Sin embargo, a veces puede que no haya buenas razones para el enfoque de fuentes cerradas. Las diferentes áreas de investigación tienen diferentes culturas que van en contra de los principios abiertos y se sienten muy frustrantes. Abordar esta barrera puede ser muy complicado, ya que las culturas pueden tardar años o décadas en cambiar.

Trabajar con software cerrado puede ofrecer oportunidades y amenazas a su investigación. En todos los casos, comprender y respetar las perspectivas de los demás ofrece las mayores posibilidades de éxito.
