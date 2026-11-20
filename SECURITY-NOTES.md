
# Security Notes – TP 7

## Q3. Pourquoi faut-il épingler une version (@v4) plutôt que @main ?

Il est préférable d'utiliser une version stable comme @v4
plutôt que @main, car la branche main peut changer à tout moment.

L'utilisation d'une version précise permet de limiter les changements
inattendus et de rendre les workflows plus prévisibles.

## Q4. Le badge « créateur vérifié » garantit-il qu'une action est sûre ?

Non. Le badge créateur vérifié confirme l'identité du créateur
de l'action, mais ne garantit pas que son code est totalement sécurisé.

Il faut toujours examiner le code source, les permissions demandées
et les dépendances utilisées.

## Q5. Citez deux vérifications à faire avant d'utiliser,
en production, une action d'un fournisseur inconnu.

1. Vérifier la réputation du fournisseur, le code source,
   les avis et l'activité du dépôt GitHub.

2. Examiner les permissions demandées, les dépendances
   et les éventuelles vulnérabilités de sécurité.
