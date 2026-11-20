# Réponses – TP 7

## Q1. Pourquoi actions/checkout n'a-t-il pas besoin de with alors que setup-node en a besoin ?

L'action actions/checkout utilise des paramètres par défaut
qui permettent de récupérer le dépôt GitHub.

En revanche, actions/setup-node nécessite le paramètre
node-version pour connaître la version de Node.js à installer.

## Q2. Pourquoi le job verify ne retrouve-t-il pas report.txt
sans l'artefact, alors que les deux jobs partagent le même dépôt ?

Chaque job GitHub Actions s'exécute dans un environnement
indépendant avec son propre runner.

Les fichiers générés dans un job ne sont donc pas automatiquement
disponibles dans un autre job.

L'utilisation de upload-artifact et download-artifact permet
de transférer les fichiers entre les jobs.

## Q6. Pourquoi actions/checkout doit-il s'exécuter avant l'appel
d'une action locale ?

L'action checkout récupère le contenu du dépôt sur le runner.

L'action locale doit être présente dans le système de fichiers
pour pouvoir être exécutée.

Il faut donc exécuter checkout avant d'appeler
une action locale avec uses: ./.github/actions/...

## Q7. Pourquoi shell: bash est-il obligatoire sur les steps run
d'une action composite ?

Dans une action composite, chaque étape utilisant run
doit préciser explicitement le shell à utiliser.

Le paramètre shell: bash indique que les commandes
seront exécutées avec l'interpréteur Bash.
