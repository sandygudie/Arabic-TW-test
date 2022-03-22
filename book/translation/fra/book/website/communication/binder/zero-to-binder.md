(z2b)=
# Zéro à lier

Dans ce chapitre, nous allons créer un projet Binder à partir de zéro : nous allons d'abord créer un dépôt sur GitHub et ensuite nous lancerons sur mybinder.org. Les sections où vous devez terminer une tâche sont désignées par trois feux de circulation : vertical_traffic_light: emojis. Certaines étapes vous donnent l'option de Python, Julia ou R - cliquez sur l'onglet de votre langue préférée.

```{admonition} Attributions
Ce tutoriel est basé sur les ateliers _Zero-to-Binder_ de Tim Head qui peuvent être trouvés ici : <http://bit.ly/zero-to-binder> et <http://bit.ly/zero-to-binder-rise>

Merci à Anna Krystalli et Oliver Strickson pour leur aide au développement du contenu R et Julia. respectivement.
```

```{attention}
Binder peut prendre beaucoup de temps à charger, mais cela ne signifie pas nécessairement que votre Binder ne sera pas lancé.
Vous pouvez toujours actualiser la fenêtre si vous voyez le message "... prend plus de temps à charger, accrocher serré!" .
```

```{admonition} If you are using R...
Si vous suivez le chemin R, nous avons inclus quelques étapes alternatives en utilisant le paquet [`holepunch`](https://github. om/karthik/holepunch) qui construira votre environnement en utilisant une [image de base de rocker](https://github.com/rocker-org/rocker) et devrait, en fin de compte, être plus rapide à construire et à lancer.
```

(z2b-reqs)=
## Exigences

Vous aurez besoin de :

- **Quelques codes et quelques données.** Le code doit prendre moins de **10 minutes à exécuter**, et les données doivent être inférieures à **10 Mo**. Cela peut signifier que vous ne choisissez qu'un script dans un projet plus vaste, ou que vous apportez un sous-ensemble de vos données. Notez qu'il est vraiment important que le code et les données puissent être rendus **publics** car nous allons utiliser l'instance du lieur public.
- **Un compte GitHub.** Veuillez en créer un si vous n'en avez pas déjà un: <https://github.com/join>

(z2b-step-1)=
## 1. Créer un dépôt pour Binderize

🚦🚦🚦

````{tabbed} Python
1) Créer un nouveau dépôt sur GitHub appelé "mon-premier-lien"
   - Assurez-vous que le dépôt est **public**, _pas privé_!
   - N'oubliez pas d'initialiser le dépôt avec un README !
2) Créez un fichier appelé `hello.py` via l'interface web avec `print("Bonjour de Binder!")` sur la première ligne et validez sur la branche `main`
````

````{tabbed} Julia
1) Créer un nouveau dépôt sur GitHub appelé "mon-premier-lien"
   - Assurez-vous que le dépôt est **public**, _pas privé_!
   - N'oubliez pas d'initialiser le dépôt avec un README !
2) Créer un fichier appelé `Bonjour. l` via l'interface web avec `println("Bonjour de Binder! )` sur la première ligne et commit sur la branche `main`
3) Créez un fichier appelé `Project. oml` (ATTENTION: la capitalisation est importante !) avec le contenu suivant et l'engage dans `main`.
   Ceci installera Julia dans l'environnement de Binder.

   ```julia
   [compat]
   julia = "1.3"
```
````

````{tabbed} R
1) Créer un nouveau dépôt sur GitHub appelé "mon-premier-lien"
   - Assurez-vous que le dépôt est **public**, _pas privé_!
   - N'oubliez pas d'initialiser le dépôt avec un README !
2) Créer un fichier appelé `Bonjour. ` via l'interface web avec `print("Bonjour de Binder! )` sur la première ligne et commit sur la branche `main`
3) Créer un fichier appelé `runtime. xt` avec `r-2022-01-01` sur la première ligne.
   Cette date représente le instantané de [CRAN](https://cran.r-project.org/) hébergé sur [RStudio Package Manager](https://packagemanager.rstudio.com) que nous allons utiliser.
   Valider ce fichier dans la branche `main`.

   ```{note}
   En R, vous pouvez utiliser `holepunch::write_runtime()` pour créer un `runtime.txt` dans le répertoire `.binder/`; il sera configuré avec la date d'aujourd'hui.
   ```
````
(z2b-public-dépôt)=
### Pourquoi le dépôt doit-il être public ?
mybinder.org ne peut pas accéder aux dépôts privés car cela nécessiterait un jeton secret. L'équipe de Binder a choisi de ne pas assumer la responsabilité de manipuler les jetons secrets, car mybinder.org est un service public et une preuve du concept technologique. Si accéder à des dépôts privés est une fonctionnalité dont vous avez besoin/votre équipe, nous vous conseillons de construire votre propre [BinderHub](https://binderhub.readthedocs.io).
(z2b-step-2)=
## 2. Lancez votre premier dépôt !
🚦🚦🚦
1) Allez sur **<https://mybinder.org>** 2) Tapez l'URL de votre dépôt dans la zone "Dépôt ou URL GitHub". Cela devrait ressembler à ceci:
> **https://github.com/YOUR-USERNAME/my-first-binder** 3) Au fur et à mesure que vous tapez, la page Web génère un lien dans le "Copier l'URL ci-dessous. ." box Cela devrait ressembler à ceci : **https://mybinder. rg/v2/gh/VOTRE USERNAME/mon-premier-lieur/tête** 4) Copiez-le, ouvrir un nouvel onglet du navigateur et visiter cette URL - Vous verrez un "spinner" lorsque Binder lance le dépôt
Si tout s'est bien déroulé, vous verrez une interface JupyterLab.
(z2b-arrière-plan-1)=
### Que se passe-t-il en arrière-plan ? - Partie 1
En attendant, BinderHub (backend of Binder) est :
- Récupération de votre dépôt depuis GitHub
- Analyse du contenu
- Construire une image Docker basée sur votre dépôt
- Lancement de cette image Docker dans le cloud
- Connexion à celle-ci via votre navigateur
(z2b-step-3)=
## 3. Exécuter le script
🚦🚦🚦

````{tabbed} Python
1. Dans le panneau de lancement, sélectionnez "Terminal"
2. Dans la nouvelle fenêtre de terminal, tapez `python hello.py` et appuyez sur "Retour"
````

````{tabbed} Julia
1. Dans le panneau de lancement, sélectionnez "Terminal"
2. Dans la nouvelle fenêtre de terminal, tapez `julia hello.jl` et appuyez sur "Retour"
````

````{tabbed} R
1. Dans le panneau de lancement, sélectionnez "Terminal"
2. Dans la nouvelle fenêtre de terminal, tapez `Rscript -e 'source("Bonjour.R)'` puis appuyez sur "Retour"
````

`Bonjour de Binder !` doit être imprimé sur le terminal.

(z2b-step-4)=
## 4. Épinglage des Dépendances

Il a été facile de commencer, mais notre environnement est nu - ajoutons une **dépendance**!

🚦🚦🚦

````{tabbed} Python
1) Dans votre dépôt, créez un fichier appelé `requirements.txt`
2) Ajoutez une ligne qui dit : `numpy==1.14.5`
3) Vérifiez s'il y a des fautes ! Puis commit sur la branche `main`
4) Visitez **https://mybinder.org/v2/gh/YOUR-USERNAME/my-first-binder/HEAD** dans un nouvel onglet
````

````{tabbed} Julia
1) Dans votre dépôt, éditez le `Projet. oml` fichier
2) Ajoute un nouveau bloc qui dit :

   ```julia
   [deps]
   CSV = "336ed68f-0bac-5ca0-87d4-7b16caf5d00b"
   ```

3) Vérifie les typos ! Puis soumettez à `main`.
4) Rendez-vous sur **https://mybinder.org/v2/gh/YOUR-USERNAME/my-first-binder/HEAD** dans un nouvel onglet
````

````{tabbed} R
1) Dans votre dépôt, créez un fichier appelé `install.R`
2) Ajoutez une ligne qui dit : `install.packages("readr")`
3) Vérifiez s'il y a des fautes ! Puis commit sur la branche `main`
4) Visitez **https://mybinder. rg/v2/gh/YOUR-USERNAME/my-first-binder/HEAD** à nouveau dans un nouvel onglet

```{note}
Si vous utilisez `holepunch`, vous pouvez créer une `installation. ` et ajoute automatiquement le code pour installer toutes les dépendances dans votre projet en utilisant `holepunch::write_install()`.
```
````
Cette fois-ci, cliquez sur "Build Logs" dans la grande barre grise, horizontale et grise. Cela vous permettra de suivre l'évolution de votre construction. It's useful when your build fails or something you think _should_ be installed is missing.

```{note}
Parfois, les logs de construction de Binder impriment les choses dans la police rouge, comme les avertissements que `pip` n'est pas à jour (`pip` est souvent obsolète car il est régulièrement mis à jour ! ou les messages d'installation, surtout si vous utilisez R.
Ces messages rouges ne signifient pas nécessairement qu'il y a un problème avec votre build et il échouera - c'est juste un malheureux choix de couleur de police !
```

(z2b-arrière-plan-2)=
### Que se passe-t-il en arrière-plan ? - Partie 2

Cette fois-ci, BinderHub lira le fichier de configuration que vous avez ajouté et installera la version spécifique du paquet que vous avez demandé.

(z2b-dependencies)=
### Plus d'informations sur l'épinglage des dépendances

````{tabbed} Python
Dans l'exemple ci-dessus, nous avons utilisé deux signes égaux (`==`) pour épingler la version de `numpy`.
Cela indique à Binder d'installer cette version _specific_.

Une autre façon d'épingler un numéro de version est d'utiliser le signe supérieur ou égal à (`>=`) pour permettre à n'importe quelle version au-dessus d'une version particulière d'être installée.
Ceci est utile lorsque vous avez beaucoup de dépendances qui peuvent avoir des dépendances les unes avec les autres et permet à Binder de trouver une configuration de vos dépendances qui ne sont pas en conflit les unes avec les autres tout en évitant toute version antérieure qui pourrait endommager ou modifier votre code.

Enfin vous n'avez pas pu fournir le moindre numéro de version (juste le nom de la bibliothèque/paquet) et Binder installera la dernière version de ce paquet.
````

````{tabbed} Julia
Dans l'exemple ci-dessus, nous avons copié un hash dans notre fichier `Project.toml` qui est lié à la version du paquet que nous voudrions installer.
Pour un graphe de dépendance complet, nous devrions également inclure un fichier `Manifest.toml` qui documenterait les dépendances des dépendances.
Entre ces deux fichiers, nous sommes en mesure d'instancier une réplication exacte d'un environnement Julia.

Bien sûr, nous pouvons imaginer qu'au fur et à mesure que l'environnement se développe et que les interdépendances deviennent plus complexes, il deviendrait très taxant d'écrire ces fichiers à la main!
La vérité est que vous ne le feriez jamais manuellement, le gestionnaire de paquets intégré `Pkg` peut [les générer automatiquement](https://julialang.github.io/Pkg.jl/v1/environments/).
````

````{tabbed} R
Dans l'exemple ci-dessus, nous avons spécifié que nous voulons utiliser R dans notre projet en incluant une date dans `runtime.txt`.
La date indique à Binder à quel instantané CRAN se trouve à partir de la source R et des paquets.
Ces instantanés sont fournis à partir du [gestionnaire de paquets RStudio](https://packagemanager.rstudio.com) (RSPM).
Dans l'exemple ci-dessus, l'instantané RSPM daté de `r-2022-01-01-01` est utilisé et la version de R et `readr` disponible à cette date et installée.
Pour que l'exemple de workflow fonctionne correctement, veuillez vous assurer que vous ne fournissez pas une date antérieure à cette date d'exemple.

Ceci fournit quelques versions rudimentaires des paquets pour les utilisateurs R mais n'est pas aussi robuste que l'épinglage des versions dans un `requirements.txt` en Python.
Pour une épinglage plus robuste et spécifique en R, jetez un œil au package [`renv`](https://rstudio.github.io/renv/).
````

(z2b-step-5)=
## 5. Contrôler l'environnement

🚦🚦🚦

````{tabbed} Python
1) Depuis le panneau de lancement, sélectionnez "Python 3" dans la section Bloc-notes pour ouvrir un nouveau bloc-notes
2) Tapez ce qui suit dans une nouvelle cellule :

   ```python
   import numpy
   print(numpy.__version__)
   numpy.random. andn()
   ```

   ```{attention}
   Notez les deux tirets bas de la `version` !
   ```

3) Exécutez la cellule pour voir le numéro de version et un nombre aléatoire imprimé

   - Appuyez sur SHIFT+RETURN ou le bouton "Démarrer" dans la barre de menu
````

````{tabbed} Julia
1) Depuis le panneau de lancement, sélectionnez "Julia" dans la section Bloc-notes pour ouvrir un nouveau bloc-notes Julia
2) Tapez ce qui suit dans une nouvelle cellule :

   ```julia
   en utilisant Pkg
   Pkg. tatus()
   ```

3) Exécutez la cellule pour voir le numéro de version imprimé

   - Appuyez sur SHIFT+RETURN ou le bouton "Démarrer" dans la barre de menu
````

````{tabbed} R
1) Depuis le panneau de lancement, sélectionnez "R" dans la section Bloc-notes pour ouvrir un nouveau bloc-notes R
2) Tapez ce qui suit dans une nouvelle cellule :

   ```r
   library(readr)
   packageVersion("readr")
   read_csv(system. ile("extdata/mtcars. sv", package = "readr"))
   ```

3) Exécutez la cellule

    - Appuyez soit SHIFT+RETURN ou le bouton "Run" dans la barre de menus
    Vous devriez voir la sortie suivante :
      - le numéro de version de la version installée de `readr`
      - un tibble du contenu de `mtcars. sv` qui est un fichier csv inclus dans le paquet `readr`
````

```{attention}
Si vous enregistrez ce notebook, il **ne sera pas** enregistré dans le dépôt GitHub.
Repousser les changements vers le dépôt GitHub à travers le conteneur n'est pas possible avec Binder.
**Toutes les modifications que vous avez apportées aux fichiers à l'intérieur de la Binder seront perdues une fois que vous fermerez la fenêtre du navigateur.**
```

(z2b-step-6)=
## 6. Partagez votre travail

Le Binder est une question de partage facile de votre travail et il y a deux façons de le faire:

- Partagez directement l'URL **https://mybinder.org/v2/gh/YOUR-USERNAME/my-first-binder/HEAD**
- Visitez **[https://mybinder. rg](https://mybinder.org)**, tapez l'URL de votre dépôt et copiez le snippet Markdown ou ReStructured Text dans votre `README. d` fichier. Ce snippet va afficher un badge que les gens peuvent cliquer, qui ressemble à ceci : ![Binder](https://mybinder.org/badge_logo.svg)

🚦🚦🚦

1) Ajoute le snippet **Markdown** de **<https://mybinder.org>** au fichier `README.md` de votre dépôt
   - La barre grise affichant un badge de lieur se dépliera pour révéler les snippets. Cliquez sur l'icône du presse-papiers à côté de la case marquée par "m" pour copier automatiquement le snippet Markdown. 2) Cliquez sur le badge pour vous assurer que cela fonctionne!

(z2b-step-7)=
## 7. Accès aux données dans votre Binder

Un autre type de dépendance pour les projets est **les données**. Il existe différentes façons de rendre les données disponibles dans votre Binder en fonction de la taille de vos données et de vos préférences pour les partager.

(z2b-petits-fichiers)=
### Petits fichiers publics

L'approche la plus simple pour les petits fichiers de données publiques est de les ajouter directement dans votre dépôt GitHub. Ils sont ensuite directement encapsulés dans l'environnement et versionnés avec votre code.

Ceci est idéal pour les fichiers jusqu'à **10 Mo**.

(z2b-medium fichiers)=
### Fichiers publics moyens

Pour accéder aux fichiers médiatiques **de quelques 10 Mo à quelques centaines de Mo**, vous pouvez ajouter un fichier appelé `postBuild` à votre dépôt. Un fichier `postBuild` est un script shell qui est exécuté dans le cadre de la construction d'image et n'est exécuté qu'une seule fois quand une nouvelle image est construite, pas chaque fois que le Binder est lancé.

Voir l'exemple de [Binder `postBuild`](https://mybinder.readthedocs.io/en/latest/using/config_files.html#postbuild-run-code-after-installing-the-environment) pour plus d'utilisation du script `postBuild`.

```{note}
Les nouvelles images ne sont construites que lorsque Binder voit une nouvelle livraison, pas à chaque fois que vous cliquez sur le lien Binder.
Par conséquent, les données ne sont téléchargées qu'une seule fois lorsque l'image Docker est construite, pas à chaque fois que le Binder est lancé.
```

(z2b-gros fichiers)=
### Fichiers publics volumineux

Il n'est pas pratique de placer les gros fichiers dans votre dépôt GitHub ou de les inclure directement dans l'image que Binder construit. La meilleure option pour les gros fichiers est d'utiliser une bibliothèque spécifique au format de données pour diffuser les données que vous utilisez ou pour les télécharger à la demande dans le cadre de votre code.

Pour des raisons de sécurité, le trafic sortant de votre Binder est limité uniquement aux connexions HTTP/S ou GitHub. Vous ne pourrez pas utiliser les sites FTP pour récupérer des données sur mybinder.org.

(fichiers z2b-private-)=
### Fichiers privés

Il n'y a aucun moyen d'accéder aux fichiers qui ne sont pas publics à partir de mybinder.org. Vous devriez considérer toutes les informations de votre Binder comme publiques, ce qui signifie que :

- il ne devrait y avoir aucun mot de passe, jetons, clés et ainsi de suite dans votre dépôt GitHub;
- vous ne devriez pas taper des mots de passe dans un Binder fonctionnant sur mybinder.org;
- vous ne devriez pas télécharger votre clé privée SSH ou votre jeton API sur un Binder en cours d'exécution.

Afin de supporter l'accès aux fichiers privés, vous devrez créer un déploiement local de [BinderHub](https://binderhub.readthedocs.io) où vous pourrez décider vous-même des compromis en matière de sécurité.

```{note}
La construction d'un BinderHub n'est pas une tâche simple et est généralement prise en charge par les groupes IT/RSE pour des raisons de gestion de la maintenance, de la sécurité et de la gouvernance.
Cependant, cela ne veut pas dire qu'ils sont les _seuls_ groupes de personnes qui devraient/pourraient construire un BinderHub.
```

(z2b-step-8)=
## 8. Obtenir des données avec `postBuild`

🚦🚦🚦

````{tabbed} Python
1) Rendez-vous sur votre dépôt GitHub et créez un fichier appelé `postBuild`
2) Dans `postBuild`, ajoutez une seule ligne de lecture : `wget -q -O gapminder. sv http://bit.ly/2uh4s3g`
   - `wget` est un programme qui récupère le contenu des serveurs web.
     Cette ligne extrait le contenu de l'URL bitly et l'enregistre au nom du fichier indiqué par le drapeau `-O` (majuscule "O", pas zéro), dans ce cas `gapminder. sv`.
     Le flag `-q` indique à `wget` de faire cela silencieusement, ce qui signifie qu'il n'affichera rien sur la console.
3) Mettez à jour vos `exigences. fichier xt` en ajoutant une nouvelle ligne avec `pandas` dessus et une autre nouvelle ligne avec `matplotlib` sur elle
   - Ces paquets ne sont pas nécessaires pour télécharger les données, mais nous les utiliserons pour lire le fichier CSV et faire un tracé
4) Cliquez sur le badge de liant dans votre README pour lancer votre Binder

Une fois la Binder lancée, vous devriez voir apparaître un nouveau fichier qui ne faisait pas partie de votre dépôt lorsque vous avez cliqué sur le badge.

Visualisez maintenant les données en créant un nouveau bloc-notes (sélectionnez "Python 3" dans la section Notebook) et exécutez le code suivant dans une cellule.

```python
%matplotlib inline

import pandas

data = pandas.read_csv("gapminder.csv", index_col="country")

ans = données. olumns.str.strip("gdpPercap_") # Extrait l'année des 4 derniers caractères de chaque nom de colonne
data.columns = années. stype(int) # Convertir les valeurs de l'année en entiers, sauvegarde des résultats vers des données

. oc["Australie"]. lot()
```

```{note}
Voir cette [leçon de menuiserie logicielle](https://swcarpentry.github.io/python-novice-gapminder/09-plotting/index.html) pour plus d'informations.
```
````

````{tabbed} Julia
1) Rendez-vous sur votre dépôt GitHub et créez un fichier appelé `postBuild`
2) Dans `postBuild`, ajoutez une seule ligne de lecture : `wget -q -O gapminder. sv http://bit.ly/2uh4s3g`
   - `wget` est un programme qui récupère le contenu des serveurs web.
     Cette ligne extrait le contenu de l'URL bitly et l'enregistre au nom du fichier indiqué par le drapeau `-O` (majuscule "O", pas zéro), dans ce cas `gapminder. sv`.
     Le flag `-q` indique à `wget` de faire cela silencieusement, ce qui signifie qu'il n'affichera rien sur la console.
3) Mettez à jour votre `Projet. oml` fichier en ajoutant de nouvelles dépendances à `[deps]` avec les lignes suivantes :

   ```julia
   DataFrames = "a93c6f00-e57d-5684-b7b6-d8193f3e46c0"
   Plots = "91a5bcdd-55d7-5caf-9e0b-520d859cae80"
   ```

   - Ces paquets ne sont pas nécessaires pour télécharger les données, mais nous les utiliserons pour lire le fichier CSV et faire un tracé
4) Cliquez sur le badge binder dans votre README pour lancer votre Binder

Une fois le Binder lancé, le Binder a été lancé, vous devriez voir apparaître un nouveau fichier qui ne faisait pas partie de votre dépôt lorsque vous avez cliqué sur le badge.

Maintenant, visualisez les données en créant un nouveau bloc-notes (sélectionnez "Julia" dans la section Notebook) et exécutez le code suivant dans une cellule.

```julia
en utilisant des DataFrames
en utilisant CSV
en utilisant des Plots

données = CSV.read("gapminder. sv", DataFrame)

# Extraire la ligne correspondant à l'Australie
aus_gdp = data[:, :country] . = "Australie", :]
aus_gdp = Matrice(aus_gdp[:, :end])[:] # en tant que vecteur

# Extraire les années comme Ints des noms de colonnes
ans = [x[end-3:end] pour x dans les noms(data)[2:end]]
ans = parse. Int, années)

# Tracé
tracé (années, aus_gdp)
```
````

````{tabbed} R
1) Rendez-vous sur votre dépôt GitHub et créez un fichier appelé `postBuild`
2) Dans `postBuild`, ajoutez une seule ligne de lecture : `wget -q -O gapminder. sv http://bit.ly/2uh4s3g`
   - `wget` est un programme qui récupère le contenu des serveurs web.
     Cette ligne extrait le contenu de l'URL bitly et l'enregistre au nom du fichier indiqué par le drapeau `-O` (majuscule "O", pas zéro), dans ce cas `gapminder. sv`.
     Le flag `-q` indique à `wget` de faire cela silencieusement, ce qui signifie qu'il n'affichera rien sur la console.
3) Mettez à jour votre fichier `install.R` pour installer deux dépendances supplémentaires, `"tidyr"` et `"ggplot2"`. Pour ce faire, fournissez un vecteur de caractères des paquets requis à `install.packages()` au lieu d'une seule chaîne de caractères. La commande d'installation devrait maintenant ressembler à ceci :

   ```r
   install. ackages(c("readr", "tidyr", "tidyr", "ggplot2"))
   ```

    - Ces paquets ne sont pas nécessaires pour télécharger les données, mais nous les utiliserons pour lire le fichier CSV, Traitez-le et faites un tracé
4) Cliquez sur le badge du lieur dans votre README pour lancer votre Binder

Une fois que le Binder a démarré, vous devriez voir apparaître un nouveau fichier qui ne faisait pas partie de votre dépôt lorsque vous avez cliqué sur le badge.

Visualisez maintenant les données en créant un nouveau bloc-notes (sélectionnez "R" dans la section Notebook) et en exécutant le code suivant dans une cellule.

```r
library(readr)
library(tidyr)
library(ggplot2)

data <- read_csv("gapminder. sv") %>%
    pivot_longer(-pays,
                 noms_to = "année",
                 valeur_to = "gdpPercap",
                 names_prefix = "gdpPercap_",
                 noms_transformation = list(year = as. nteger))

données[données$country == "Australie", ] %>%
    ggplot(aes(x = année, y = gdpPercap)) +
    geom_line()
```
````
(z2b-beyond-notebooks)=
## Changement de l'interface
Tout au long de ce tutoriel, nous avons utilisé l'interface JupyterLab. C'est l'interface par défaut pour les instances de Binder nouvellement créées. Cependant, ce n'est pas la seule interface disponible sur mybinder.org, la vue Classique Notebook et RStudio sont également disponibles. (Un environnement R doit être installé pour que RStudio soit disponible.)
Vous pouvez accéder aux différentes interfaces de différentes façons. Le moyen le plus simple est d'utiliser les boutons dans le lanceur JupyterLab, mais vous pouvez fournir des paramètres d'URL pour ouvrir directement une interface (ou un fichier! lorsque l'instance Binder est lancée. Nous allons maintenant couvrir trois façons de manipuler l'URL de votre Binder pour naviguer entre les interfaces.
### de l'intérieur d'un Binder en cours
Voici la structure de l'URL dans une instance de Binder exécutant JupyterLab:
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
