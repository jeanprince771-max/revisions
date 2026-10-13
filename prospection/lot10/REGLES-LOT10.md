# Règles du lot 10 : Suède, studios d'animation et de jeu vidéo (master prompt v7)

Le texte complet du brief est dans `/home/user/revisions/prospection/lot10/master-prompt-v7.txt`. Lis-le en entier : il fait foi. Ce fichier ajoute les contraintes techniques et le format exact.

## Contraintes techniques

- Le proxy réseau bloque l'ouverture des pages (WebFetch et curl renvoient 403). N'essaie pas de le contourner.
- Utilise uniquement WebSearch (charge-le avec ToolSearch, requête `select:WebSearch`). Le paramètre `allowed_domains` permet de lire les extraits d'un site précis (ex. `["gamehabitat.se"]`, `["dataspelsbranschen.se"]`, `["linkedin.com"]`).
- Budget : celui indiqué dans ta mission. Plusieurs agents partagent le même plafond de recherches : ne le dépasse pas.
- **Le DNS de l'environnement est hors service** (NXDOMAIN sur google.com). Ne tente pas de vérifier les MX. `verificationMX` = « non vérifié (DNS) » sur toutes les lignes.
- Pas de commit git. N'écris que dans tes deux fichiers de sortie, avec le module csv de Python (UTF-8).

## Règles non négociables

1. **N'invente jamais** un nom, un poste, un domaine ou un fait. Une personne est retenue si un extrait de recherche la cite dans son rôle actuel (idéalement deux sources, dont une de 2025-2026). Dis-le dans la note quand c'est un seul extrait.
2. **Indépendance obligatoire** : vérifie l'actionnariat de chaque studio (recherche « acquired by », « Embracer », « Stillfront », « MTG », « Tencent », « Thunderful », « Enad Global 7 », « Modern Times Group », « Remedy », « Keywords Studios »…). Un studio détenu par un groupe va dans les écartés, motif « actionnariat : détenu par X ». Exclus d'office : EA DICE, King, Mojang, Avalanche Studios Group, Paradox Interactive (et ses studios), Massive Entertainment, Sharkmob, et toute filiale d'Embracer, Stillfront, MTG, Tencent, Microsoft, Sony. Thunderful Group et Enad Global 7 sont aussi des groupes : leurs filiales sont exclues. Un studio qui a seulement un éditeur pour un jeu reste indépendant.
3. **Taille 2 à 50 personnes.** Activité prouvée 2025-2026 ; dernière preuve de plus de 2 ans = priorité C (cas limite).
4. **Contacts nominatifs** : prénom + nom + fonction (founder, co-founder, CEO, managing director, studio head, executive producer, head of production, head of business development, publishing manager). Pas de générique en contact principal ; un générique publié se note dans la colonne `note`.
5. **Emails** :
   - `publiée` : l'adresse exacte de la personne apparaît dans un extrait (site du studio, fiche festival/marché, presse). Note l'URL dans la note.
   - `devinée` : seulement si le domaine du studio est confirmé par un extrait du site. Cherche d'abord un format observé (`"@domaine.se"`). Format observé → utilise-le ; sinon prenom@ pour un studio de moins de 10 personnes, prenom.nom@ au-delà. Écris dans la note « format observé : … (URL) » ou « aucun format observé, prenom@ par défaut ». **Une seule adresse devinée par domaine** (pour le 1er contact) ; les autres personnes du studio vont en sans email, sauf adresse publiée. Translittère les caractères suédois (å→a, ä→a, ö→o, é→e).
   - `sans email` : domaine non confirmé ou 2e contact sans adresse publiée.
   - Ne devine **jamais** sur un domaine non confirmé.
6. **Un 1er contact par studio**, au maximum deux contacts supplémentaires notés « 2e contact (à envoyer plus tard) ».
7. **Icebreaker** en anglais : un fait précis et daté (sortie Steam/console avec date, prix ou nomination Swedish Game Awards / Nordic Game Awards, financement Swedish Film Institute ou Nordisk Film & TV Fond, festival, série diffusée), avec l'URL de la source dans `icebreakerSourceUrl`. Formule courte, au passé ou au présent, sans flatterie, ex. : « I saw that Starbreeze… » → non ; préférer « Congrats on the Nordic Game Award nomination for X in May 2025. » Sans fait sourcé : phrase de repli exacte « I am reaching out to a handful of {animation|game} studios in Sweden, and {studio} is one of them. » avec `icebreakerType` = « phrase de repli ».
8. Pas de valeur en français dans `secteur`, `icebreaker`, `firstName`, `companyName`, `ville` (ville en graphie locale : Stockholm, Malmö, Göteborg, Skövde, Umeå, Skellefteå, Visby). Les autres colonnes de suivi (pays, langue, typeStudio, statutEmail, note…) suivent les valeurs du brief, en français.
9. Ne reprends aucun studio cité dans `exclusions.txt` (s'il existe) ni un studio d'un autre pôle que le tien (si un studio a deux bureaux, il appartient au pôle de son siège).

## Format de sortie

Fichier principal `suede-{pole}-animation-jeu.csv`, 21 colonnes dans cet ordre :

email,firstName,lastName,companyName,jobTitle,linkedinUrl,secteur,icebreaker,icebreakerSourceUrl,icebreakerType,senderName,pays,ville,langue,priorite,typeStudio,tailleEquipe,actionnariat,statutEmail,verificationMX,note

- secteur : `animation studio` ou `game studio` (hybride : selon l'activité dominante)
- senderName : `Garry Yankson` ; pays : `Suède` ; langue : `anglais`
- priorite : A (studio actif 2025-2026, dirigeant confirmé par 2 sources, adresse publiée ou domaine confirmé) | B (actif, une seule source ou adresse devinée sans format observé) | C (cas limite : dernière preuve de plus de 2 ans, ou doute sur le périmètre)
- typeStudio : `animation` | `jeu` | `hybride`
- tailleEquipe : fourchette observée (ex. « 5-10 ») ou « non trouvée »
- actionnariat : `indépendant` (ou `indépendant (éditeur : X pour le jeu Y)`)
- statutEmail : `publiée` | `devinée` | `sans email` ; verificationMX : `non vérifié (DNS)`
- linkedinUrl : uniquement une URL vue telle quelle dans un résultat de recherche, sinon vide
- note : commence par `companyDomain=<domaine ou (non confirmé)> ; 1er contact.` ou `... ; 2e contact (à envoyer plus tard).`, puis sources, format email, générique publié, réserves.

Fichier des écartés `agent-0X-ecartes.csv` : colonnes `companyName,companyDomain,personne,motif,url`. Motifs clairs : « actionnariat : détenu par X », « taille > 50 », « pas d'activité 2025-2026 », « aucun dirigeant nommé », « hors périmètre (éditeur / agence / école) ».

## Rapport final (dernier message, en français, court)

Contacts livrés / quota ; 1ers contacts et 2es contacts ; publiées / devinées / sans email ; animation / jeu / hybride ; cas limites C ; studios écartés pour actionnariat (liste) ; studios exploitables en surplus (s'il y en a, laisse-les dans le fichier avec la note « réserve ») ; chemins des deux fichiers.
