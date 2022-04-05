msgid "" msgstr "" "Project-Id-Version: content\n" "Report-Msgid-Bugs-To: https://github.com/haiwen/seafile-docs/issues\n" "POT-Creation-Date: 2020-02-05 19:08:03+0000\n" "PO-Revision-Date: 2020-04-07 14:21+0000\n" "Last-Translator: Alejandro © <acoca@turing.ac.uk>, 2021\n" "Language-Team: Spanish (https://www.transifex.com/theturingway/teams/107194/es/)\n" "MIME-Version: 1.0\n" "Content-Type: text/plain; charset=UTF-8\n" "Content-Transfer-Encoding: 8bit\n" "Language: es\n" "Plural-Forms: nplurals=2; plural=(n != 1);\n"
# BinderHub

## Prerequisites/recommended skill level

| Prerequisite                                    | Importance     |
| ----------------------------------------------- | -------------- |
| {ref}`Version Control<rr-vcs>`            | Very Important |
| {ref}`Reproducible Environments<rr-renv>` | Very Important |

msgid "" "We will cover the technologies and tools that BinderHub utilises and the " "resources you will need to setup your own BinderHub." msgstr "" "Abarcaremos las tecnologías y herramientas que utiliza BinderHub y los " "recursos que necesitarás para configurar tu propio BinderHub."

msgid "" "This chapter is primarily aimed at Research Software Engineers and IT " "Services who wish to provide a BinderHub as a service to a group of " "researchers." msgstr "" "Este capítulo está dirigido principalmente a especialistas en ingeniería de " "sistemas y servicios de TI que deseen proporcionar un BinderHub como " "servicio a un grupo de investigadores."

```{figure} ../figures/binderhub.jpg
---
name: binderhub
alt: A representation of the BinderHub architecture that involves GitHub, repo2docker, docker, jupyterhub and shipping to clients in company.
|"
msgstr ""
"| Una representación de la arquitectura de BinderHub.
_The Turing Way_ project illustration by Scriberia. Used under a CC-BY 4.0 licence. DOI: 10.5281/zenodo.3332807.
```

## Motivation

msgid "" "Reading this chapter will give you a clearer picture of how Binder services " "(such as [mybinder.org](https://mybinder.org)) operate, the technologies " "powering BinderHub and how they interact with one another." msgstr "" "La lectura de este capítulo te dará una idea más clara de cómo funcionan los" " servicios de Binder ([mybinder.org](https://mybinder.org)), las tecnologías" " que impulsan BinderHub y cómo interactúan entre sí."
