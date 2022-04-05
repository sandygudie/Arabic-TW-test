# Advanced Structure for Data Analysis

## Prerequisites/Recommended Skill Level

| Prerequisite                                    | Importance | Notes                                           |
| ----------------------------------------------- | ---------- | ----------------------------------------------- |
| {ref}`Version Control<rr-vcs>`            | Helpful    | Knowledge of using git for version control      |
| {ref}`Open Research<rr-open>`             | Helpful    | Components are part of the compendium           |
| {ref}`Reproducible Environments<rr-renv>` | Helpful    | Can be used to make the compendium reproducible |

## Summary

When planning out a research study, one crucial and often forgotten component is setting up a repository. In this section, the benefits and considerations of designing a repository will be outlined, along with an example structure and further resources to guide your workflow.

The prerequisites for this chapter can vary depending on the organisational needs of a project. Creating a repository with a simple research project layout can require minimal technical knowledge (such as managing only input data and output results). Meanwhile, advanced repository layouts can be required for more complicated projects (such as projects with dependencies on other projects).

## Background

A repository (or a "repo") is a storage location for your research project. A repository can contain a range of digital objects and can be used to store your project by using online platforms such as GitHub. The aim of a repository is to organise your project in such a way this is both accessible to others and efficient to use.

So far, we saw the key documents that one should add when starting or setting up a project repository. If you are following along, your project should contain the following files:

```
Project Folder/
├── CODE_OF_CONDUCT          <- Code of Conduct for community projects
├── CONTRIBUTING             <- Contribution guideline for collaborators
├── LICENSE                  <- software license
├── ...                      <- any other files that you may have added for your project
└── README.md                <- information about the repo
```

In this subchapter, we outline the benefits and considerations of designing a repository, along with an example structure and further resources to guide your workflow.

```{note}
The main benefit of designing your repository by intentionally adding documentation, resources and relevant information allows creating an infrastructure for ethical, open and high-quality research from the get-go.
```

## Main Considerations

When sharing your resources via your repository, consider the following aspects of reproducibility in your research:

- Transparency and openness
- Version control system (no more files like final_v1_FINAL.R, final_v2_FINAL.R, ...)
- Make it easy to navigate so that you save time for everyone involved
- Consider {ref}`pd-overview-repro` aspects
- Make sure that you provide sufficient details so that others can build on your work

## Main Recommendations

Always consider designing your project for collaboration by adding key documents describing project goals, vision, roadmap, contribution and communication process (as described in earlier subchapters).
- Include details in {ref}`README file<pd-project-repo-readme>`describing _what_ the repository is for and _how_ to navigate it
- Provide vision, goals and roadmap wherever possible (see [Kamran Ahmed's developer roadmap](https://github.com/kamranahmedse/developer-roadmap) for example)
- General structure should separate input (data), methods (scripts) and output (results, figures, manuscript)
- Specify what shouldn't be tracked in the `.gitignore` file, such as sensitive/private files, large dataset or personal notes
- Include information on your computational environment {ref}`Reproducible Environments<rr-renv>` to ensure reproducibility (this can also be specified in the README)

## Example Repository Structure

### Example for a Research Project

Here are suggestion of files and folders a research project must have.

```
Project Folder/
├── docs                     <- documentation
│   └── codelist.txt 
│   └── project_plan.txt
│   └── ...
│   └── deliverables.txt
├── data
│   └── raw/
│       └── my_data.csv
│   └── clean/
│       └── data_clean.csv
├── analysis                 <- scripts
│   └── my_script.R
├── results                  <- analysis output     
│   └── figures
├── .gitignore               <- files excluded from git version control 
├── install. R                <- environment setup
├── CODE_OF_CONDUCT          <- Code of Conduct for community projects
├── CONTRIBUTING             <- Contribution guideline for collaborators
├── LICENSE                  <- software license
├── README.md                <- information about the repo
└── report.md                <- report of project
```

### Example with Every Possible Folder

This example shows different files and directory a project can contain when building a software application or research engineering tools.

```
Carpeta de Proyecto/                        
Ningun análisis                 <- secuencias de comandos
mañana: my_script. ► Compilación                    <- archivos construidos, Makefile
| mañanotidiano debug
| mañana: lanzamiento
mañanos-datos
mañana/raw/
mañana-mi_data. sv
→ Limpieza/
tópica_limpia de datos. sv
→ Documentos                     <- documentación
✓ Codelist. xt 
→ Gestión de proyectos       <- Documentos relacionados con la gestión de proyectos
- Comunicación. d
ochté.md
oz. project-report.md
ooz. tools. d
✫ :/=$ res                      <- recursos estáticos (imágenes y archivos de audio)
mañanas: figuras
ful. itignore               <- archivos excluidos del control de la versión de git 
✓ CODE_OF_CONDUCT          <- Código de Conducta para los proyectos de la comunidad
aficiones             <CONTRIBUTING < - Guía de colaboración para los colaboradores
lib de facto                      <- dependencias (componentes compartidos que pueden ser utilizados a través de una aplicación o a través de proyectos, código que soporta la aplicación básica)
registros. xt                 <- historial de todas las actualizaciones importantes como versión de características, corrección de errores, Actualizaciones
✓ ejemplo                  <- aplicación de código de ejemplo
→ LICENSE                  <- licencia de software
✓ ambiente. ml          <- configuración de entorno anaconda   
☆ install. <- Configuración de entorno R
Requisitos de 2020. xt         <- configuración de entorno de python
(tiempo de ejecución). xt              <- R en la configuración de binder
report. d                <- informe de análisis
☆ README. d                <- información sobre el repo
☆ src                      <- archivos fuente
→ Prueba                     <- pruebas unitarias  
```

## Resources

### R and Python Packages

| R                                                                 | Python                                                       |
| ----------------------------------------------------------------- | ------------------------------------------------------------ |
| [rrtools](https://annakrystalli.me/rrresearch/10_compendium.html) | [compendium-dodo](https://pypi.org/project/compendium-dodo/) |
| [template](https://github.com/Pakillo/template)                   | [css-compendium](https://pypi.org/project/ccs-compendium/)   |
| [rcompendia](https://github.com/FRBCesab/rcompendium)             |                                                              |
| [remake](https://github.com/richfitz/remake)                      |                                                              |

### Curated Examples of GitHub Repositories

- [_The Turing Way_ project repo](https://github.com/alan-turing-institute/the-turing-way)
- [Jupyter Book project repo](https://github.com/executablebooks/jupyter-book)
- [Pandas Package repo](https://github.com/pandas-dev/pandas)
- [Atom Text Editor repo](https://github.com/atom/atom)

For more details, please follow {ref}`project-repo-recommendations-advanced`.
