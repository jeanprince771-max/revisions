# Règles du lot 2 (prospection Afrique anglophone)

## Contexte : ce que le lot 1 nous a appris (résultats Lemlist réels)

Sur 34 emails devinés en prenom.nom@domaine :
- 4 livrables : stuart.forrest@triggerfish.com, phil.cunningham@ et jacqui.cunningham@sunriseproductions.tv, gwamaka.mwabuka@tai.or.tz.
- 5 risqués (domaines catch-all) : Nemsia Studios (2), Anthill Studios, Moving Shot Pictures, Creatures Animation.
- 25 inexploitables.

Ce qui a marché :
1. Des structures **établies et anciennes** (Triggerfish, Sunrise : 20+ ans, équipes nombreuses), avec messagerie Google Workspace ou Microsoft 365. Dans ces maisons, prenom.nom@ est courant.
2. Des dirigeants **connus et cités partout** dans la presse spécialisée, dans le rôle actuel.

Ce qui a échoué :
1. **Domaines sans serveur mail** (aucun MX) ou inexistants : 7 échecs sur 25 auraient pu être évités par une simple vérification DNS.
2. **Noms périmés** : emma.kaye@triggerfish.com est inexploitable alors que stuart.forrest@ sur le même domaine est livrable. Le format était bon, mais la personne n'y est sans doute plus. Un nom tiré d'un seul extrait de recherche peut être daté.
3. **Petits studios** (fondateur + quelques personnes) : prenom.nom@ y échoue souvent ; ils utilisent plutôt prenom@.

## Contrainte technique

Le réseau de l'environnement bloque l'ouverture des pages web (WebFetch et curl renvoient 403 / EGRESS_BLOCKED). **N'essaie pas de contourner le proxy.** Tu peux :
- utiliser **WebSearch** (charge-le avec ToolSearch, requête `select:WebSearch`) ;
- vérifier les serveurs mail par DNS en Bash (cela fonctionne) :

```
python3 -c "
import dns.resolver,sys
for d in sys.argv[1:]:
    try: print(d, sorted(str(r.exchange) for r in dns.resolver.resolve(d,'MX',lifetime=6)))
    except Exception as e: print(d, 'ECHEC', type(e).__name__)
" domaine1.com domaine2.co.za
```

## Règles

1. **Exclusions** : ne reprends aucune structure listée dans `/home/user/revisions/prospection/lot2/exclusions-deja-vues.txt` (déjà traitée au lot 1), ni filiales de grands groupes internationaux (Netflix, Disney, Showmax/MultiChoice, Skydance…).
2. **Cible prioritaire** : structures établies (idéalement 5 ans d'existence ou plus, au moins 3 productions ou clients visibles, activité 2025-2026 visible dans les résultats de recherche). Postes : CEO / Managing Director / fondateur dirigeant, puis Head of Content / Head of Production, puis Head of Partnerships.
3. **Nom et poste** : retiens une personne seulement si **au moins deux résultats de recherche indépendants** (sources différentes) la citent dans ce rôle, dont au moins un daté de 2025 ou 2026. Note les deux URL (personSourceUrl = la meilleure, l'autre dans note). N'invente jamais un nom.
4. **Domaine** : le domaine doit apparaître dans les résultats de recherche comme site de la structure. Puis **vérifie le MX** avec la commande ci-dessus. Pas de MX ou domaine inexistant → la structure va dans les écartés (motif « aucun serveur mail »). Note le fournisseur (Google, Microsoft, autre) dans la note.
5. **Modèle d'email observé** : avant de deviner, cherche des emails réellement publiés sur ce domaine avec WebSearch, par exemple `"@domaine.com"`, `"@domaine.com" email`, `domaine.com contact email producer`. Si un extrait de recherche montre une adresse nominative sur ce domaine (n'importe quelle personne), c'est un modèle observé : note l'URL dans modeleSourceUrl, le modèle en clair dans confiance (ex. « prenom@ observé dans un extrait de recherche »), et précise dans note que c'est un extrait, pas une page ouverte. Si l'adresse de la personne cible elle-même apparaît, statutEmail = publie et emailSourceUrl = l'URL du résultat.
6. **Sans modèle observé** : propose prenom.nom@ pour une structure de plus d'environ 10 personnes, prenom@ pour un petit studio. Écris dans confiance exactement « aucun modèle observé (prenom.nom@ choisi : grande structure) » ou « aucun modèle observé (prenom@ choisi : petite structure) ».
7. Email générique (info@, hello@…) dans emailGenerique seulement s'il apparaît dans un résultat de recherche.
8. fiabilite = « solide » seulement si le nom vient de 2 sources dont une de 2025-2026 ET que le modèle est observé ; sinon « a verifier ».
9. Quota : 6 contacts. Si le lot est pauvre, livre moins et explique en deux lignes. Ne baisse pas la qualité pour atteindre le chiffre.

## Format de sortie

CSV UTF-8 écrit avec le module csv de Python, 18 colonnes dans cet ordre :

firstName,lastName,email,companyName,companyDomain,jobTitle,country,zone,statutEmail,confiance,personSourceUrl,emailSourceUrl,modeleSourceUrl,emailGenerique,fiabilite,dernierePreuveActivite,priorite,note

- statutEmail : publie | devine | vide
- companyDomain : domaine nu (sans https ni www)
- country : en anglais (Nigeria, South Africa, Kenya, Ghana, Rwanda, Uganda, Tanzania, Zimbabwe)
- priorite : A (structure au cœur du secteur + dirigeant décisionnaire + modèle observé ou grande structure) | B | C
- note : une phrase utile pour l'accroche (production récente précise) + les réserves (extrait non ouvert, fournisseur mail, 2e source)

Fichier des écartés : colonnes companyName,companyDomain,personne,motif,url.

Pas de commit git. N'écris que dans tes deux fichiers.

## Rapport final (dernier message, en français, court)

Contacts livrés / 6 ; publie / devine / vide ; parmi les devinés, combien avec modèle observé ; nombre d'écartés et motifs principaux ; chemins des deux fichiers.
