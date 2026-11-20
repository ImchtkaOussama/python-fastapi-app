
# TP 6 – Variables d'environnement, Inputs et Outputs

## Q1. Pourquoi la variable n'est-elle pas disponible dans la step qui l'a définie, mais seulement dans les suivantes ?

GITHUB_ENV permet de définir des variables d'environnement accessibles aux étapes suivantes du même job.

La step qui écrit dans GITHUB_ENV ne peut pas utiliser immédiatement ces variables, car GitHub Actions les charge uniquement au début de chaque étape suivante.

## Q2. Quelle est la portée de GITHUB_ENV ?

GITHUB_ENV a une portée limitée au job courant.

Les variables définies dans un job ne sont pas automatiquement disponibles dans les autres jobs, car chaque job s'exécute dans un environnement indépendant.

## Q3. Que se passe-t-il si on utilise > au lieu de >> dans GITHUB_OUTPUT ?

L'opérateur > écrase le contenu précédent du fichier, tandis que >> ajoute du contenu à la fin du fichier.

Si plusieurs outputs sont définis dans la même étape avec >,
seul le dernier output sera conservé.

Il faut donc utiliser >> pour enregistrer plusieurs outputs.

## Q4. Pourquoi GITHUB_ENV ne suffit-il pas ici, alors que GITHUB_OUTPUT fonctionne entre jobs ?

GITHUB_ENV permet uniquement de partager des variables entre les étapes d'un même job.

GITHUB_OUTPUT permet de définir des outputs pour une étape. Ces outputs peuvent ensuite être exposés au niveau du job avec outputs, puis récupérés dans un autre job grâce à needs.

## Q5. Que se passe-t-il si on retire needs: build du job deploy ?

Sans needs: build, le job deploy ne dépend plus du job build.

Les deux jobs peuvent alors s'exécuter en parallèle. Le job deploy ne garantit plus que le job build soit terminé avant son exécution.

Les outputs de build ne sont donc pas disponibles de manière fiable pour deploy.
