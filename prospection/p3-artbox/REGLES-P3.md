# Règles de travail P3 : alumni Artbox / Creative Armenia

Le brief complet est dans `/home/user/revisions/prospection/p3-artbox/master-prompt-p3.md`. Lis-le en entier : il fait foi pour le périmètre, les phases et les colonnes. Ce fichier ajoute les contraintes techniques.

## Contraintes techniques

- Le proxy bloque l'ouverture des pages (WebFetch et curl : 403). N'essaie pas de le contourner. Utilise uniquement WebSearch (ToolSearch, `select:WebSearch`). `allowed_domains` permet de lire les extraits d'un site précis : `["artbox.am"]`, `["creativearmenia.org"]`, `["linkedin.com"]`, `["instagram.com"]`, `["facebook.com"]`, `["mirrorspectator.com"]`, `["armenpress.am"]`, `["arka.am"]`, `["civilnet.am"]`, `["evnreport.com"]`, `["hetq.am"]`, `["azatutyun.am"]`, etc. Cherche aussi en arménien et en russe (Artbox, Արթբոքս, Creative Armenia, Քրեատիվ Արմենիա).
- Liens : seulement ceux vus tels quels dans un résultat de recherche. Ne construis jamais une URL. Note « vu en résultat de recherche, non ouvert ».
- DNS hors service : pas de vérification MX.
- Ne touche pas à Lemlist ni à HubSpot (l'orchestrateur s'en charge en lecture seule). Pas de commit git. N'écris que dans tes fichiers de sortie, module csv de Python, UTF-8.

## Règles

- N'invente jamais un nom, un poste, une entreprise, un fait. En cas de doute : « à vérifier ».
- Chaque ligne a au moins une URL source.
- Relation avec Garry Yankson : « contact direct » seulement si une source le prouve (publication citant Garry Yankson avec cette personne ou cette entreprise, session documentée). Sinon « alumni de l'écosystème Artbox ».
- Emails : publié sur une source officielle = « vérifié » ; sinon format observé sur le domaine = « deviné (format observé : modèle) » ; sinon, **à la demande de Garry, deviner quand même si le domaine professionnel de l'entreprise est confirmé** : prenom@ pour une structure de moins de 10 personnes (format le plus fréquent chez les petites structures), prenom.nom@ au-delà ; translittération latine de l'arménien (ex. Hovhannes → hovhannes) ; statut « deviné (sans format observé, prenom@ par défaut) ». Jamais de gmail / mail.ru inventé ; une adresse personnelle publiée par la personne comme contact pro peut être notée avec le signalement « adresse personnelle ». Pas de domaine inventé.
