# Generation de l'image Docker en local
Pour générer l'image Docker en local, il faut lancer lancer et exécuter la commande suivante: 

    docker build --target lean -t 'consoneo-snapshot-nexus.consoneo.tech/consoneo/superset:$DESIRED_VERSION' --build-arg PY_VER=3.8.12 . -m 4g --platform linux/amd64
