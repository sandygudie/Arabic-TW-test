(liaison)=
# Binder

Dans ce chapitre, nous discuterons de Project Binder et mybinder.org comme moyen de partager la recherche de manière transparente et interactive.

(binder-share)=
## Pourquoi devriez-vous partager votre travail?

La motivation pour le partage des résultats de recherche est explorée plus en profondeur dans le chapitre {ref}`ouvert`.

En bref, le partage de votre code de recherche peut aider à fournir un contexte aux résultats que vous présentez en illustrant le processus que vous avez parcouru pour les atteindre. En partageant le code nous évitons également de réinventer la roue afin de progresser sur un sujet de recherche puisque les outils précédents sont disponibles pour être construits sur le dessus.

Cependant, le plus grand obstacle au partage de code est souvent l'installation de paquets et la mise en place de l'environnement informatique, comme nous le verrons dans la section suivante. En partageant votre travail via des plates-formes telles que mybinder.org:

- L'installation de paquets logiciels n'est plus un défi
- Les personnes utilisant différents systèmes d'exploitation ont des expériences similaires depuis le calcul sur la plate-forme, pas sur leur machine locale
- Votre travail peut être distribué à un public plus large puisque la barrière technique a été abaissée

(binder-quoi)=
## Qu'est-ce que le lien de projet ?

Nous avons discuté des raisons pour lesquelles il est important de partager votre travail et nous sommes arrivés à un point où nous avons décidé de publier des cahiers Jupyter avec du code d'analyse sur une plate-forme de collaboration, comme GitHub.

GitHub est une excellente plateforme pour partager du code _statiquement_. Si le dépôt est public, n'importe qui peut accéder à votre bloc-notes et lire le contenu. Cependant, le code _en cours d'exécution_ est beaucoup plus compliqué que de l'afficher comme GitHub. Beaucoup de parties interdépendantes sont nécessaires pour exécuter du code, par exemple :

- une copie du code lui-même;
- le logiciel approprié pour l'exécuter ;
- tous les paquets supplémentaires dont le code dépend de ceux qui ne sont pas expédiés dans le logiciel de base ;
- toute donnée d'entrée que l'analyse requière;
- et vous avez également besoin de matériel (un ordinateur !) pour le faire fonctionner.

En plus d'acquérir toutes ces pièces, vous devez également les installer correctement et de manière à ce qu'ils ne soient pas influencés ou entrent en conflit avec d'autres logiciels qui peuvent fonctionner sur votre machine. C'est beaucoup de travail !

Combien plus facile serait-il si nous pouvions **exécuter du code dans le navigateur**, similaire à la façon dont il est affiché ? C'est ce que le Project Binder vise à réaliser.

Project Binder fournit à un utilisateur l'infrastructure suivante :

- du matériel pour exécuter du code, généralement un serveur hébergé dans le cloud, mais peut également être sur place ;
- un environnement de calcul contenant :
  - le logiciel d'évaluation
  - les dépendances supplémentaires du paquet,
  - toutes les données de saisie requises,
  - et une copie du code lui-même (blocs-notes ou scripts);
- une URL à l'endroit où l'environnement est en cours d'exécution pour que le code puisse être interagit avec vous ou vos collaborateurs.

Project Binder a rassemblé toutes les pièces mobiles qui rendent difficile le partage du travail informatique dans une interface simple à utiliser. Il y a une version **libre et publique** de cette interface fonctionnant à [**mybinder.org**](https://mybinder.org).

Le dessin animé ci-dessous, par Juliette Taka, démontre un workflow un que les scientifiques qui utilisent Binder pourraient adopter.

```{figure} ../figures/binder-comic.png
---
nom : binder_comic
alt : Une illustration des pas qu'une personne peut prendre pour créer un projet lié.
---
Crédit de figure : [Juliette Taka, Logilab et le projet OpenDreamKit](https://opendreamkit.org/2017/11/02/use-case-publishing-reproducible-notebooks/)
```

Vous pouvez en savoir plus sur Project Binder et mybinder.org sur leur [page à propos de mybinder.org](https://mybinder.readthedocs.io/en/latest/about/about.html).

(liaison-disam)=
### Désambiguïté

Dans cette section, il y a des termes connexes qui seront décrits ici pour plus de clarté:

- **Binder de projet**: Une communauté ouverte qui permet de créer des environnements partagés, interactifs et reproductibles. La sortie technologique de ce projet est un hub {ref}`rr-binderhub`.
- **BinderHub**: Une infrastructure basée sur les nuages pour générer des liaisons. Le plus largement utilisé est [mybinder.org](https://mybinder.org), qui est maintenu par l'équipe de Project Binder. Il est construit sur une gamme d'outils open source, y compris [JupyterHub](https://z2jh.jupyter.org), pour fournir des ressources de calcul cloud aux utilisateurs via un navigateur; et [`repo2docker`](https://repo2docker.readthedocs.io/), pour construire des images docker à partir de projets. Comme il s'agit d'un projet ouvert, il est possible de créer d'autres BinderHubs qui peuvent supporter des configurations plus spécialisées. Une telle configuration pourrait inclure l'authentification pour permettre le partage de dépôts privés entre des collaborateurs proches.
- **A Binder**: Une version partageable d'un projet qui peut être visualisée et interagir dans un environnement informatique reproductible fonctionnant dans le cloud via un navigateur Web. En automatisant l'installation de l'environnement informatique (tel que décrit dans le chapitre {ref}`rr-renv` ), Project Binder transforme le coût du partage d'un tel environnement en acte de partage d'une URL.
- **[mybinder.org](https://mybinder.org)**: Un BinderHub public et libre. Parce qu'il est public, vous ne devriez pas l'utiliser si votre projet nécessite des informations personnelles ou sensibles (comme des mots de passe).
- **Binderize**: Le processus de faire un lieur à partir d'un projet.

(binder-approprié)=
## Quand est-il approprié d'utiliser mybinder.org?

Maintenir un service gratuit et anonyme dans le nuage est beaucoup de travail bénévole et coûte beaucoup d'argent. Afin de réduire quelque peu les coûts de fonctionnement, mybinder.org place des restrictions de calcul sur chaque instance de Binder. Ces restrictions sont :

- 1 CPU, et
- 1 Go de RAM.

Par conséquent, mybinder.org n'est **pas un endroit approprié** pour effectuer des réplications de bout en bout des flux de travail d'apprentissage automatique, par exemple !

Et c'est la raison principale pour laquelle ce chapitre sur Binder a été placé dans le "Guide pour la Communication". Avec ces restrictions informatiques, mybinder.org se prête très bien à l'hébergement de démonstrations interactives et de ressources d'apprentissage pour des paquets logiciels ou des analyses de recherche. Dans ce scénario, les personnes qui cliquent sur le lien Lier veulent probablement apprendre quelque chose, et rester assis dans un processus de formation de modèle qui demande du temps ne les aidera probablement pas à y parvenir. Au lieu de cela, vous pouvez fournir des modèles pré-formés ou des instructions sur la façon de former les modèles sur leur propre matériel et _revenez_ sur le Binder pour le reste du tutoriel interactif.

Alors, quand est-il approprié d'utiliser mybinder.org?

- Quand vous voulez _communiquer_ quelque chose de manière interactive, comme des analyses courtes, des tutoriels ou même des blogs ! Check out [Achintya Rao's blog powered by mybinder.org](https://blog.achintyarao.in/about/)!
- Lorsque le code et les données associées (le cas échéant) sont publiquement disponibles
- Lorsque le code que vous voulez exécuter interactivement ne nécessite pas beaucoup de ressources ou de ressources spécialisées (par exemple, GPUs)

(binder-faqs)=
## Foire aux questions

De nombreuses questions courantes sont résolues sur la [page à propos de mybinder.org](https://mybinder.readthedocs.io/en/latest/about/about.html).

### Comment enregistrer mes modifications dans mon référentiel ?

Malheureusement, vous ne pouvez pas le faire. Au moins, pas à partir de la ligne de commande dans une instance Binder en cours d'exécution.

Écriture vers un dépôt hébergé, que ce soit sur GitHub ou une autre plate-forme, nécessitera un identifiant de quelque nature que ce soit pour vous autoriser à écrire dans ce référentiel. Et comme cela a été dit, mybinder. rg est un service entièrement public et vous ne devez fournir aucune information sensible à une instance Binder en cours d'exécution en aucune circonstance.

Cependant, mylider. rg exécute un module appelé [`jupyter-offlinenotebook`](https://github.com/manics/jupyter-offlinenotebook) qui fournit un bouton de téléchargement pour enregistrer vos notebooks localement, _même si votre navigateur a perdu sa connexion avec l'infrastructure cloud qui fournit le calcul!_ Cela signifie que vous pouvez enregistrer votre progression localement, mettez à jour votre dépôt avec vos cahiers sauvegardés et relancez votre binder avec les cahiers mis à jour.

```{figure} ../figures/binder_notebook_banner.jpg
---
name : lider_notebook_banner
alt: Une capture d'écran du panneau de contrôle d'un Notebook Jupyter avec un bouton de téléchargement surligné par un rectangle violet.
---
Utiliser ce bouton "Télécharger" dans un bloc-notes Jupyter fonctionnant sur mybinder. rg vous permettra d'enregistrer vos blocs-notes localement, même après que l'instance Binder ait été déconnectée des ressources de calcul.
```

### Comment puis-je collaborer avec mes pairs sur mybinder.org?

Ce n'est pas impossible, mais il y a certainement de la place pour développer cette fonctionnalité par rapport aux autres services de "cloud compute" disponibles.

Ceux qui sont intéressés par ceci, peut en savoir plus dans [ce post de Discourse](https://discourse.jupyter.org/t/collaborating-on-one-binder-instance/407) et dans le [`jupyterlab-link-share` repository](https://github.com/jtpio/jupyterlab-link-share).

### En quoi mybinder.org est-il différent de Google Colab?

Google Colab fournit un environnement informatique « évier de cuisine » avec de nombreux logiciels de données parmi les plus populaires préinstallés. En revanche, mybinder.org construit des images sur mesure pour chaque dépôt lancé, en installant spécifiquement les paquets répertoriés dans vos fichiers de configuration.

### Puis-je me connecter au `FOURNISSEUR DE DONNÉES ICI`?

Les connexions réseau sur mybinder.org sont assez limitées à des fins de sécurité et de prévention des abus. Cela étant dit, vous devriez être en mesure de vous connecter à un fournisseur de données externe pour autant qu'il réponde aux deux critères suivants :

- Il est accessible via une connexion HTTP/HTTPS
- Vous n'avez pas besoin d'identifiants pour accéder aux données

Rappelez-vous que mybinder.org est un service entièrement public et que vous ne devez en aucun cas fournir à une instance de Binder des renseignements confidentiels, tels que des titres de compétence.

(relief-segue)=
## Comment créer un projet prêt pour le Binder

Le prochain chapitre contient un tutoriel [Zéro à Binder](z2b) qui vous guidera dans la création de votre premier projet sur GitHub.
