(rr-rdm-metadatos)=
# Documentación y metadatos

Tener datos disponibles no sirve de nada si no se puede entender. Por ejemplo, una tabla de números es inútil si no hay cabeceras que describan lo que contienen las columnas/filas. Por lo tanto, debe asegurarse de que los conjuntos de datos abiertos incluyan documentación.

## Documentación

La documentación proporciona un contexto para su trabajo. Permite a sus colaboradores, colegas y futuros comprender lo que se ha hecho y por qué. La documentación de datos se puede hacer a diferentes niveles. Toda la documentación que acompañe los datos debe estar escrita en un lenguaje claro y sencillo. La documentación permite a los usuarios de datos tener suficiente información para entender la fuente, fortalezas, debilidades, y limitaciones analíticas de los datos para que puedan tomar decisiones informadas al usarlo.

## Metadatos

Los metadatos son información acerca de los datos, descriptores que facilitan la catalogación de datos y el descubrimiento de datos. A menudo, los metadatos están destinados a la lectura de máquinas. Cuando los datos se envían a un repositorio de datos de confianza, los metadatos legibles por la máquina son generados por el repositorio. Si los datos no están en un repositorio se puede añadir un archivo de texto con metadatos legibles por la máquina como parte de la documentación.

- El tipo de investigación y la naturaleza de los datos también influyen en qué tipo de documentación es necesaria.
- El nivel de documentación y metadatos [{term}`def<Metadata>`] variará de acuerdo al proyecto, y el rango de personas por las que los datos deben ser entendidos.
- Ejemplos de documentación pueden incluir elementos como [diccionarios de datos](https://help.osf.io/hc/en-us/articles/360019739054-How-to-Make-a-Data-Dictionary) o códigos, protocolos bitácoras o revistas de laboratorio, archivos README, registros de investigación, sintaxis de análisis, algoritmos y comentarios de código.
- Las variables deben ser definidas y explicadas usando diccionarios de datos o códigos debooks.
- Los datos deben almacenarse en estructuras lógicas y jerárquicas de carpetas, con un archivo README usado para describir la estructura. El archivo README es útil para otros y también le ayudará a encontrar sus datos en la futura {cite:ps}`documentación de Fuchs2018`. Vea la plantilla [README de Cornell](https://cornell.app.box.com/v/ReadmeTemplate) para un ejemplo.
- Es una buena práctica utilizar estándares reconocidos de metadatos comunitarios para facilitar la combinación de conjuntos de datos.

(rr-rdm-metadata-estándares)=
### Estándares Comunitarios - Metadatos

El uso de estándares definidos por la comunidad para los metadatos es vital para la investigación reproducible y permite la comparación de datos heterogéneos de múltiples fuentes, dominios y disciplinas. Los estándares de metadatos son específicos de la disciplina. Por ejemplo, para los datos cerebros, la estructura de datos de imagen cerebral [](https://doi.org/10.25504/FAIRsharing.rd1j6t) es el estándar a utilizar. Sin embargo, no todas las disciplinas pueden usar estándares de metadatas. Puedes ver si tu disciplina utiliza estándares de metadatos a través de [FAIRsharing](https://fairsharing.org/), un recurso para identificar y citar los metadatos o esquemas de identificación, bases de datos o depósitos que existen para sus datos y disciplina. También hay situaciones en las que los investigadores utilizan estándares de metadatos más generales, por ejemplo, cuando utilizan un archivo genérico para almacenar sus datos, tienen que adherirse a los estándares de metadatos del archivo. En este caso, un archivo de texto con metadatos específicos de disciplina puede ser añadido como parte de la documentación.
