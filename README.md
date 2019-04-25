# ADR-rackspace
devoir 1

Établir un ADR aposteriori comprenant les 3 entrées correspondant
aux 3 versions majeures.

VERSION 1 :
Contexte: systeme de fichiers stoqués en format flat text sur chaque serveur de mail.
problematique: acces aux données difficile pour le support informatique.
cas d'utilisation: en cas de probleme, le support sera contraint de contacter un ingenieur qui cherchera (en ssh et avec des grep) sur chaque serveur pour retrouver l'information chercher.
attribut de qualité mis en avant: Disponibilité, ergonomie (pour les equipes de support), time consumption.


VERSION 2 : 
Contexte: Système MySql basé sur des bases de données relationnel a la place de fichier flat text, a l'aide de tables pour log, droppées et recrées a chaque clean up (tout les 3 jours), et traitement des log en amont pour pas envoyer trop de data au serveur de log.
problematique: flux de données trop important pour la table de log avec ralentissement important.  
cas d'utilisation: lors de la phase de test, indexer chaque log prenais de plus en plus de temps, apres la premiere heure de test le systeme ne pouvais plus suivre du a l'insertion ligne par ligne en base de données.
attribut de qualité mis en avant: Disponibilité, time consumption.

VERSION 3 :
Contexte: utilisation de Hadoop (projet opensource se basant sur Google File System et MapReduce) pour la gestion des logs, avec possibilité d'adapter le code au besoin de l'entreprise et de le faire evoluer avec les besoin de l'entreprise, il distribue le flux a travers plusieurs serveurs pour repondre a la problematique de la version 2.
problematique: bug lié au developpement de cette solution.
cas d'utilisation: des bugs sont decouvert et corriger par les equipes de developpement au fur et a mesure qu'ils sont trouver.
attribut de qualité mis en avant: Testabilité, modifiabilité.
