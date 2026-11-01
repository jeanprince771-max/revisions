# Consignes : trouver un domaine, un LinkedIn et deviner l'email des alumni Artbox

Objectif de Garry : 60 alumni Artbox avec un email (trouvé ou deviné) pour un test Lemlist. 21 sont déjà faits ; il en faut au moins 39 de plus. Ton fichier d'entrée contient des alumni sans email, triés par pertinence.

## Pour chaque contact (dans l'ordre du fichier)

1. Cherche le **site professionnel** de la personne ou de sa marque / structure : site de la marque, boutique en ligne (Etsy ne compte pas comme domaine), portfolio perso (prenomnom.com, nommarque.am), lien en bio Instagram vu dans un extrait, fiche Spyur.am, page Behance qui cite un site, etc.
2. Cherche une **adresse publiée** sur ce domaine (`"@domaine"` avec allowed_domains, pages contact). Si une adresse nominative est publiée : statut « publiée ». Si une autre adresse nominative du même domaine est vue : devine sur ce format, statut « devinée (format observé : modèle) ».
3. Sinon, si le domaine est confirmé (vu en résultat de recherche, rattaché à la personne ou à sa structure) : **devine** prenom@domaine (structure < 10 personnes, artiste solo, petite marque) ou prenom.nom@domaine (institution, structure > 10). Statut « devinée (sans format observé) ». Translittération latine simple (Hovhannes → hovhannes, Tatevik → tatevik), sans accents.
4. Une adresse **gmail / mail.ru / yandex publiée par la personne elle-même** comme contact pro (bio, site, catalogue) peut être notée : statut « publiée (adresse personnelle) ». N'invente **jamais** une adresse gmail ou un domaine.
5. Une adresse **générique publiée** (info@, hello@, contact@ sur le domaine de la marque) : mets-la dans `emailGenerique`. Si la structure est un artiste solo ou une micro-marque, tu peux la mettre aussi dans `email` avec le statut « générique publiée » (Garry testera).
6. Cherche le **LinkedIn** personnel (`allowed_domains: ["linkedin.com"]`, nom + marque ou nom + Armenia). Ne le note que si le nom ET un élément (marque, ville, métier) correspondent ; sinon « à vérifier » dans la note.
7. Sans domaine trouvé : laisse `email` vide, statut « absente ». Passe au suivant sans t'acharner (2 à 3 recherches max par contact).

Priorise : les contacts qui ont une marque ou une structure (plus de chances d'avoir un site) et ceux de langue EN (diaspora). Les institutions publiques (musées) ont souvent un domaine officiel : cherche-le.

## Contraintes techniques

- Seulement WebSearch (ToolSearch `select:WebSearch`) ; le proxy bloque l'ouverture des pages, n'essaie pas. Liens : seulement ceux vus tels quels dans un résultat ; note « vu en résultat de recherche, non ouvert ».
- Budget : 55 recherches. Pas de commit git, ne touche ni à Lemlist ni à HubSpot. N'écris que ton fichier de sortie (module csv, UTF-8). Aucun tiret cadratin.
- N'invente jamais un nom, un poste, un domaine ou un fait.

## Fichier de sortie

Une ligne par contact du fichier d'entrée (y compris ceux restés sans email), colonnes dans cet ordre :

email,firstName,lastName,companyName,jobTitle,linkedinUrl,companyDomain,domaineSourceUrl,emailGenerique,statutEmail,formatEmail,pays,langue,programmeArtbox,promotion,pertinenceBlueprint,icebreaker,icebreakerSourceUrl,sourcePrincipale,note

- companyName propre (marque ou structure ; pour un artiste solo sans marque : prénom nom)
- statutEmail : publiée | publiée (adresse personnelle) | générique publiée | devinée (format observé : modèle) | devinée (sans format observé) | absente
- icebreaker : reprends « Fait daté pour accroche » de l'entrée s'il existe, ou un fait daté 2025-2026 que tu trouves (en anglais si langue EN) ; sinon vide.
- Rapport final (court, en français) : nombre d'emails par statut, LinkedIn trouvés, contacts restés sans email.
