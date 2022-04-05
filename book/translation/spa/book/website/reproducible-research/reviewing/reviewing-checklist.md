(rr-checklist-for-code-review)=
# Checklist for code review process

This section presents some checklists for both the coder and the reviewer, as part of a formal review process. The reviewer checklists are split into two categories: one for the whole program, and one for individual files or proposed changes.

The lists are created with a focus on good software engineering practice and are intended to be a source of inspiration. When assessing the checklists, it is recommended to consider to what extent the item mentioned is implemented. Some items on the lists may not apply to your project or programming language, in which case they should be disregarded.

In all cases, the goal is to use your programming experience to figure out how to make the code better.

## For the coder

- Compruebe los estándares requeridos del proyecto. Los estándares normalmente están escritos en `pautas de contribución` por el proyecto al que estás contribuyendo.
- Is there [documentation](#documentation) that meets the required standards of the project?
- Are you following any declared {ref}`style guide<rr-code-quality>` for the project?
- Are there new [tests](#tests) for the new material, based on the required standards of the project?
  - Do these tests pass locally?
  - Are the tests in the rest of the code base still passing locally?
- Create the pull request.
- Many {ref}`continuous integration (CI)<rr-ci>` systems will check if the tests in the main project pass automatically once you create a pull request. If the repository is using a CI, make sure all builds and tests complete. Consult the CI reports to see if your code is causing the tests in the main project to fail.
- If necessary, now formally request a review.

## For the reviewer

- Check the required standards of the project. ¿Cumple el nuevo código con los estándares requeridos del proyecto? Los estándares normalmente están escritos bajo `pautas de contribución` por el proyecto al que estás contribuyendo.
- Check the code meets basic project {ref}`style guide<rr-code-quality>`, if this is not automatically checked by {ref}`continuous integration (CI)<rr-ci>`.
- Do the [tests](#tests) and [documentation](#documentation) conform to the standards?
- Is all the code easily understood? Depending on the language, files may contain interfaces, classes or other type definitions, and functions (see [Architecture](#architecture)). The essential architectural concepts can be reviewed as follows:
  - Check the [interfaces](#interfaces) lists.
  - Check the [classes and types](#classes-and-types) lists.
  - Check the [function/method declarations](#function-method-declarations) lists.
  - Check the [function/method definitions](#function-method-definitions) lists.
- Do the [tests](#tests) actually ensure the code is robust in its intended use?
  - Are there any bugs or other defects?
- Are [security](#security) issues handled correctly?
  - Check the [security of new codes](#security-of-new-codes).
- Does the new code meet the [legal requirements](#legal)?

## Program level checklist

Aquí hay una lista de cosas a tener en cuenta al considerar el programa como un todo, en lugar de mirar un archivo individual o un cambio.

### Documentation

Documentation is a prerequisite for using, developing, and reviewing the program. Alguien que no esté involucrado con tu proyecto debería entender lo que hace tu código, y qué enfoque estás tomando. Here are some things to check for.

- Is there a description of the purpose of the program or library?
- Are detailed requirements listed?
- Are requirements ranked according to [MoSCoW](https://en.wikipedia.org/wiki/MoSCoW_method)?
- Is the use and function of third-party libraries documented?
- ¿Está documentada la estructura/arquitectura del programa? (ver abajo) (see below)
- Is there an installation manual?
- Is there a user manual?
- Is there documentation on how to contribute?
  - Including how to submit changes
  - Including how to document your changes

### Architecture

Estos artículos son principalmente importantes para programas más grandes, pero pueden ser buenos para considerarlos también para los pequeños.

- Is the program split up into clearly separated modules?
- Are these modules as small as they can be?
- ¿Hay una estructura de dependencia clara, jerárquica o por capas, entre estos módulos?
  - Si no es así, la funcionalidad debería reorganizarse, o tal vez se deberían combinar módulos interdependientes.
- Can the design be simplified?

### Security

Si está haciendo software accesible al mundo exterior (por ejemplo, una aplicación web ), entonces la seguridad es importante. Los problemas de seguridad son defectos, pero no todos los defectos son problemas de seguridad. Un diseño consciente de seguridad puede ayudar a mitigar el impacto de seguridad de los defectos.

- Which modules deal with user input?
- Which modules generate output?
- Are input and output compartmentalized?
  - Si no, considera hacer módulos separados que gestionan toda la entrada y la salida, así que la validación puede ocurrir en un solo lugar.
- In which modules is untrusted data present?
  - The fewer the better.
- Is untrusted data compartmentalized?
  - Idealmente, valida en el módulo de entrada y pasa solo datos validados a otras partes.

### Legal

Como desarrollador, deberías prestar atención a los derechos legales de los creadores del código que estás usando. Here are some things to check. Cuando tengas dudas, pídele consejo a alguien con experiencia en licencias.

- Are the licenses of all modules/libraries that are used documented?
- Are the requirements set by those licenses fulfilled?
  - Are the licenses included where needed?
  - Are copyright statements included in the code where needed?
  - Are copyright statements included in the documentation where needed?
- Are the licenses of all the parts compatible with each other?
- Is the project license compatible with all libraries?

## File/Change level checklist

Cuando está comprobando cambios o archivos individuales en una solicitud de extracción, el código en sí mismo se convierte en objeto de escrutinio. Dependiendo del idioma, los archivos pueden contener interfaces, clases u otras definiciones de tipo y funciones. Todas estas deben ser revisadas.

### Interfaces

- Is the interface documented?
- Does the concept it models make sense?
- Can it be split up further? (Interfaces should be as small as possible)

Ten en cuenta que la mayoría de los siguientes elementos asumen un estilo de programación orientada a objetos , el cual puede no ser relevante para el código que estás buscando.

### Classes and types

- Is the class documented?
  - Are external programs needed by the class documented?
- Does it have a single responsibility? Can it be split?
- If it's designed to be extended, can it be?
- If it's not designed to be extended, is it protected against that?
- If it's derived from another class, can you substitute an object of this class for one of its parent class(es)?
- Is the class testable?
  - Are the dependencies clear and explicit?
  - Does it have a small number of dependencies?
  - Does it depend on interfaces, rather than on classes?

### Function/Method declarations

- Are there comments that describe the intent of the function or method?
- Are input and output documented? Including units?
- Are pre- and postconditions documented?
- Are edge cases and unusual things commented?

### Function/Method definitions

- Are edge cases and unusual things commented?
- Is there any incomplete code?
- Could this function be split up (is it not too long)?
- Does it work? ¿Funciona? Realizar la función prevista, lógica correcta, ...
- Is it easy to understand?
- Is there redundant or duplicate code? (DRY)
- Do loops have a set length and do they terminate correctly?
- Can debugging or logging code be removed?
- Can any of the code be replaced by library functions?

### Security of new codes

- If you're using a library, do you check errors it returns?
- Are all data inputs checked?
- Are output values checked and encoded properly?
- Are invalid parameters handled correctly?

### Tests

- Do unit tests actually test what they are supposed to?
- Is bounds checking being done?
- Is a test framework and/or library used?
