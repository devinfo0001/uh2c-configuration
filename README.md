# Notes

C'est un Repository pour hébérger les fichiers de configuration ("application.properties" ou "application.yml") des différents projets PARI.

A _cloner_ sur le poste local et à ouvrir en tant que projet simple dans le Workspace.

Si le fichier de configuration ("application.yml") était présent sur le Repo (pari-configuration) et sur le projet pari-xxx au poste local, le Spring Cloud Config Server (pari-config-server), après avoir cherché et récupéré le contenu du fichier hébérgé, va surcharger le contenu du fichier présent en local et le négliger. Il faudrait ne garder donc que le fichier "bootstrap.yml" contenant principalement : 
- le nom technique du MicroService : `spring.application.name: {nom_technique_MS}`
- l'adresse du Spring Cloud Config Server sur lequel va pointer pour aller chercher les propriétés (parmi lesquelles se trouve le port de démarrage !) et les initialiser chez lui : `spring.cloud.config.uri: http://localhost:{port_config_server}/`

Si ce n'est pas bien fait :
* Le MicroService va aller chercher le Config Server via le port par défaut « localhost:8888 » ;
* Le MicroService va démarrer via le port de _secours_ : localhost:8080

