TLS https://www.youtube.com/watch?v=P6brMpIZaOo
3 piliers : Authentification, Confidentialité, Intégrité

Cryptographie symétrique : On chiffre et déchiffre avec la même clé
Cryptographie asymétrique : On à une clé publique pour chiffrer et une clé privée pour déchiffrer, on peut aussi utiliser la clé privée pour générer une signature, et cette signature pourras être vérifier par la clé publique pour vérifier que celle ci à bien été faite par la clé privée ( dans le cas d’une authentification par exemple ) 

initialisation de la connexion, requête GET, application/data ?? 

On dit que TLS est un protocole hybride, car il utilise à la fois la cryptographie symétrique et la cryptographie symétrique.

On utilise donc du chiffrement asymétrique à l’initialisation de la connexion, une fois que a connexion est fiate et que les donénes applicatif passe, on bascule sur du de la cryptographie symétrique.

Plusieurs question se pose :
- Quel est la clé partagée ?
- Comment est-ce qu’on l’échange ?
- Comment est-ce qu’on chiffre le contenu ?
- Comment vérifier le certificat serveur ?
- Comment vérifier l’intégrité du contenu ? 
Pour cela le protocole inclus une initialisation qu’on appelle le « Hand Shake »  

TLS 1.2
![tls 1.2](img/tls/tls-1.2.png)
￼
Historiquement, dans les versions précédentes et jusqu’à (TLS 1.2) , la phase d’initialisation, ce hand shake, c’est 2 allez retour, ce qu’il faut retenir , cest que le client va proposer un certain nombre de réponse, qu’il supporte par rapport au sujet qu’on a aborder au dessus,	et il va le faire  en travers d’un champ particulier qui s’appelle le cipher suite ( suite cryptographique ) 
Premier échange
- Le client commence par informé le serveur ce qu’il supporte
- Le serveur va donc prendre en compte cette information  
Deuxième échange 
- Le client est le serveur s’échange la clé.

TLS 1.3
￼
![tls 1.3](img/tls/TLS-1.3)
TLS 1.3 est plus performant car il n’ya pas deux allez retour mais un seul, et si le client à déjà visiter le site web, alors  il ne refait pas cet allez retour, ce qui rend l’expérience utilisateurs plus agréable, la latence étant réduite. De plus il est plus sécurisé car il ne prend plus en charge les algorithme trop ancien ayant des vulnérabilité qui ont était découverte.
En TLS 1.3 le client part déjà d’un postulat ou le serveur propose déjà ce que lui supporte donc il ne l’informe plus de cela ( cipher suite ? )  et comme dans la plupart des cas c’est bon alors le serveur peut directement prendre en compte ce que le client supporte, sinon il feront comme précédemment en s’adaptant et en faisant les deux aller retour, mais dans la plupart des cas il n’y a plus ce problème. L’échange de clé se fait donc plus tôt ce qui permet de passer en clé symétrique plus rapidement. 

CIPHER SUITES  (Suite cryptographique)

Très important en 1.2 car c’est ce qui va définir notre niveau de sécurité 

 Les cipher suite sont ici ce qu’on peut retrouver lorsque l’on regarde les détails des certificat dans les site web
![cipher suits](img/tls/most-popular-cipher-suit.png)

Chaine de caractère « Cipher Suite »
![most popular cipher suits](img/tls/Algorithm-Strengh.png)
Key Exchange : Acronyme de « Eliptic Curve Diffie-Hellman Ephemeral » ou en français « Echange de clés Diffie-Hellman basé sur les courbes éliptiques » 
- EC : « Eliptic-Curve » Pour dire la manière, l’algorithme mathématique qui va être utilisé pour implémenter Diffie-Hellman, ( On à aussi un autre mode qui s’appelle RSA « Rivest Shamir Edleman » 
- DHE : « Diffie-Hellman Ephemeral » Ephemeral pour insister sur le fait qu’on va régénérer les clé à chaque fois.

