# CoapTutoriel

CoAP (Constrained Application Protocol) est un protocole de transfert Web optimisé pour les périphériques et réseaux contraints utilisés dans les réseaux de capteurs sans fil pour former l'Internet des objets. 
Basé sur le style architectural REST, il permet de manipuler au travers d’un modèle d’interaction client-serveur les ressources des objets communicants et capteurs identifiées par des URI (Uniform Resource Identifer, courte chaine de caractère identifiant une ressource sur un réseau physique) en s'appuyant sur l'échange de requêtes-réponses et méthodes similaires au protocole HTTP. 

Cette technologie permet l’interaction avec des capteurs au travers de services web RESTful. Ce protocole a été élaboré pour les périphériques contraints alimentés par batterie, équipés de microprocesseurs peu performants et disposant d’une quantité de mémoire RAM et ROM limitée. Il offre simplicité, faible surcharge pour environnements réseaux contraints de faible puissance confrontés à des taux de perte important. CoAP permet les communications M2M requises pour l’interaction et l'exploitation des systèmes embarqués. Il est défini comme protocole générique pour les réseaux à basse puissance et avec pertes et s'appuie sur les protocoles et réseaux sous-jacents 6LoWPAN, IEEE802.15.4.

il apporte ces principales fonctionnalités : 
•	Faible surcharge d'entête et complexité d’interprétation réduite ;
•	Transport UDP avec une couche application unicast fiable et le support du multicast ;
•	Échange de messages sans état en asynchrone ;
•	Possibilité d'utiliser des proxys (facilite l’intégration avec l'existant) et de mettre les informations en cache (périphériques en veille) ;
•	Découverte et observation des ressources ;
•	Représentation des ressources URI et support de différents types de contenus.

CoAP s'appuie sur un modèle client-serveur semblable à HTTP, où les clients envoient des requêtes sur des ressources REST pour récupérer de l'information d'un capteur ou contrôler un périphérique et son environnement. Cependant CoAP traite les échanges de manière asynchrone au travers de datagrammes UDP.

Une requête CoAP est similaire à une requête HTTP. Elle est envoyée par le client pour demander une action GET, POST, PUT ou DELETE sur une ressource identifiée par une URI. Le serveur répond par un code réponse accompagné éventuellement de la représentation de la ressource.

L'architecture CoAP est divisée en deux couches. Une couche message qui apporte fiabilité et le séquencement des échanges de bout en bout qui repose sur UDP. Une couche « Request/Response » qui utilise des méthodes et codes réponses pour les interactions requêtes/réponses. Il s'agit cependant bien d'un seul et même protocole qui propose ces fonctionnalités dans son entête. 
 
L'utilisation d'un jeton (=nom de le requête) permet à CoAP de faire l'association entre les requêtes et réponses au cours d'une communication. Tandis qu'un « Label » généré et inséré par le client dans chaque entête de message CoAP permet de détecter les doublons.

Les réponses sont identifiées par des codes réponses analogues aux codes d'état de succès 2.xx , d'erreur 4.xx ou 5.xx du protocole HTTP qui indiquent le statut de l'opération11. 
 
Success
2.xx, indique que la requête a été correctement reçue, comprise et acceptée.
Client Error 
4.xx indique que le client a rencontré une erreur.
Internal Server Error
5.xx indique que le serveur est dans l'impossibilité de traiter la requête.


 

Les messages CoAP sont par défaut transportés au travers de datagrammes UDP. Cette communication peut être transmise via DTLS mais aussi par d’autres moyens comme SMS, TCP, ou SCTP. Les messages sont encodés dans un format binaire simple. Un message commence par un entête fixe de 4 octets, suivi par un champ « Token » de taille variable comprise entre 0 et 8 octets qui permet dans les échanges d’associer les requêtes aux réponses. Sa longueur est indiquée par le champ « TKL ». Il apparait ensuite, une séquence d’options au format TLV suivie en option des données qui occupent le reste du datagramme. Dans le cas où ces dernières sont présentes, elles sont séparées de l’entête grâce à un marqueur d’1 octet contenant la valeur «0xFF».
