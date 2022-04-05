(rr-code-reuse-recomendaciones)=
# Resumen de reutilización de código

This section contains a checklist of recommendations for making your software more reusable. La sección {ref}`rr-code-reuse-details` contiene una explicación más detallada de cada una de estas recomendaciones. You can follow the recommendations that are more suitable for your type of software and skip the ones which are not relevant in your case.

## Recomendaciones repetibles

1. Asegúrese de encontrarlo (en el espacio; significando: ser capaz de localizar el repositorio/proyecto)
1. Asegúrese de encontrarlo (en el tiempo; significando: ser capaz de localizar una versión en particular)
1. Make sure you can execute the same sequence of operations
1. Make sure your environment and sequence of operations is robust and no human is needed to replicate what was done
1. License your code
    - with a license that allows for reuse;
    - with a license compatible with the dependencies’ licenses
1. Make sure it is citable
1. Include necessary data
1. Write useful documentation*

## Recomendaciones reejecutables

1. Remueve bits codificados (tales como rutas que sólo existían en el disco duro donde se ejecutaba el pipeline) y crea el código modular
1. Test that the modules you made can take different types of input data or parameters
1. Turn the modules into a package/toolbox
1. Write useful documentation*

## Recomendaciones portátiles
1. Make sure you can recreate the environment where it lived
1. Write useful documentation*

## Recomendaciones extendidas
1. Write useful documentation*

## Recomendaciones modificables
1. Make sure your code is readable by humans
1. Make sure comments are present
1. Write useful documentation*

The observant reader might will notice that `Write useful documentation` is mentioned for every level of reuse. This is because different levels of documentation are required for different levels of reuse.

## Documentation

*Different documentation requirements for different levels of reuse*

Writing useful documentation is an important requirement for all levels of reuse. However, for the different levels of reuse, there are different documentation requirements:

The documentation:
- explains usage, specifying:
  - what the software does; (required for repeatable)
  - how it can be used; (required for repeatable)
  - what options/parameters are available. (required for repeatable)
- contains examples of how to run it. (required for repeatable)
- has installation instructions, including good descriptions of:
  - the hardware it depends on (for example GPUs); (required for portable)
  - the operating system the software has been tested on; (required for portable)
  - software requirements (such as libraries and shell settings). (required for portable)
