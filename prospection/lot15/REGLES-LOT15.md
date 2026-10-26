# Règles du lot 15 : studios d'animation 2D indépendants (Royaume-Uni, Irlande, Suède, Amérique latine)

Le brief complet est dans `/home/user/revisions/prospection/lot15/master-prompt-anim2d.txt`. Lis-le en entier : il fait foi (périmètre 2D, taille < 40, indépendance, exclusions, contact, adresses, icebreaker, score, colonnes). Ce fichier ajoute les contraintes techniques et précise trois points.

## Contraintes techniques

- Le proxy bloque l'ouverture des pages (WebFetch, curl : 403). N'essaie pas de le contourner. Utilise uniquement WebSearch (ToolSearch, `select:WebSearch`). `allowed_domains` permet de lire un site précis (le domaine du studio pour `"@<domaine>"`, `["linkedin.com"]`, `["find-and-update.company-information.service.gov.uk"]`, `["solocheck.ie"]`, `["allabolag.se"]`…).
- Liens : seulement ceux vus tels quels dans un résultat de recherche. Ne construis jamais une URL. Écris dans la note « liens vus en résultat de recherche, non ouverts ».
- DNS hors service : `verificationMX` = « non vérifié (DNS) ».
- **Anti-doublon Lemlist / HubSpot : c'est l'orchestrateur qui le fait à la consolidation, en lecture seule.** Toi, tu ne touches pas à Lemlist ni à HubSpot. Tu vérifies seulement les exclusions du brief et `exclusions-historique.txt`.
- Budget : celui de ta mission. Pas de commit git. N'écris que dans tes deux fichiers (module csv de Python, UTF-8).

## Précisions

1. **Exclusions.** En plus de la liste du brief, ne reprends aucune société de `/home/user/revisions/prospection/lot15/exclusions-historique.txt` (lots 1 à 14). **Exception** : les studios 2D déjà livrés au lot 12 (Irlande : Treehouse Republic, Ink and Light, Turnip and Duck, Igloo Animations, Little Moon Animation, Dream Logic Studios, Distillery Films, Studio Meala, Pictor) et au lot 10 (Suède : LEE Film, Cinematic, Kaktus Film, Filmic Animation, Double Up Studio, Studio Konkret, Studio Fyr) peuvent être repris s'ils font de la 2D, parce que plusieurs n'ont jamais été importés dans Lemlist. Mets « déjà livré au lot 12 » ou « déjà livré au lot 10 » au début de la note ; l'orchestrateur écartera ceux qui sont déjà dans Lemlist.
2. **Adresses : règle stricte du brief.** Adresse publiée d'abord. Sinon, devine **uniquement** à partir d'un format réellement observé sur le même domaine (une autre adresse nominative vue dans un extrait) et écris l'adresse modèle dans `formatEmail` (ex. « prenom@ (modèle : ana@estudio.com.ar, vue sur …) »). Sans format observé : `email` vide, `statutEmail` = absente, générique dans `emailGenerique`. Un format majoritaire du pays n'autorise pas une devinette.
3. **Score et décision.** Score sur 100 réparti en cinq critères (pertinence 2D, indépendance, qualité de l'adresse, fraîcheur et solidité du déclencheur, signal international) : détaille-les dans la note, ex. `score : 2D 20/20, indépendance 20/20, adresse 15/20, déclencheur 15/20, international 10/20`. COLD_OK ≥ 65 avec adresse exploitable ; HOLD 50-64 ou sans adresse ; < 50 = écarté. Un studio sans fait daté des 12 derniers mois (date de référence 2026-10-26) est HOLD, pas éliminé.

## Format de sortie

Fichier principal (nom dans ta mission), colonnes dans cet ordre :

pays,rangContact,email,firstName,lastName,companyName,jobTitle,linkedinUrl,companyDomain,ville,technique2D,tailleEquipe,formeJuridique,numeroSociete,icebreaker,icebreakerSourceUrl,icebreakerType,statutEmail,formatEmail,emailGenerique,verificationMX,score,decision,contreSignal,note

- pays en français (Royaume-Uni, Irlande, Suède, Argentine, Chili, Colombie, Mexique, Brésil, Uruguay, Pérou…)
- rangContact : 1 (contact principal) ou 2 (second contact, au plus un par société)
- icebreakerType : FACT fort | FACT moyen | SIGNAL | (vide si aucun) ; icebreaker dans la langue du destinataire (anglais UK/Irlande/Suède, espagnol Amérique hispanophone, portugais Brésil). Sans fait daté : laisse l'icebreaker vide, la ligne sera HOLD.
- statutEmail : publiee | devinee | absente
- decision : COLD_OK | HOLD
- companyName propre (sans Ltd, AB, S.A., S.R.L., virgule)
- Aucun tiret cadratin.

Écartés `agent-XX-ecartes.csv` : `companyName,companyDomain,personne,motif,url` (motifs : 3D exclusif, stop-motion exclusif, VFX, jeu vidéo, taille ≥ 40, actionnariat : X, liquidation / dormante, déjà prospecté, pas de dirigeant nommé, score < 50).

## Rapport final (dernier message, en français, court)

Studios livrés / quota ; COLD_OK / HOLD ; publiées / devinées (avec modèle) / absentes ; déclencheurs par type ; écartés par motif ; chemins des fichiers.
