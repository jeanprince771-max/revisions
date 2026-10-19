# Règles du lot 12 : Irlande, studios d'animation (master prompt v11)

Le brief complet est dans `/home/user/revisions/prospection/lot12/master-prompt-v11.txt`. Lis-le en entier : il fait foi (paliers, déclencheurs, score sur 100, colonnes). Ce fichier ajoute les contraintes techniques et précise quelques points.

## Contraintes techniques

- Le proxy réseau bloque l'ouverture des pages (WebFetch et curl : 403). N'essaie pas de le contourner. Utilise uniquement WebSearch (ToolSearch, `select:WebSearch`). `allowed_domains` permet de lire les extraits d'un site précis (ex. `["animationireland.com"]`, `["screenireland.ie"]`, `["core.cro.ie"]`, `["solocheck.ie"]`, `["vision-net.ie"]`, `["linkedin.com"]`).
- **Liens** : on ne peut pas ouvrir les pages. Un lien n'est livré que s'il apparaît **tel quel dans un résultat de recherche**. Ne construis jamais une URL. Dans `note` : « liens vus en résultat de recherche, non ouverts ». En conséquence, un fait daté vu dans un extrait de recherche compte comme FACT seulement si l'extrait montre la date et le fait ; sinon c'est un SIGNAL.
- **DNS hors service** : pas de vérification MX. `verificationMX` = « non vérifié (DNS) ». Aucune adresse devinée n'a donc de domaine « qui répond » : le critère Accès au décideur vaut au plus **5** pour une adresse devinée (règle du brief : 10 = format vérifié sur un domaine qui répond), 15 pour une adresse publiée.
- Budget : celui de ta mission. Plusieurs agents partagent le plafond de recherches.
- Pas de commit git. N'écris que dans tes deux fichiers de sortie, module csv de Python, UTF-8.
- Ne touche pas à Lemlist ni à HubSpot.

## Points clés (rappel du brief)

1. **République d'Irlande uniquement.** Vérifie le siège : tout studio d'Irlande du Nord est exclu (voir `exclusions.txt`).
2. **Numéro CRO obligatoire** (`numeroCRO`). Cherche `"<nom>" CRO number` ou sur solocheck.ie / vision-net.ie / core.cro.ie / opencorporates. Sans numéro CRO vu dans un extrait, la ligne ne part pas : mets-la dans les écartés avec le motif « numéro CRO non trouvé ». Sole traders et partenariats exclus.
3. **Effectif strictement < 30** (1-4 = HOLD sauf IP propre et production prouvée ; 30+ = exclu). Source : LinkedIn, CRO, page équipe. Jamais de chiffre inventé : « non trouvée » sinon.
4. **Actionnariat** : vérifie systématiquement. Plusieurs grands studios irlandais appartiennent à des groupes (à vérifier toi-même, par exemple Brown Bag Films, Cartoon Saloon, Boulder Media, Piranha Bar, Moetion, Kavaleer, Telegael, Lighthouse Studios, JAM Media, Daily Madness…). Coentreprise créée pour servir un partenaire étranger = exclue.
5. **Contre-signaux** : head of sales / international / distribution, ou distributeur attitré → note-le dans `contreSignal` et baisse Besoin.
6. **Déclencheur** : fait daté (AAAA-MM) avec URL vue en résultat. Date de référence : 2026-10-19. < 6 mois = plein, 6-12 mois = moitié, > 12 mois = 0 et plafond COLD_OK. Le contexte sectoriel (Animation Ireland, Irish Times du 14 octobre 2026) n'est jamais un déclencheur ni un icebreaker.
7. **Score** : 5 notes (scoreDeclencheur, scoreICP, scoreBesoin, scoreAcces, scoreValeur) + total. PRIORITY ≥ 80, COLD_OK 65-79, HOLD 50-64, EXCLUDE < 50 (va dans les écartés avec la raison). Une ligne avec phrase de repli ne peut pas être PRIORITY. Une société avec seulement une HYPOTHESIS ne dépasse pas HOLD.
8. **Paliers** : épuise le palier 1 avant le 2, etc. Note le palier.
9. **Emails** : publiée (adresse exacte vue dans un extrait) > devinée (domaine de la société lu dans un extrait, format observé si possible via `"@domaine.ie"`, sinon prenom@ < 10 pers., prenom.nom@ au-delà) > sans email. Jamais de gmail. Ne déduis jamais un domaine .ie : lis-le. Garry veut des adresses : quand le domaine est confirmé, devine l'adresse du 1er contact.
10. **Une seule personne par société** dans le fichier principal ; au plus 2 autres personnes notées « 2e contact (à envoyer plus tard) » (elles ne comptent pas dans les 20).
11. **Aucun tiret cadratin** (—) nulle part. Pas de valeur en français dans `secteur`, `typeStudio` n'est pas une variable (valeurs du brief), `icebreaker`, `firstName`, `companyName`, `jobTitle`, `ville`, `comte`.
12. Icebreaker : nomme le fait, ne le commente pas. Repli exact : « I am reaching out to a handful of independent animation studios in Ireland, and {companyName} is one of them. »

## Format de sortie

Fichier principal (nom dans ta mission), 38 colonnes dans cet ordre :

email,firstName,lastName,companyName,jobTitle,linkedinUrl,palier,secteur,typeStudio,tailleEquipe,sourceTailleEquipe,formeJuridique,numeroCRO,actionnariat,ville,comte,declencheur,declencheurType,declencheurDate,declencheurSourceUrl,contreSignal,icebreaker,icebreakerSourceUrl,icebreakerType,scoreDeclencheur,scoreICP,scoreBesoin,scoreAcces,scoreValeur,score,decision,senderName,pays,langue,priorite,statutEmail,verificationMX,note

- secteur en anglais (« animation studio », « game studio », « production company », « VFX studio ») ; typeStudio : animation | hybride animation-jeu | jeu | production | vfx-post
- declencheurType : FACT fort | FACT moyen | SIGNAL | (vide si aucun) ; icebreakerType : fait sourcé | phrase de repli
- decision : PRIORITY | COLD_OK | HOLD ; senderName `Garry Yankson` ; pays `Irlande` ; langue `anglais`
- priorite : A (adresse publiée + déclencheur < 6 mois) | B | C (cas limite)
- statutEmail : publiée | devinée | sans email ; verificationMX : non vérifié (DNS)
- note : commence par `companyDomain=<domaine ou (non confirmé)> ; 1er contact.` ou `... ; 2e contact (à envoyer plus tard).` ; si au-delà de ton quota : `... ; 1er contact ; réserve.` Puis : raison sociale, sources (effectif, CRO, actionnariat, dirigeant), format email, générique publié, HYPOTHESIS éventuelles, réserves.

Écartés `agent-XX-ecartes.csv` : `companyName,companyDomain,personne,motif,url`. Motifs : « taille ≥ 30 (chiffre, source) », « actionnariat : détenu par X », « Irlande du Nord », « numéro CRO non trouvé », « pas d'activité 2025-2026 », « aucun dirigeant nommé », « EXCLUDE score X : raison », « hors périmètre ».

## Rapport final (dernier message, en français, court)

Sociétés livrées / quota par palier ; PRIORITY / COLD_OK / HOLD ; FACT fort / FACT moyen / SIGNAL / repli ; tranches d'effectif ; contre-signaux ; publiées / devinées / sans email ; écartés par motif (taille avec chiffre, actionnariat avec groupe) ; chemins des fichiers.
