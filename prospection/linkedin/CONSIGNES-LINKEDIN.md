# Consignes : retrouver le profil LinkedIn de chaque contact

## But
Pour chaque personne de ton fichier d'entrée, trouver l'URL de son profil LinkedIn personnel (linkedin.com/in/...) et, si possible, la page LinkedIn de sa structure (linkedin.com/company/...).

## Contraintes techniques
- Le proxy réseau bloque l'ouverture des pages (WebFetch et curl renvoient 403). N'essaie pas de le contourner.
- Utilise uniquement WebSearch (charge-le avec ToolSearch, requête `select:WebSearch`). Budget : environ 40 recherches, soit 2 par personne au plus.
- Requêtes efficaces :
  1. `"Prénom Nom" "Structure" LinkedIn`
  2. si rien : `"Prénom Nom" <poste ou pays> site:linkedin.com/in` (ou le paramètre allowed_domains = ["linkedin.com"] si l'outil le permet)
- Pas de commit git. N'écris que dans ton fichier de sortie, avec le module csv de Python (UTF-8).

## Règles de correspondance (non négociables)
- Tu ne fabriques JAMAIS une URL. Tu ne construis pas `linkedin.com/in/prenom-nom` par analogie. L'URL doit apparaître telle quelle dans un résultat de recherche.
- Retiens un profil seulement si l'extrait du résultat montre le nom de la personne ET un élément qui la relie à la fiche : la structure, le poste, ou le pays et le secteur (cinéma, animation, production).
- Homonymes : si plusieurs profils portent le même nom, prends celui dont l'extrait cite la structure. Sinon, laisse vide et note les candidats.
- Classe chaque ligne dans la colonne `correspondance` :
  - `nom + structure` : l'extrait cite la personne et sa structure (meilleur niveau)
  - `nom + poste ou secteur` : l'extrait cite la personne avec un poste ou un secteur cohérent, sans nommer la structure
  - `introuvable` : aucun profil fiable ; laisse linkedinUrl vide
- Note dans `posteVuSurLinkedIn` le titre affiché dans l'extrait (ex. « CEO at Triggerfish Animation »). C'est utile : si le titre montre que la personne a quitté la structure, écris-le dans la note (signal de contact périmé).

## Format de sortie
Colonnes, dans cet ordre :
firstName,lastName,companyName,email,linkedinUrl,linkedinCompanyUrl,correspondance,posteVuSurLinkedIn,note

- linkedinUrl : URL complète https://www.linkedin.com/in/... (ou sous-domaine pays, ex. za.linkedin.com, garde-la telle quelle)
- note : une phrase (candidats écartés, départ de la structure, doute sur l'homonyme)

## Rapport final (dernier message, en français, court)
Nombre de profils trouvés par niveau de correspondance ; nombre d'introuvables ; signaux de contacts périmés (personne partie de la structure) ; chemin du fichier.
