# Règles du lot 9 (master prompt v6, pays lusophones)

## Master prompt v6 (mot pour mot)

MASTER PROMPT v6 — Studios d'animation et hybrides animation/jeu vidéo, pays lusophones

Objectif
Trouver des studios d'animation (et des studios hybrides animation + jeu vidéo) dans les pays lusophones, avec des contacts nominatifs et des adresses vérifiées. Ce prompt reprend les règles de la v5 (pays hispanophones) et les adapte au portugais.

Pays cibles (20 contacts par pays, sauf indication contraire de Garry)
1. Brésil
2. Portugal
3. Angola
4. Moçambique
5. Cabo Verde
Si Garry ne veut que le Brésil et le Portugal, ne traiter que ces deux pays.

Périmètre
- Studios d'animation 2D, 3D, stop-motion, motion design narratif, séries et courts.
- Studios hybrides animation + jeu vidéo : inclus. Un studio qui fait les deux est une cible.
- Petites structures : 2 à 50 personnes. Exclure les grands groupes et les filiales de studios internationaux.
- Exclure : agences de publicité qui font de la pub animée sans production propre, écoles, festivals, plateformes.
- Un studio doit avoir une activité prouvée sur 2025-2026. Une preuve datée de plus de 2 ans = cas limite, à marquer C.

Contacts
- Nominatif obligatoire : prénom + nom + fonction.
- Fonctions visées : fondateur, co-fondateur, CEO, diretor, sócio, produtor executivo, head of production, business development.
- Pas de contact générique (info@, contato@) en contact principal. Le générique peut être noté dans une colonne à part.

Adresses email
Ordre de priorité :
A. Adresse publiée par le studio, la fiche festival, le marché (MIFA, Annecy, Cartoon, Animamundi, Festival Anima, Ancine, Portugal Film Commission, etc.).
B. Adresse publiée sur un domaine du studio, sans preuve de la personne.
C. Adresse devinée à partir d'un format observé sur le domaine (prenom@, prenom.nom@, initiale+nom@).

RÈGLE BLOQUANTE (héritée de la v5)
Une adresse devinée (C) n'entre dans le fichier d'import que si son domaine a déjà répondu. Sinon, elle va dans contacts-serveur-muet.csv, sans import.

Vérification
- Vérifier le MX du domaine avant d'accepter toute adresse. Si le DNS ne répond pas, le noter : la vérification restera à faire dans Lemlist.
- Ne jamais inventer un domaine. Si le domaine du studio n'est pas confirmé, ne pas deviner.
- Une même adresse ne doit apparaître qu'une fois dans l'ensemble des fichiers.
- Un seul contact par studio dans le fichier d'import principal. Les autres contacts du même studio vont dans un fichier à part, à envoyer plus tard.

Icebreaker (obligatoire pour chaque contact)
- Un fait précis et daté, sourcé : festival, prix, série, coproduction, client public, sortie récente.
- Colonne icebreaker : une phrase en portugais (ou en anglais pour Cabo Verde si le studio publie en anglais).
- Colonne icebreakerSourceUrl : l'URL de la source. Sans URL, pas de fait sourcé.
- Si aucun fait sourcé n'existe, utiliser la phrase de repli, en la marquant icebreakerType = phrase de repli :
  PT : "Estou a contactar alguns estúdios de animação no {pays}, e {studio} é um deles."
  EN (Cabo Verde) : "I am reaching out to a handful of animation studios in {pays}, and {studio} is one of them."

Format de sortie
Un fichier CSV par pays, nommé pays-lot-animation-jeu.csv, avec les colonnes :
email, firstName, lastName, companyName, jobTitle, linkedinUrl, secteur, icebreaker, icebreakerSourceUrl, icebreakerType, senderName, pays, langue, priorite, hybrideJeu, statutEmail, verificationMX, note

- secteur : "estúdio de animação" (pour le portugais)
- senderName : "Garry Yankson"
- pays : nom en français (Brésil, Portugal, Angola, Moçambique, Cabo Verde)
- langue : portugais (ou anglais pour Cabo Verde)
- priorite : A, B ou C
- hybrideJeu : non | oui - animation dominante | oui - jeu dominant
- statutEmail : publiée | devinée | sans email
- verificationMX : OK | non vérifié (DNS) | échec

Fichiers de sortie supplémentaires
- contacts-serveur-muet.csv : adresses devinées dont le domaine n'a pas répondu, sans import.
- contacts-sans-email.csv : contacts trouvés sans adresse.
- rapport.md : nombre de contacts par pays et par priorité, nombre de hybrides, nombre de cas limites, liste des domaines non vérifiés.

Ce qu'il faut éviter
- Ne pas mettre de variables Lemlist vides : icebreaker, firstName, companyName, senderName doivent être remplis pour chaque ligne.
- Pas de variable {{secteur}} dans les textes espagnols ou portugais avec une valeur en français.
- Pas de "Re:" en fausse réponse, pas de "Hey".
- Pas de doublon d'adresse entre les pays.

Rapport final
Donner à Garry, en français : le nombre de contacts par pays, le nombre de cas hybrides, les cas limites, et ce qui reste à vérifier dans Lemlist.


## Contraintes techniques de cet environnement (à lire avant de commencer)
- Le proxy réseau bloque l'ouverture des pages (WebFetch et curl renvoient 403). N'essaie pas de le contourner.
- WebSearch fonctionne (charge-le avec ToolSearch, requête `select:WebSearch`). Il accepte allowed_domains : une recherche restreinte au site d'un studio renvoie les extraits de ses pages (equipe, sobre, contato), c'est ta façon de « lire » une page. Budget : environ 60 recherches.
- Toute personne retenue l'est sur la foi d'extraits de recherche : écris-le dans la note. Exige deux résultats indépendants qui citent la personne dans ce rôle, dont un daté de 2025 ou 2026 ; ou un seul si c'est la page equipe / sobre du site du studio lui-même.
- DNS HORS SERVICE (vérifié le 13 octobre) : dnspython, la résolution système et les résolveurs DNS en HTTPS échouent tous. Ne perds pas de recherches dessus. verificationMX = « non vérifié (DNS) » sur toutes les lignes. Conséquence de la règle bloquante : toutes les adresses devinées iront dans contacts-serveur-muet.csv (l'orchestrateur s'en charge) ; produis-les quand même dans ton fichier pays avec statutEmail = devinée, une seule adresse devinée par domaine sauf format observé sur ce domaine (prenom@ par défaut).
- Ne jamais deviner sur un domaine qui n'est pas confirmé par un extrait du site du studio lui-même.
- Exclusions : /home/user/revisions/prospection/lot9/exclusions.txt (studios brésiliens déjà contactés ou écartés aux lots 7 et 8, et structures africaines déjà traitées aux lots 1 à 5). Ne reprends pas un studio « DEJA CONTACTE ». Un studio « DEJA ECARTE » seulement avec la preuve qui manquait, signalée dans la note.
- linkedinUrl : seulement si l'URL apparaît telle quelle dans un résultat de recherche. Jamais construite.
- Pas de commit git. N'écris que dans tes fichiers. CSV UTF-8 écrit avec le module csv de Python, séparateur virgule.

## Fichiers à produire par chaque agent
1. Le fichier pays, avec exactement ces 18 colonnes dans cet ordre :
   email,firstName,lastName,companyName,jobTitle,linkedinUrl,secteur,icebreaker,icebreakerSourceUrl,icebreakerType,senderName,pays,langue,priorite,hybrideJeu,statutEmail,verificationMX,note
   - icebreakerType : « fait sourcé » ou « phrase de repli »
   - Ajoute dans la note : companyDomain=<domaine> au début, puis « 1er contact » ou « 2e contact (à envoyer plus tard) » si le studio a plusieurs contacts.
2. agent-NN-ecartes.csv : companyName,companyDomain,personne,motif,url

## Rapport final (ton dernier message, en français, court)
Contacts livrés / 20 ; publiées / devinées / sans email ; icebreakers sourcés vs phrases de repli ; hybrides ; cas limites (C) ; domaines non vérifiés ; écartés et motifs ; si moins de 20, où le gisement s'est tari ; chemins des fichiers.
