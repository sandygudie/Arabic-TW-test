(rr-code-reuse)=
# Code réutilisable
Votre projet logiciel pourrait aller d'un petit script que vous utilisez pour le traitement des données à un bloc-notes utilisé pour l'analyse des données, ou une bibliothèque logicielle implémentant vos algorithmes. Peu importe la taille ou la taille de votre projet logiciel, il est important de rendre votre code réutilisable.

Différents types de logiciels ont des exigences différentes pour être réutilisables : pour un petit script, avoir suffisamment de documentation peut suffire, tandis que pour une bibliothèque logicielle critique, des tests approfondis peuvent être nécessaires. Au niveau le plus basique, tout ce que vous avez à faire est de mettre votre code en ligne quelque part qui va probablement durer longtemps. Une approche plus élaborée pour rendre votre logiciel de recherche plus réutilisable est en suivant les Principes FAIR pour les Logiciels de Recherche (Principes FAIR4RS) {cite:ps}`ChueHong2021FAIR4RS`.

Lorsque nous parlons de rendre le code réutilisable, il est utile de clarifier ce que nous voulons. Dans la table des définitions de {ref}`pour la reproductibilité<rr-overview-definitions-reproducibility>` nous avons défini la recherche reproductible comme utilisant les mêmes données et le même code. Cependant, lorsque nous parlons de réutilisation du code, cela peut prendre plusieurs formes: nous pouvons vouloir exécuter exactement le même code (pour les langages de programmation compilés, cela pourrait même signifier le même fichier binaire), ou nous pouvons vouloir modifier le code source et l'étendre d'une manière particulière pour répondre à nos besoins. Freire et Chirigati {cite:ps}`Freire2018Reproduccibility` fournissent un cadre de différents niveaux de reproductibilité, selon ce qui peut être modifié. Ils définissent les niveaux suivants de reproductibilité : répétable, réexécutable, portable, extensible et modifiable.

Nous pouvons cartographier les définitions de reproductiblement dans le cadre Freire comme suit:

| Freire framework | Définitions de reproductiblement                                          |
| ---------------- | ------------------------------------------------------------------------- |
| Répétitif        | Reproductible (mêmes données, même analyse)                               |
| Réexécutable     | Robuste & Réplique (même code, données / analyse / paramètres différents) |
| Portable         | *Non considéré* (Même code/données, environnement différent)              |
| Extensible       | (partiellement) Généralisable                                             |
| Modifiable       | (partiellement) Généralisable                                             |

La portabilité n'était pas envisagée précédemment, mais pour les logiciels un environnement différent (tel que le matériel différent, ou même une nouvelle installation sur un matériel comparable) peut affecter la capacité du logiciel à fonctionner (par exemple, cela peut affecter les dépendances).

Aussi, généralisable encapsule deux concepts : extensible (la capacité à s'intégrer à d'autres logiciels) et modifiable (la capacité de changer une partie de l'implémentation pour étendre sa fonctionnalité).

Dans le reste de ce chapitre, nous fournissons une liste de recommandations que vous pouvez suivre pour vous assurer que votre code est réutilisable.

(rr-code-reuse-recommendation-checklist)=
## Comment rendre votre code plus réutilisable
Cette section contient une liste de recommandations pour rendre votre logiciel plus réutilisable. La section {ref}`rr-code-reuse-recommendation-details` contient une explication plus approfondie de chacune de ces recommandations. Vous pouvez suivre les recommandations qui sont plus adaptées à votre type de logiciel et sauter celles qui ne sont pas pertinentes dans votre cas.

### Recommandations répétables
1. Assurez-vous que vous pouvez le trouver (dans l'espace)
1. Assurez-vous de le trouver (en temps)
1. Assurez-vous que vous pouvez exécuter la même séquence d'opérations
1. Assurez-vous que votre environnement et la séquence des opérations sont robustes et qu'aucun humain n'est nécessaire pour reproduire ce qui a été fait
1. Licence de votre code
    - avec une licence qui permet la réutilisation ;
    - avec une licence compatible avec les licences des dépendances
1. Assurez-vous qu'il est citable
1. Inclure les données nécessaires
1. Écrire une documentation utile*

### Recommandations réexécutables
1. Enlever les bits codés en dur et rendre le code modulaire
1. Teste que les modules que tu as créés peuvent prendre différents types de données ou paramètres d'entrée
1. Transformez les modules en package/toolbox
1. Écrire une documentation utile*

### Recommandations portables
1. Assurez-vous que vous pouvez recréer l'environnement où il a vécu
1. Écrire une documentation utile*

### Recommandations extensibles
1. Écrire une documentation utile*

### Recommandations modifiables
1. Assure-toi que ton code est lisible par les humains
1. Assurez-vous que les commentaires sont présents
1. Écrire une documentation utile*

Le lecteur observant peut remarquer que `Écrire de la documentation utile` est mentionné pour chaque niveau de réutilisation. Ceci est dû au fait que différents niveaux de documentation sont requis pour différents niveaux de réutilisation.

### Différentes exigences de documentation pour différents niveaux de réutilisation
Écrire de la documentation utile est une exigence importante pour tous les niveaux de réutilisation. Cependant, pour les différents niveaux de réutilisation, il y a des exigences de documentation différentes :

La documentation:
- explique l'utilisation, en précisant :
  - ce que fait le logiciel ; (requis pour le répéter)
  - comment il peut être utilisé ; (requis pour répéter)
  - quelles options/paramètres sont disponibles. (requis pour les répétitives)
- contient des exemples de comment le lancer. (requis pour les répétitives)
- a des instructions d'installation, y compris les bonnes descriptions de :
  - le matériel dont il dépend (par exemple GPUs); (requis pour le portable)
  - le système d'exploitation sur lequel le logiciel a été testé ; (requis pour être portable)
  - des exigences (telles que les bibliothèques et les paramètres de l'interpréteur de commandes). (requis pour le portable)

(rr-code-reuse-recommendation-details)=
## Recommandations pour le code réutilisable
Assurez-vous que vous (ou quelqu'un d'autre) pouvez réutiliser votre code pour faire la même chose que vous. La section {ref}`rr-code-reuse-recommendation-checklist` contient une liste de recommandations pour rendre votre logiciel plus réutilisable. Dans cette section, vous trouverez une explication plus détaillée de chacune de ces recommandations, avec des pointeurs vers d'autres parties pertinentes de ce guide.

### Recommandations répétables
À ce stade, vous n'aurez peut-être même pas besoin de pouvoir ouvrir le code et le lire, vous voulez juste vous assurer que vous pouvez relancer toutes les étapes nécessaires et obtenir les mêmes résultats que vous avez obtenus.

#### 1. Assurez-vous que vous pouvez le trouver (dans l'espace)
Votre code doit être stocké publiquement et partagé avec des collaborateurs. Il a un identifiant persistant unique, afin que tout le monde puisse le trouver et y accéder.

**Voir aussi**: {ref}`rr-vc`

#### 2. Assurez-vous de le trouver (en temps)
Idéalement, l'évolution temporelle du code est documentée avec le contrôle de version. Cela vous permet de récupérer une version spécifique du passé.

**Voir aussi**: {ref}`rr-vc`

#### 3. Assurez-vous que vous pouvez exécuter la même séquence d'opérations
Souvent, l'homme qui a mis en place l'environnement est aussi celui qui a écrit le code et celui qui connaît l'ordre exact des étapes nécessaires pour pouvoir ré-exécuter le code et reproduire les résultats. Cela pourrait certainement être soigneusement documenté pour qu'un autre humain le réagisse.

**Voir aussi**: [leçon CodeRefinery sur la recherche reproductible](https://coderefinery.github.io/reproducible-research/)

#### 4. Assurez-vous que votre environnement et la séquence des opérations sont robustes et qu'aucun humain n'est nécessaire pour reproduire ce qui a été fait
Vous ne voulez pas dépendre des humains. Ils ont tendance à commettre des erreurs, même s'ils n'ont pas de mauvaises intentions. Vous voulez donc que votre environnement soit scripté et soit recréé au besoin et que votre séquence d'opérations soit exécutée par un script de pipeline qui colle toutes les séquences d'étapes.

**Voir aussi**: {ref}`rr-renv-option`

#### 5. Licence de votre code
Assurez-vous d'attacher une licence à votre code et indiquez comment vous voulez être cité lorsque les gens le réutilisent. Pensez à utiliser une licence permissive qui permet une réutilisation. De plus, vous devez choisir une licence compatible avec les licences des bibliothèques ou des paquets dont dépend votre logiciel.

**Voir aussi**: {ref}`rr-licence-logiciel`, {ref}`rr-licence-logiciel-permissive`, {ref}`rr-compatibilité-licence-compatibilité`

#### 6. Assurez-vous qu'il est citable
Assurez-vous de spécifier comment vous voulez être cité lorsque les gens le réutilisent.

**Voir aussi**: {ref}`cm-citable-logiciel`

#### 7. Inclure les données nécessaires
Si le logiciel dépend de n'importe quel type de données, les données doivent être disponibles

**Voir aussi**: {ref}`rr-rdm-données`

### Recommandations réexécutables
Assurez-vous que vous (ou d'autres) pouvez le réutiliser pour faire ce que vous avez fait, mais avec des données différentes/différents paramètres

#### 1. Enlever les bits codés en dur et rendre le code modulaire
Vous ne voulez pas avoir de détails spécifiques à vos données ou paramètres d'analyse codés en dur dans le code. Si quelque chose peut devenir une fonction réutilisable, séparez-la des paramètres codés en dur et transformez-la en quelque chose (ré)utilisable tout seul. Rendre les modules purs : étant donné la même entrée, une fonction pure retourne toujours la même valeur.

**Voir aussi**: [leçon de développement de code modulaire CodeRefinery](https://cicero.xyz/v3/remark/0.14.0/github.com/coderefinery/modular-code-development/master/talk.md/#1)

#### 2. Teste que les modules que tu as créés peuvent prendre différents types de données ou paramètres d'entrée
Vous ne savez peut-être pas encore comment votre code sera réutilisé dans le futur, mais vous pouvez éviter comment il ne devrait pas être utilisé si vous pouvez tester quels paramètres sont autorisés.

**Voir aussi**: [leçon CodeRefinery sur les tests automatisés](https://coderefinery.github.io/testing/motivation/)

#### 3. Transformez les modules en package/toolbox
Séparez encore plus les spécificités de votre projet avec les bits qui peuvent être réutilisés dans d'autres de vos projets ou par d'autres personnes.

**Voir aussi**: {ref}`rr-renv-package`, [Logiciel d'emballage](https://scicomp.aalto.fi/scicomp/packaging-software/), [packaging logiciel en Python](https://aaltoscicomp.github.io/python-for-scicomp/packaging/)

### Recommandations portables
La portabilité désigne la capacité de transférer des logiciels vers un nouvel environnement. Cela pourrait faire référence à une machine identique (mais pas la même), mais il peut aussi faire référence à une nouvelle architecture matérielle, système d'exploitation, etc. Ces deux éléments sont importants pour la réutilisation des logiciels.

#### 1. Assurez-vous que vous pouvez recréer l'environnement où il a vécu
L'environnement est un instantané fragile dans le temps qui accompagne silencieusement le code. Il peut inclure l'humain qui a géré le logiciel, les étapes que l'humain a fait pour préparer les données, le matériel, le système d'exploitation, les bibliothèques, les paquets externes/boîtes à outils/dépendances. Tout cela peut être soigneusement documenté pour qu'un autre humain puisse refaire les mêmes étapes.

**Voir aussi**: {ref}`rr-renv`

### Recommandations extensibles et modifiables
Assurez-vous que d'autres peuvent construire sur votre code pour l'étendre et l'améliorer.

#### 1. Assure-toi que ton code est lisible par les humains
Il paie souvent plus à écrire du code pour les autres humains afin qu'ils puissent le lire (y compris votre futur moi-même). Un oneliner cryptique avec des noms de variables obscurs n'est ni plus rapide ni plus efficace que de diviser la ligne en plusieurs étapes avec des noms de variables lisibles qui ont un sens. De plus, l'utilisation de conventions de codage aidera d'autres lecteurs.

**Voir aussi**: {ref}`rr-code-style-and-formatting`, {ref}`rr-code-quality-avantages`

#### 1. Assurez-vous que les commentaires sont présents
Écrivez des commentaires avant d'écrire le code actuel. Imaginez que quelqu'un puisse juste lire les commentaires et sauter tous les bits de code entre les commentaires et obtenir une image complète de ce qui se passe comme s'il lisait tout le code.
