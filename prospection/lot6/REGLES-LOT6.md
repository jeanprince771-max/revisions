# Règles du lot 6 (master prompt v3) : studios d'animation hors Afrique

## Paramètres de la mission
- SECTEUR CIBLE : studios d'animation (2D, 3D, stop-motion) et studios VFX / motion design indépendants. Cible de la campagne 1 de Garry (lui-même fondateur de studio d'animation) : angle « studio à studio ».
- ZONE GLOBALE : Espagne, Amérique latine, Europe de l'Est, Canada
- LANGUE DES CIBLES : celle du pays (espagnol, portugais, anglais, français, langues d'Europe de l'Est) ; écris la note en français
- POSTES VISÉS, par ordre de priorité : fondateur / CEO / Managing Director / directeur général, puis Executive Producer / Head of Production / Head of Development, puis Head of Business Development / Partnerships
- PROFIL : studio indépendant actif en 2025-2026, environ 5 à 200 personnes, au moins 3 productions (séries, longs, courts primés, prestations pour plateformes ou marques) visibles
- EXCLUSIONS : filiales ou antennes de grands groupes internationaux (Disney, Pixar, DreamWorks, Netflix Animation, Sony Pictures Imageworks, Technicolor / Mikros, Framestore, DNEG, ILM, Cinesite, Xilam, Banijay, Studio 100…), écoles, festivals, freelances seuls. Un seul contact par studio, sauf si un second a un rôle clairement différent (alors priorité B et note « à séquencer »).
- Date du jour : 2026-10-09

## Contraintes techniques de cet environnement (à lire avant les règles)
- Le proxy réseau bloque l'ouverture des pages web : WebFetch et curl renvoient 403 / EGRESS_BLOCKED, y compris dns.google. N'essaie pas de contourner le proxy.
- WebSearch fonctionne (charge-le avec ToolSearch, requête `select:WebSearch`). Budget : environ 50 recherches pour toi. Ne les gaspille pas : une recherche par structure pour la trouver, une ou deux pour la personne, une pour un email publié (`"@domaine"`).
- Comme aucune page ne peut être ouverte, toute personne retenue l'est sur la foi d'extraits de recherche : fiabilite = « a verifier », et tu l'écris dans la note (règle 4.2). Exige au moins deux résultats de recherche indépendants qui citent la personne dans ce rôle, dont un daté de 2025 ou 2026.
- `dig`, `host` et `nslookup` ne sont pas installés, mais le DNS fonctionne en Python. Pour la règle 4.4, utilise :

```
python3 -c "
import dns.resolver,sys
for d in sys.argv[1:]:
    try: print(d, sorted(str(r.exchange) for r in dns.resolver.resolve(d,'MX',lifetime=6)))
    except Exception as e: print(d, 'ECHEC', type(e).__name__)
" domaine1.com domaine2.es
```

- Historique des verdicts Lemlist (cas 1 et 2 de la règle 4.4) : /home/user/revisions/prospection/lot6/historique-verdicts-domaines.csv. Consulte-le pour tout domaine avant de deviner.
- Un domaine sans MX ou inexistant (NXDOMAIN, NoAnswer) : pas de devinette, la personne va dans les écartés ou en email vide.
- Ne devine que sur un domaine dont un résultat de recherche montre qu'il est bien celui de la structure (au lot 4, les domaines non confirmés ont tous échoué). Méthode qui marche : une recherche WebSearch restreinte au domaine candidat (paramètre allowed_domains) ; si elle renvoie des pages du site du studio, le domaine est confirmé. La recherche « @domaine » rend rarement quelque chose.
- Les studios de ces régions ont presque tous un site avec page équipe ou « about » : cherche-la ("<studio>" team / equipo / équipe / zespół) pour trouver le dirigeant, et un éventuel email nominatif publié (contact, press, jobs).
- Pas de commit git. N'écris que dans tes deux fichiers. CSV UTF-8 écrit avec le module csv de Python.

## Règles de recherche (section 4 du master prompt v3, mot pour mot)

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

4.4 — SAVOIR SI LE SERVEUR RÉPOND, AVANT DE DEVINER  (corrigé en v3)

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

Nomme l'hébergeur :

      aspmx.l.google.com, googlemail.com        → Google Workspace
      *.mail.protection.outlook.com             → Microsoft 365
      *.zoho.com, *.zoho.eu                     → Zoho
      mail.<ledomaine>, hébergeur mutualisé,
      cPanel, ou le domaine lui-même            → auto-hébergé
      *.mimecast.com, *.pphosted.com,
      barracuda, proofpoint                     → passerelle de filtrage
      serveur d'opérateur local                 → autre

Ce que tu cherches à savoir n'est pas le nom de l'hébergeur mais une
seule chose : ce serveur donne-t-il une réponse franche quand on lui
demande si une adresse existe ? Un serveur qui répond permet de
deviner, puisqu'on saura si on s'est trompé. Un serveur muet accepte
tout, renvoie « risqué » quel que soit le format, et on ne saura jamais
rien. L'hébergeur n'est qu'un indice de cela, pas la réponse. La v2
disait qu'un serveur auto-hébergé ne répond jamais, et c'était faux :
sur la vague 4, cinq domaines auto-hébergés ont répondu franchement,
dont deux en livrable.

Classe donc le domaine par ordre de preuve décroissante :

   1. Le domaine a DÉJÀ renvoyé « livrable » ou « inexploitable » lors
      d'une vague précédente → il répond. Devine sans hésiter, quel que
      soit son hébergeur. Note-le : verificationUtile = oui (deja
      repondu).

   2. Le domaine a déjà renvoyé « risqué » → il est en catch-all. Ne
      devine pas, et surtout ne reteste pas un autre format : la
      réponse sera la même. verificationUtile = non (catch-all
      constate).

   3. Jamais testé, et hébergé chez Google, Microsoft ou Zoho → il
      répond très probablement. Devine. verificationUtile = oui.

   4. Jamais testé, et auto-hébergé, passerelle ou opérateur local →
      incertain. Propose une seule adresse pour ce domaine, en prenom@,
      et attends le verdict avant d'en proposer d'autres sur la même
      maison. verificationUtile = a determiner.

Dans les cas 2 et 4, deux issues si tu ne veux pas tenter : soit tu
trouves l'email nominatif publié, soit tu laisses la colonne email
vide et la personne part dans le fichier des contacts à chercher au
finder ou sur LinkedIn. Tu renseignes toujours la colonne
hebergeurMail, même quand tu ne devines pas.

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

4.6 — Choix du format, et quand s'arrêter  (corrigé en v3)

En l'absence de preuve de niveau 1 ou 2, prends prenom@domaine, quelle
que soit la taille de la maison. Sur ce marché, prenom@ a donné 33 % de
livrables contre 12 % pour prenom.nom@, y compris dans des structures
de plus de dix personnes (Sea Monster, Luma, Red Pepper). La règle
« prenom.nom@ pour les grandes structures » est fausse ici : ne
l'applique pas, même si un agrégateur l'annonce.

La cascade des relances, mesurée sur onze relances de la vague 4 :

   prenom.nom@ rejeté → relancer en prenom@ : six réussites sur sept.
      C'est la relance qui paie. Mo Abudu, Richard Oboh, Eugene
      Mbugua, Benon Mugumbya, Mathew et Eleanor Nabwiso ont tous été
      retrouvés comme ça.

   prenom@ rejeté sur un serveur qui répond → ARRÊTE. Ne tente pas
      initiale+nom@ : zéro réussite sur quatre essais. Le serveur a dit
      que l'adresse n'existe pas, et la variante n'existe pas non plus.
      La personne part dans le fichier des contacts à chercher au
      finder ou sur LinkedIn.

   réponse « risqué » → ne reteste aucun format, voir 4.4 cas 2.

Garde prenom.nom@ comme premier essai seulement pour les maisons
anciennes et institutionnelles, et uniquement si un indice le soutient.

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

4.8 — Une adresse valide ne ressuscite pas une structure  (nouveau v3)

Quand tu reprends une structure écartée lors d'une vague précédente
pour défaut d'activité récente, tu ne la reclasses pas au seul motif
que son adresse s'est révélée livrable. Une boîte mail peut rester
ouverte des années après l'arrêt de l'activité, et la personne peut
avoir quitté la maison.

Ces lignes partent avec aRequalifier = « oui - activite non confirmee »
et priorite = C, et elles passent en fin de campagne. Pour les faire
remonter, il faut une preuve d'activité postérieure à 2024 et une
confirmation que la personne est toujours en poste : alors seulement tu
mets aRequalifier = non et tu remontes la priorité.

Sur la vague 4, onze livrables sur dix-sept venaient de cette pile. Le
volume était flatteur et la moitié de ce volume n'était pas qualifiée.

## Format de sortie (section 5 du master prompt v3)

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
   aRequalifier           non | oui - activite non confirmee  (cf. 4.8)
   verificationUtile      oui (deja repondu) | oui | non (catch-all
                          constate) | a determiner   (cf. les quatre cas
                          de la section 4.4)
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

En-tête exacte (22 colonnes) :
firstName,lastName,email,companyName,companyDomain,jobTitle,country,zone,statutEmail,hebergeurMail,aRequalifier,verificationUtile,niveauPreuve,formatEmail,personSourceUrl,emailSourceUrl,modeleSourceUrl,emailGenerique,fiabilite,dernierePreuveActivite,priorite,note

country en anglais (Spain, Mexico, Colombia, Argentina, Brazil, Poland, Romania, Canada…). Quand l'email est vide, laisse formatEmail vide.

Fichier des écartés : colonnes companyName,companyDomain,personne,motif,url.

## Rapport final (ton dernier message, en français, court)
Contacts livrés / quota ; publie / devine / vide ; répartition par verificationUtile ; répartition par niveau de preuve ; nombre d'adresses devinées sur catch-all constaté (doit être 0) ; nombre d'écartés et motifs principaux ; si quota non atteint, deux lignes sur ce qui bloquait ; chemins des deux fichiers.
