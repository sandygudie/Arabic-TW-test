(rr-code-style-and-formatting)=
# Style de code et mise en forme

A coding style is a set of conventions on how to format code. For instance, what do you call your variables? Do you use spaces or tabs for indentation? Where do you put comments? Consistently using the same style throughout your code makes it easier to read. Code that is easy to read is easier to understand by you as well as by potential collaborators. Therefore, adhering to a coding style reduces the risk of mistakes and makes it easier to work together on software. [Why Coding Style Matters](http://coding.smashingmagazine.com/2012/10/25/why-coding-style-matters/) is a nice article on why coding styles matter and how they increase software quality.

For example, [PEP8](https://www.python.org/dev/peps/pep-0008/) is the most widely used Python coding style and [ECMAScript 6](http://es6-features.org/) aka [ES6](http://es6-features.org/) is the scripting-language specification standardized by ECMA International for programming in Javascript.

For commonly used style guides for various programming languages see the [Language Guides](https://guide.esciencecenter.nl/best_practices/language_guides/languages_overview.html). Google also has a [style guide](https://code.google.com/p/google-styleguide/) for many languages that are used in open source projects originating out of Google.

## Formatage automatique

Numerous tools exists to automatically format code such that it follows a certain style. Automatic formatting enables higher code quality, especially when you are collaborating in a team and other people need to look at the code you've written. Many developers and organisations maintain standards of code formatting like **2-space** or **4-space indentation**. Using these is highly recommended since the probability of finding bugs (if any) increases multifold.

[EditorConfig](https://editorconfig.org) is a language independent tool that helps maintain consistent whitespace styles for multiple people working on the same project across various editors. Most editors support EditorConfig either natively or through a plugin. Almost all widely used IDEs and text-editors support automatic code formatting upon typing. For example: [JetBrains IDE Suite](https://www.jetbrains.com/products.html#), [VSCode](https://code.visualstudio.com/) and [Atom](https://atom.io/).

In addition to that, there are many language specific tools for automatically formatting code according to a particular style. Note that editors often support using these tools directly from the editing environment.

| Langue        | Outil Formatter                                                                                             |
| ------------- | ----------------------------------------------------------------------------------------------------------- |
| C/C++         | [GNUIndent](http://www.gnu.org/software/indent/), [GreatCode](http://sourceforge.net/projects/gcgreatcode/) |
| Python        | [Noir](https://black.readthedocs.io), [yapf](https://pypi.org/project/yapf/)                                |
| Javascript    | [Io](https://beautifier.io/)                                                                                |
| Java          | [Format Google Java](https://github.com/google/google-java-format), [Jindent](http://www.jindent.com/)      |
| PHP           | [phpStylist](http://sourceforge.net/projects/phpstylist/)                                                   |
| Perl          | [PerlTidy](http://perltidy.sourceforge.net/)                                                                |
| Obus / Frappe | [Indentation du coquillage](http://www.bolthole.com/AWK.html)                                               |
| CSS           | [CSSTidy](http://csstidy.sourceforge.net/)                                                                  |
| HTML          | [Tidy](http://tidy.sourceforge.net/)                                                                        |

**Quick Tip**: If you use VS Code as your primary text editor, you can enable automatic code formatting right into your browser. Open your preferences page in JSON mode and add the following line:

```
"editor.formatOnSave": vrai,
```

## Services en ligne fournissant des contrôles de qualité des logiciels

There are several web services that analyse code and make the quality of the code visible. Usually these services run one or more static code analysis tools that can also be used from the command line or integrated into your editor on your own computer. Using a code quality service that integrates with a GitHub/GitLab repository is highly recommended, as it can detect and communicate quality issues in pull requests.

Code quality analysis services are websites that often offer the following features:

- Analyser automatiquement votre code après l'avoir envoyé sur GitHub/GitLab
- Habituellement gratuit pour les projets open source
- Prise en charge de plusieurs langages de programmation, mais pas toutes les langues auront le même niveau de fonctionnalités
- Note ou note pour la qualité de tout le code dans le référentiel
- Liste des problèmes avec le code, regroupés par gravité
- Descendez vers l'emplacement du ticket
- Liste par défaut des vérifications que le fournisseur de services trouve les meilleures pratiques
- Peut être configuré pour rendre la liste des contrôles plus stricte ou plus détendue
- Peut être configuré pour ignorer les fichiers ou les extensions
- Peut lire un fichier de configuration depuis le référentiel
- Suivre les problèmes au fil du temps et envoyer des alertes lorsque la qualité se détériore
- Rapporte éventuellement sur la couverture de code générée par une version CI
- Déployer automatiquement le dépôt et générer une version d'aperçu avant la publication finale.

For a list of choices see [shields.io](https://shields.io/category/analysis) or [this list of services that are free for open source projects](https://github.com/ripienaar/free-for-dev#code-quality).
