Projet 1 : Analyse de Trafic Réseau & Audit de Protocoles

I- Description du Module : Analyse DNS
Ce module présente ma première étude pratique du protocole DNS (Domain Name System) réalisée sous Kali Linux. L'objectif est de valider les concepts théoriques en analysant la structure et le comportement des requêtes et des réponses DNS.

Structure des Fichiers
   `README.md` : Présentation globale du projet.
    `dns/` : Dossier contenant les livrables de l'exercice.
       `exo1-capt1.jpg` & `exo1-capt2.jpg` : Captures d'écran ciblées de l'interface Wireshark.
       `exo1-capt1.odt` & `exo1-capt2.odt` : Rapports détaillés rédigés sous LibreOffice présentant l’analyse des paquets DNS.

Environnement Technique
*   Système d'exploitation : Kali Linux
*   Logiciel d'analyse : Wireshark
*   Protocole étudié : DNS (Port UDP/53)

Éléments Analysés dans cet Exercice
1.  Requête DNS (Query) : Identification du domaine recherché et vérification du type de requête
2.  Réponse DNS (Response) : Analyse de la réponse du serveur, vérification de l'adresse IP retournée et étude des champs d'autorité.


II- Description du Module : Analyse du Handshake TCP (HTTPS - Wikipedia)

Ce module présente mon étude pratique du protocole TCP (Transmission Control Protocol) réalisée sous Kali Linux lors d'une connexion sécurisée vers Wikipedia. L'objectif est de valider les concepts théoriques du Three-Way Handshake en analysant la structure des drapeaux (flags) TCP ainsi que le comportement des paquets réseau.

Structure des Fichiers
`README.md` : Présentation globale du projet.
`tcp/` : Dossier contenant les livrables de l'exercice.
- `analyser-wikipedia.org.pcapng` : Capture brute du trafic réseau.
- `capt1-tcp-handshake.jpg`, `capt2-tcp-SYN-ACK.jpg` et `capt3-tcp-ACK.jpg` : Captures d'écran ciblées de l'interface Wireshark.
- `capt1-tcp-handshake.odt`, `capt2-tcp-SYN-ACK.odt` et `capt3-tcp-ACK.odt` : Rapports détaillés rédigés sous LibreOffice présentant l’analyse de chaque étape du handshake TCP.

Environnement Technique
- Système d'exploitation : Kali Linux
- Logiciel d'analyse : Wireshark
- Protocole étudié : TCP / HTTPS (Port 443)

Éléments Analysés dans cet Exercice

1. Étape 1 : Paquet [SYN] (Ligne 228)
Demande de connexion initiale du client, analyse du drapeau SYN (0x002) et initialisation du numéro de séquence TCP.

2. Étape 2 : Paquet [SYN, ACK] (Ligne 232)
Acceptation de la connexion par le serveur, analyse du drapeau SYN-ACK (0x012) et observation du temps aller-retour (RTT).

3. Étape 3 : Paquet [ACK] (Ligne 251)
Confirmation finale du client, validation du drapeau ACK (0x010) et établissement officiel de la connexion TCP avant le démarrage du chiffrement TLSv1.3.


Auteur

Projet personnel réalisé dans le cadre du développement de mes compétences en réseaux et cybersécurité.

Rina Randriamasivelona

