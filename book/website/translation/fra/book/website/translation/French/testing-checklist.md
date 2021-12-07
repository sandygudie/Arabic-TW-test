# Liste de contrôle des tests de code

Cette liste de contrôle contient beaucoup d'éléments. Comme {ref}`l'a mentionné avant<rr-testing-write-tests>`, il est bien mieux de faire certains éléments que aucun d'eux. Ne soyez pas découragé si cette liste de tâches semble insurmontable.

<a name="Writing_tests"></a>

## Tests d'écriture

- Écrivez quelques tests de fumée.
- Écrivez des tests unitaires pour toutes vos unités de code.
- Écrire des tests d'intégration pour vérifier l'intégration entre unités.
- Écrire quelques tests systèméme. Prioriser les chemins communs et importants dans le cadre du programme.
- Ecrivez les tests de régression. Les tests de reconnaissance peuvent exister à n'importe quel niveau de test.
- Le cas échéant pour votre projet écrire des tests d'acceptation.
- Ajouter des tests d'exécution à votre projet.

<a name="Good_practice_checks"></a>

## Bonnes vérifications de pratique

- [ ] Documentez les tests et comment les executer.
  - [ ] Écrire des scripts pour configurer et configurer toutes les ressources nécessaires pour exécuter les tests.
- [ ] Choisissez et utilisez un framework de test.
- [ ] Exécutez les tests réguliérement.
  - [ ] Automatiser le processus de tests en cours d'excution. Envisagez d'utiliser l'intégration continue (voir le chapitre sur l'intégration continue) pour ce faire.
- [ ] Vérifiez la couverture de vos tests et essayez de l'améliorer.
- [ ] Engager dans la révision de code avec un partenaire.
