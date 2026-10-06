# Règles du lot 3 (master prompt v2)

## Paramètres de la mission
- SECTEUR CIBLE : production audiovisuelle, studios d'animation et maisons de production indépendantes
- ZONE GLOBALE : Afrique anglophone (Nigeria, Ghana, Kenya, Afrique du Sud, Rwanda, Ouganda, Tanzanie, Zimbabwe)
- LANGUE DES CIBLES : anglophone
- POSTES VISÉS, par ordre de priorité : CEO / Managing Director (ou fondateur dirigeant), puis Head of Content ou Head of Production, puis Head of Partnerships
- PROFIL : structures avec site actif et preuve d'activité en 2025-2026, au moins 3 productions ou clients visibles
- EXCLUSIONS : toute structure listée dans /home/user/revisions/prospection/lot3/exclusions-deja-vues.txt (déjà traitée aux lots 1 et 2 ; compare aussi les noms approchants), filiales de grands groupes internationaux (Netflix, Disney, Showmax/MultiChoice, Skydance…), structures hors Afrique
- Date du jour : 2026-10-06

## Contraintes techniques de cet environnement (à lire avant les règles)
- Le proxy réseau bloque l'ouverture des pages web : WebFetch et curl renvoient 403 / EGRESS_BLOCKED, y compris dns.google. N'essaie pas de contourner le proxy.
- WebSearch fonctionne (charge-le avec ToolSearch, requête `select:WebSearch`). Comme aucune page ne peut être ouverte, toute personne retenue l'est sur la foi d'extraits de recherche : fiabilite = « a verifier », et tu l'écris dans la note (règle 4.2). Exige au moins deux résultats de recherche indépendants qui citent la personne dans ce rôle, dont un daté de 2025 ou 2026.
- `dig`, `host` et `nslookup` ne sont pas installés, mais le DNS fonctionne en Python. Pour la règle 4.4, utilise :

```
python3 -c "
import dns.resolver,sys
for d in sys.argv[1:]:
    try: print(d, sorted(str(r.exchange) for r in dns.resolver.resolve(d,'MX',lifetime=6)))
    except Exception as e: print(d, 'ECHEC', type(e).__name__)
" domaine1.com domaine2.co.za
```

  Un domaine sans MX ou inexistant (NXDOMAIN, NoAnswer) part dans les écartés (motif « aucun serveur mail »).
- Pas de commit git. N'écris que dans tes deux fichiers. CSV UTF-8 écrit avec le module csv de Python.

## Règles de recherche (section 4 du master prompt v2, mot pour mot)

4.1 — Trouver l'entreprise

Pars de recherches web réelles, pas de ta mémoire. Une entreprise
n'entre dans la liste que si tu as ouvert son site et constaté qu'il
est vivant : contenu récent, pages qui répondent, pas de domaine parqué
ni de site détourné. Si le domaine redirige vers une page de vente de
nom de domaine, un casino, un blog générique ou une erreur,
l'entreprise part dans le fichier des écartés avec le motif.

Note la date de la preuve d'activité la plus récente que tu as vue. Si
tu ne trouves aucune trace postérieure à 2024, classe la structure en
fiabilité « à vérifier » et dis pourquoi.

4.2 — Trouver la personne

Le nom et le poste doivent venir d'une page que tu as réellement
ouverte : page équipe, page direction, communiqué, article nommant la
personne dans ce rôle, profil LinkedIn public. Tu enregistres l'URL
exacte dans personSourceUrl.

Interdictions, sans exception :
   - inventer un nom plausible parce que le poste existe forcément ;
   - déduire un nom à partir d'une adresse générique ;
   - citer une page que tu n'as pas pu ouvrir.

Si tu n'as pu lire la page que via un résumé de recherche, écris-le
dans la note et mets fiabilite = « a verifier ». Une adresse peut être
livrable alors que le poste est faux : la vérification Lemlist teste la
boîte, pas la fonction.

4.3 — L'email publié

Cherche d'abord l'email nominatif réellement publié. Les endroits qui
marchent : page contact, page équipe, mentions légales, bas de
communiqué, PDF de rapport annuel, page presse, signature dans un
article, fiche d'intervenant sur un site de conférence.

4.4 — VÉRIFIER L'HÉBERGEUR MAIL AVANT DE DEVINER  (nouveau)

Avant de proposer une adresse devinée, relève l'enregistrement MX du
domaine, par exemple :

      dig +short MX exemple.com
      (ou : host -t MX exemple.com / nslookup -type=mx exemple.com)

Si ces commandes ne sont pas installées, ou si le DNS sortant est
bloqué, passe par un résolveur public en HTTPS :

      https://dns.google/resolve?name=exemple.com&type=MX

Lis la valeur du champ « data » des entrées de type 15 du tableau
« Answer ». Ne confonds pas avec le champ « name », qui répète
simplement le domaine interrogé : une lecture trop rapide fait croire
que le domaine pointe sur lui-même alors qu'il est chez Google. Et
quand « data » vaut bien le domaine lui-même, par exemple
« 0 exemple.com. », c'est un serveur auto-hébergé.

Si tu n'arrives à relever le MX par aucun de ces moyens, écris
hebergeurMail = inconnu et verificationUtile = a determiner, et ne
prétends pas avoir fait le contrôle.

Classe le résultat :

   RÉPOND CLAIREMENT
      aspmx.l.google.com, googlemail.com        → Google Workspace
      *.mail.protection.outlook.com             → Microsoft 365
      *.zoho.com, *.zoho.eu                     → Zoho

   NE RÉPOND PAS
      mail.<ledomaine>, serveur d'hébergeur
      mutualisé, cPanel                         → auto-hébergé
      *.mimecast.com, *.pphosted.com,
      barracuda, proofpoint                     → passerelle de filtrage
      serveur d'opérateur local                 → autre

Règle de décision :

   Hébergeur qui répond clairement → tu peux deviner. Le serveur
   refuse les destinataires inconnus, donc la vérification donnera un
   verdict net : l'adresse existe ou elle n'existe pas.

   Hébergeur qui ne répond pas → ne devine pas pour remplir une case.
   Ces serveurs acceptent toutes les adresses, donc la vérification
   renverra « risqué » quel que soit le format essayé, et personne ne
   saura si l'adresse est bonne. Dans ce cas, deux issues seulement :
   soit tu trouves l'email nominatif publié, soit tu laisses la colonne
   email vide et la personne part dans le fichier des contacts à
   chercher au finder ou sur LinkedIn. Tu renseignes quand même
   l'hébergeur dans la colonne hebergeurMail.

4.5 — Hiérarchie des preuves de modèle

Quand tu devines, dis sur quoi tu t'appuies, en reprenant exactement un
de ces quatre niveaux dans la colonne niveauPreuve :

   1. « adresse complete observee » — une autre personne de la même
      maison a son adresse nominative publiée, et tu copies son URL
      dans modeleSourceUrl. C'est le meilleur niveau.

   2. « indice masque coherent » — un agrégateur (ZoomInfo,
      RocketReach) affiche une adresse tronquée du type c***@domaine ou
      h******@domaine, et l'initiale plus la longueur collent avec le
      prénom de la personne. Compte les caractères et écris ton calcul
      dans la note. Sur les vagues précédentes, cet indice a donné le
      bon format cinq fois sur cinq.

   3. « format annonce par un agregateur » — l'agrégateur dit
      « first@ » ou « first.last@ » sans montrer d'adresse. Indice
      faible.

   4. « aucun modele observe » — rien. Tu n'écris jamais « format
      confirmé », « modèle prouvé » ou « pattern vérifié » à ce niveau.
      Point non négociable : une vague antérieure annonçait 36 adresses
      « confirmées » et a donné 0 livrable, parce que les preuves
      étaient circulaires ou génériques.

4.6 — Choix du format par défaut

En l'absence de preuve de niveau 1 ou 2, prends prenom@domaine.
Sur ce marché, prenom@ a donné 33 % de livrables contre 12 % pour
prenom.nom@, y compris dans des maisons de plus de dix personnes
(Sea Monster, Luma, Red Pepper). La règle « prenom.nom@ pour les
grandes structures » est fausse ici : ne l'applique pas.

Garde prenom.nom@ pour les maisons anciennes et institutionnelles, et
signale initiale+nom@ comme variante à tester quand prenom@ échoue :
cette variante a récupéré quatre livrables sur des domaines où
prenom.nom@ était rejeté.

L'email générique de la structure (info@, contact@, hello@) va dans sa
propre colonne. Il ne remplace pas un contact nominatif et ne compte
pas dans le quota.

4.7 — Le quota

Tu livres le nombre demandé si le réel le permet. Si ton lot est
pauvre, tu livres moins et tu expliques en deux lignes ce que tu as
cherché et ce qui bloquait (robots.txt, 403, 404, pas de page équipe,
secteur peu digitalisé). Tu ne descends pas d'un cran sur la qualité
des sources pour atteindre le chiffre. Une case email vide avec un nom
solide vaut mieux qu'une adresse inventée sur un serveur catch-all.

## Format de sortie (section 5 du master prompt v2)

Chaque agent produit un CSV avec exactement ces colonnes, dans cet
ordre. Les quatre premières sont celles qu'attend Lemlist.

   firstName
   lastName
   email                  (publié, deviné, ou vide)
   companyName
   companyDomain
   jobTitle
   country
   zone                   (le lot de l'agent)
   statutEmail            publie | devine | vide
   hebergeurMail          Google Workspace | Microsoft 365 | Zoho |
                          auto-heberge | passerelle | autre | inconnu
   verificationUtile      oui | non   (oui pour les trois premiers)
   niveauPreuve           un des quatre libellés de la section 4.5
   formatEmail            prenom@ | prenom.nom@ | initiale+nom@ | autre
   personSourceUrl
   emailSourceUrl         (si publié)
   modeleSourceUrl        (si preuve de niveau 1)
   emailGenerique
   fiabilite              solide | a verifier
   dernierePreuveActivite
   priorite               A | B | C
   note                   une phrase d'accroche utile, ou la réserve
                          sur la source, ou le calcul de l'indice masqué

Priorité : A pour une structure dont l'activité correspond directement
au secteur visé avec un contact au bon niveau de décision ; B pour une
structure pertinente mais plus éloignée ou un contact moins
décisionnaire ; C pour un cas limite que je trancherai.

Chaque agent produit aussi agent-NN-ecartes.csv avec les structures ou
personnes rejetées et le motif en clair.

En-tête exacte (21 colonnes) :
firstName,lastName,email,companyName,companyDomain,jobTitle,country,zone,statutEmail,hebergeurMail,verificationUtile,niveauPreuve,formatEmail,personSourceUrl,emailSourceUrl,modeleSourceUrl,emailGenerique,fiabilite,dernierePreuveActivite,priorite,note

country en anglais (Nigeria, South Africa, Kenya, Ghana, Rwanda, Uganda, Tanzania, Zimbabwe). Quand l'email est vide, laisse formatEmail vide.

Fichier des écartés : colonnes companyName,companyDomain,personne,motif,url.

## Rapport final (ton dernier message, en français, court)
Contacts livrés / quota ; publie / devine / vide ; répartition par hébergeur mail ; répartition par niveau de preuve ; nombre d'adresses devinées sur serveur muet (doit être 0) ; nombre d'écartés et motifs principaux ; si quota non atteint, deux lignes sur ce qui bloquait ; chemins des deux fichiers.
