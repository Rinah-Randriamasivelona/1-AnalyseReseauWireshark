# Projet 1 — Analyse de Trafic Réseau & Audit de Protocoles

Projet personnel réalisé dans le cadre du développement de mes
compétences en réseaux et cybersécurité.

Système : Kali Linux
Outil : Wireshark
Niveau : Junior — Infrastructure & Cybersécurité



## Protocoles analysés

| Protocole | Dossier | Port | Description |
|-----------|---------|------|-------------|
| DNS | dns/ | UDP/53 | Résolution de noms de domaine |
| TCP | tcp/ | TCP | Three-Way Handshake vers Wikipedia |
| ICMP | icmp/ | — | Ping Google — Echo Request/Reply |
| UDP | udp/ | UDP/53 | Transport sans connexion — DNS sur UDP |
| HTTP | http/ | TCP/80 | Requêtes et réponses HTTP en clair |



## I — Module DNS

Analyse du protocole DNS sous Wireshark.
Étude des requêtes et réponses DNS, types A et AAAA,
résolution de noms vers adresses IP.

Fichiers :
- dns/exo1-capt1.jpg — capture requête DNS
- dns/exo1-capt2.jpg — capture réponse DNS
- dns/exo1-capt1.odt — rapport requête
- dns/exo1-capt2.odt — rapport réponse

Éléments analysés :
1. Requête DNS — domaine recherché, type de requête
2. Réponse DNS — adresse IP retournée, champs d'autorité



## II — Module TCP

Analyse du Three-Way Handshake TCP lors d'une connexion
HTTPS vers Wikipedia.

Fichiers :
- tcp/analyser-wikipedia.org.pcapng — capture brute
- tcp/capt1-tcp-handshake.jpg — vue globale handshake
- tcp/capt2-tcp-SYN-ACK.jpg — étape SYN-ACK
- tcp/capt3-tcp-ACK.jpg — étape ACK finale
- tcp/capt1-tcp-handshake.odt — rapport SYN
- tcp/capt2-tcp-SYN-ACK.odt — rapport SYN-ACK
- tcp/capt3-tcp-ACK.odt — rapport ACK

Éléments analysés :
1. Paquet SYN (ligne 228) — demande de connexion client
2. Paquet SYN-ACK (ligne 232) — acceptation serveur
3. Paquet ACK (ligne 251) — confirmation client, connexion établie



## III — Module ICMP

Analyse du protocole ICMP via la commande ping vers Google.

Fichiers :
- icmp/analyse-ping-google.pcapng — capture brute
- icmp/capt1-icmp.jpg — Echo Request
- icmp/capt2-icmp.jpg — Echo Reply
- icmp/capt1-icmp.odt — rapport Echo Request
- icmp/capt2-icmp.odt — rapport Echo Reply

Éléments analysés :
1. Echo Request (ligne 19) — ping envoyé vers Google
2. Echo Reply (ligne 20) — réponse automatique du serveur



## IV — Module UDP

Analyse du protocole UDP en capturant des requêtes DNS
générées depuis le terminal avec les commandes :

    nslookup google.com
    dig facebook.com
    dig wikipedia.org

Six paquets analysés (244 à 249) — trois requêtes et
trois réponses DNS transportées par UDP.

Fichiers :
- udp/analyse-udp.pcapng — capture brute
- udp/rapport-udp.odt — rapport complet fusionné
- udp/capt1-terminal-udp.jpg — terminal avec les commandes
- udp/capt-paquet-244.jpg — requête DNS Google
- udp/capt-paquet-245.jpg — réponse DNS Google
- udp/capt-paquet-246.jpg — requête DNS Facebook
- udp/capt-paquet-247.jpg — réponse DNS Facebook
- udp/capt-paquet-248.jpg — requête DNS Wikipedia
- udp/capt-paquet-249.jpg — réponse DNS Wikipedia

Éléments analysés :
1. Paquet 244 — requête UDP/DNS Google (type AAAA - IPv6)
2. Paquet 245 — réponse UDP/DNS Google
3. Paquet 246 — requête UDP/DNS Facebook (type A - IPv4)
4. Paquet 247 — réponse UDP/DNS Facebook
5. Paquet 248 — requête UDP/DNS Wikipedia (type A - IPv4)
6. Paquet 249 — réponse UDP/DNS Wikipedia



## V — Module HTTP

Analyse du protocole HTTP en capturant du trafic en clair
généré depuis le terminal avec les commandes :

    curl http://example.com
    curl http://neverssl.com
    curl http://httpforever.com

Six paquets analysés (31, 35, 53, 55, 67, 71) — trois requêtes
GET et trois réponses 200 OK sur trois sites différents.

Fichiers :
- http/analyse-http.pcapng — capture brute
- http/rapport.pdf — rapport complet
- http/terminal.jpg — terminal avec les commandes curl
- http/capt1.jpg — requête GET example.com (paquet 31)
- http/capt2.jpg — réponse 200 OK example.com (paquet 35)
- http/capt3.jpg — requête GET neverssl.com (paquet 53)
- http/capt4.jpg — réponse 200 OK neverssl.com (paquet 55)
- http/capt5.jpg — requête GET httpforever.com (paquet 67)
- http/capt6.jpg — réponse 200 OK httpforever.com (paquet 71)

Éléments analysés :
1. Paquet 31 — requête GET example.com, User-Agent curl/8.15.0
2. Paquet 35 — réponse 200 OK, Server cloudflare, HTML 528 octets
3. Paquet 53 — requête GET neverssl.com, flags TCP PSH ACK
4. Paquet 55 — réponse 200 OK, Server Apache/2.4.66, HTML 3961 octets
5. Paquet 67 — requête GET httpforever.com, Connection keep-alive
6. Paquet 71 — réponse 200 OK, Server nginx/1.18.0 Ubuntu, HTML 5124 octets

Points clés observés :
- Tout le trafic HTTP circule en clair et est lisible dans Wireshark
- User-Agent révèle l'outil utilisé sur le réseau
- Server header révèle la version du logiciel serveur (banner grabbing)
- HTTP repose obligatoirement sur TCP en dessous
- HTTPS avec TLS chiffre tout ce trafic et le rend illisible



## Auteur

Rinah Randriamasivelona
Projet personnel — Infrastructure & Cybersécurité
