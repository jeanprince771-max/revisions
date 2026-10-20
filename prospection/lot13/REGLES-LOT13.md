# Règles du lot 13 : Royaume-Uni, animation et jeu vidéo indépendants (master prompt v12)

Le brief complet est dans `/home/user/revisions/prospection/lot13/master-prompt-v12.txt`. Lis-le en entier : il fait foi (paliers, déclencheurs, score, détection de format, colonnes). Ce fichier ajoute les contraintes techniques.

## Avant toute recherche : dédoublonnage

`/home/user/revisions/prospection/lot13/exclusions.txt` liste les 215 sociétés du lot 11 (Royaume-Uni), les sociétés déjà dans Lemlist / HubSpot, le lot Irlande et des groupes exclus. Lis-le **avant** de chercher et ne reprends aucune de ces sociétés (même retenue au lot 11).

## Contraintes techniques

- Le proxy réseau bloque l'ouverture des pages (WebFetch et curl : 403). N'essaie pas de le contourner. Utilise uniquement WebSearch (ToolSearch, `select:WebSearch`). `allowed_domains` permet de lire les extraits d'un site précis (ex. `["find-and-update.company-information.service.gov.uk"]`, `["store.steampowered.com"]`, `["ukgamesfund.com"]`, `["animationuk.org"]`, `["linkedin.com"]`, ou le domaine du studio pour son press kit : `["<domaine>"]` avec une requête `press kit contact email` ou `"@<domaine>"`).
- **Liens** : on ne peut pas ouvrir les pages. Un lien n'est livré que s'il apparaît **tel quel dans un résultat de recherche**. Ne construis jamais une URL. Dans `note` : « liens vus en résultat de recherche, non ouverts ». Un fait daté vu dans un extrait compte comme FACT seulement si l'extrait montre le fait et la date ; sinon SIGNAL.
- **DNS hors service** (NXDOMAIN sur google.com) : aucun MX vérifiable. `verificationMX` = « non vérifié (DNS) » partout. Conséquence (règle bloquante du brief) : aucune adresse reconstruite (C1/C2) n'entre dans l'import ; elle ira dans `contacts-serveur-muet.csv` à la consolidation. Fais quand même tout le travail de format : Garry fera tester les domaines dans Lemlist.
- **Score Accès** sans MX : 15 pour une adresse publiée (A) ; pour une reconstruite, note ce que la ligne vaudrait (12 en C1, 8 en C2) mais écris dans la note « accès provisoire, MX non vérifié ».
- Budget : celui de ta mission. Plusieurs agents partagent le plafond.
- Pas de commit git. N'écris que dans tes deux fichiers de sortie, module csv de Python, UTF-8. Ne touche pas à Lemlist ni à HubSpot.

## Adresses : la règle la plus importante

1. Cherche d'abord une adresse **publiée** de la personne (qualité A) : press kit (`"<studio>" press kit`, `"<domaine>" presskit`), page contact/équipe/mentions légales, Steam/itch.io, annuaires (Animation UK, Ukie, TIGA, Games London), catalogues de marchés (Cartoon Forum, MIFA, CMC), Kickstarter, offres d'emploi.
2. Sinon, **collecte les adresses réelles du domaine** (n'importe quelle personne) avec `"@<domaine>"`. Une seule adresse nominative observée = format C2 ; deux adresses cohérentes = C1. Génériques (info@, hello@, press@, jobs@) : ne donnent pas de format nominatif, mais vont dans `emailGenerique`.
3. **Aucun format observé = adresse interdite** (qualité D) : laisse `email` vide, `statutEmail` = « sans email », et écris dans la note « format inconnu » (la ligne ira dans `contacts-format-inconnu.csv`). Ne devine PAS par défaut, contrairement aux lots précédents.
4. Applique le format au nom exact lu sur Companies House ; note les autres orthographes dans `variantesEmail`.
5. Pas de gmail ni d'adresse personnelle.

## Autres points (rappel du brief)

- Numéro Companies House et statut **active** obligatoires (sinon la ligne ne part pas : écartée). Formes : Ltd, PLC, LLP, CIC. Vérifie PSC / groupe de rattachement : beaucoup de studios britanniques ont été rachetés.
- Effectif strictement < 30 (1-4 = HOLD sauf IP propre et production prouvée).
- Jeu vidéo : exclure si éditeur exclusif, ou si tous les jeux sortent chez le même éditeur ; note l'éditeur dans `editeurAttitre`.
- République d'Irlande, îles Anglo-Normandes, île de Man : exclues. Irlande du Nord : incluse.
- Date de référence des déclencheurs : 2026-10-20.
- Une ligne en C2 ne peut pas être PRIORITY ; une phrase de repli non plus.
- Aucun tiret cadratin. Pas de français dans `secteur`… attention : le brief impose des valeurs françaises pour `secteur` (animation | jeu video | hybride | production | vfx-post) et `typeStudio` : utilise-les, ce ne sont pas des variables d'e-mail. `companyName`, `firstName`, `jobTitle`, `icebreaker`, `ville` restent en anglais.

## Format de sortie

Fichier principal (nom dans ta mission), 47 colonnes dans l'ordre du brief :

email,firstName,lastName,companyName,jobTitle,linkedinUrl,palier,secteur,typeStudio,tailleEquipe,sourceTailleEquipe,formeJuridique,numeroCompaniesHouse,statutSociete,actionnariat,editeurAttitre,ville,nation,region,declencheur,declencheurType,declencheurDate,declencheurSourceUrl,contreSignal,icebreaker,icebreakerSourceUrl,icebreakerType,qualiteEmail,formatEmailObserve,nbAdressesObservees,sourceFormat,variantesEmail,emailGenerique,verificationMX,scoreDeclencheur,scoreICP,scoreBesoin,scoreAcces,scoreValeur,score,decision,senderName,pays,langue,priorite,statutEmail,note

- statutEmail : publiee | reconstruite | sans email ; qualiteEmail : A | B | C1 | C2 | (vide si sans email)
- decision : PRIORITY | COLD_OK | HOLD (EXCLUDE va dans les écartés)
- icebreakerType : fait sourcé | phrase de repli
- note : commence par `companyDomain=<domaine ou (non confirmé)> ; 1er contact.` ou `... ; 2e contact (à envoyer plus tard).` (au plus 2 seconds contacts par société) ; au-delà de ton quota : `... ; 1er contact ; réserve.` Puis : raison sociale et numéro Companies House, sources (effectif, PSC, dirigeant), adresses observées sur le domaine, HYPOTHESIS éventuelles, réserves.

Écartés `agent-XX-ecartes.csv` : `companyName,companyDomain,personne,motif,url`. Motifs : « doublon lot 11 », « taille ≥ 30 (chiffre, source) », « actionnariat : détenu par X », « éditeur exclusif : X », « work for hire sans IP », « République d'Irlande », « Companies House : numéro non trouvé / statut non actif », « pas d'activité 2025-2026 », « aucun dirigeant nommé », « EXCLUDE score X : raison ».

## Rapport final (dernier message, en français, court)

Sociétés livrées / quota, par palier ; PRIORITY / COLD_OK / HOLD ; FACT fort / moyen / SIGNAL / repli ; qualité des adresses A / C1 / C2 / sans email et motifs de format observés ; tranches d'effectif ; écartés par motif (taille avec chiffre, groupe, éditeur) ; chemins des fichiers.
