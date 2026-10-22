# Règles du lot 14 : studios d'animation et sociétés de production de films indépendantes, Royaume-Uni et Suède

Demande de Garry (22/10/2026) : 30 studios d'animation ou sociétés de production de films indépendantes au Royaume-Uni ou en Suède, de moins de 40 personnes, avec des contacts nominatifs. Les adresses non trouvées sont devinées selon ce que nous savons déjà ; Garry les teste dans Lemlist.

## Contraintes techniques

- Le proxy bloque l'ouverture des pages (WebFetch et curl : 403). N'essaie pas de le contourner. Utilise uniquement WebSearch (ToolSearch, `select:WebSearch`). `allowed_domains` permet de lire un site précis.
- Liens : seulement ceux vus tels quels dans un résultat de recherche. Ne construis jamais une URL.
- DNS hors service : `verificationMX` = « non vérifié (DNS) ». Garry testera dans Lemlist.
- Budget : celui de ta mission. Pas de commit git. Ne touche pas à Lemlist ni à HubSpot. N'écris que dans tes deux fichiers (module csv de Python, UTF-8).

## Cible

- **Studios d'animation indépendants** et **sociétés de production de films indépendantes** (longs et courts métrages de fiction ou documentaires, cinéma d'auteur, coproductions). Pas les grands groupes ni leurs filiales (voir `exclusions.txt`), pas les agences de pub sans production propre, pas les écoles.
- **Moins de 40 personnes** (vérifie sur LinkedIn, le site, Companies House ou allabolag.se ; sinon « non trouvée »).
- **Activité prouvée en 2025 ou 2026** : film en production, sortie, financement (BFI, BFI Doc Society, Screen Scotland, Ffilm Cymru, Northern Ireland Screen, Film4, BBC Film ; Svenska Filminstitutet, Film i Väst, Filmpool Nord, Nordisk Film & TV Fond, Creative Europe MEDIA), sélection en festival (Cannes, Berlin, Venise, Toronto, Sundance, Annecy, Göteborg, Sheffield DocFest, CPH:DOX, Edinburgh, Glasgow).
- **Société enregistrée** : Ltd / LLP / CIC (Companies House, numéro à noter) ou AB (Suède, numéro d'organisation si vu). Pas de sole trader.
- **Aucune société de `exclusions.txt`** (lots 10, 11 et 13 : 448 noms).

## Contacts

- Nominatif obligatoire : prénom, nom, fonction (founder, co-founder, CEO, managing director, producer / producent qui dirige la société, executive producer, head of development).
- Une personne principale par société ; au plus 2 « 2e contact (à envoyer plus tard) ».

## Adresses : publiée d'abord, sinon devinée (Garry l'a demandé)

1. Cherche l'adresse publiée de la personne : page contact ou équipe, press kit, fiche festival / marché, annuaire (Pact, Animation UK, Svenska Filminstitutet, Film i Väst), communiqué, offre d'emploi. `statutEmail` = publiée.
2. Sinon cherche le format sur le domaine (`"@<domaine>"`) : une adresse nominative d'une autre personne suffit.
3. Sinon **devine**, à condition que le domaine soit confirmé par un extrait (jamais de domaine inventé, jamais de gmail) :
   - format observé sur le domaine → applique-le ;
   - **Royaume-Uni, moins de 10 personnes : prenom@** (motif majoritaire observé au lot 13, et prenom@ validé 4 fois sur 4 dans Lemlist sur de petits studios en Irlande) ;
   - **Royaume-Uni, 10 personnes ou plus : prenom.nom@** ;
   - **Suède : prenom@ pour les très petites sociétés (moins de 5), prenom.nom@ sinon** (format le plus courant en Suède) ; translittère å→a, ä→a, ö→o, é→e.
   - Une seule adresse devinée par domaine pour le 1er contact ; les 2es contacts suivent le même format.
   - `statutEmail` = devinée ; note le format et la raison dans `formatEmail`.
4. Domaine introuvable → `statutEmail` = sans email.

## Icebreaker

Une phrase en anglais, sobre, fondée sur un fait daté et sourcé (URL dans `icebreakerSourceUrl`, `icebreakerType` = fait sourcé). Sinon phrase de repli : « I am reaching out to a handful of independent {animation studios|film production companies} in {the UK|Sweden}, and {companyName} is one of them. » (`icebreakerType` = phrase de repli). Pas de tiret cadratin.

## Format de sortie

Fichier principal (nom dans ta mission), colonnes dans cet ordre :

email,firstName,lastName,companyName,jobTitle,linkedinUrl,companyDomain,pays,ville,secteur,tailleEquipe,formeJuridique,numeroSociete,icebreaker,icebreakerSourceUrl,icebreakerType,statutEmail,formatEmail,emailGenerique,verificationMX,senderName,note

- pays : Royaume-Uni | Suède ; secteur : animation studio | film production company ; senderName : Garry Yankson
- companyName propre (sans Ltd ni AB, sans virgule) ; firstName, companyName, icebreaker, senderName jamais vides
- note : commence par `1er contact.` ou `2e contact (à envoyer plus tard).`, puis : source du nom et du poste, source de l'effectif, fait daté, raison du format d'adresse, réserves. « liens vus en résultat de recherche, non ouverts ».

Écartés `agent-XX-ecartes.csv` : `companyName,companyDomain,personne,motif,url`.

## Rapport final (dernier message, en français, court)

Sociétés livrées / quota ; animation / film ; publiées / devinées (par format) / sans email ; écartés par motif ; chemins des fichiers.
