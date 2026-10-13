# Consignes : trouver le domaine et deviner l'adresse des contacts suédois sans email

Garry veut une adresse devinée pour chaque contact « sans email » du lot 10. Le blocage venait du domaine : on ne devine jamais sur un domaine non confirmé. Ta tâche est donc d'abord de **trouver le domaine du studio**, puis de deviner.

## Contraintes techniques

- Le proxy bloque l'ouverture des pages (WebFetch, curl : 403). Utilise uniquement WebSearch (ToolSearch, `select:WebSearch`). `allowed_domains` aide à lire un site précis.
- DNS hors service : pas de vérification MX.
- Budget : celui de ta mission (environ 3 recherches par studio). Pas de commit git.

## Méthode, studio par studio

1. **Domaine** : cherche `"<studio>" <ville> game studio` / `"<studio>" official website` / `"<studio>" site:se`, le site du studio sur Steam (« Visit the website »), sa page LinkedIn, Crunchbase, allabolag, Game Habitat, Sweden Game Arena, presskit. Retiens un domaine **seulement s'il apparaît dans un extrait comme site du studio** (URL de l'extrait = `domaineSourceUrl`). Un domaine d'itch.io, Steam, Facebook, Linktree, Gmail, Wix gratuit (`*.wixsite.com`) n'est pas un domaine du studio. Ne construis jamais un domaine par analogie (`nomdustudio.com`) sans l'avoir vu.
2. **Format** : cherche `"@<domaine>"`. Si une adresse nominative apparaît (n'importe quelle personne), c'est le format observé. Si l'adresse exacte de la personne apparaît, statut = `publiée`.
3. **Adresse devinée** :
   - format observé → applique-le ;
   - sinon : `prenom@` si l'équipe compte moins de 10 personnes ou si la taille est inconnue et le studio présenté comme petit ; `prenom.nom@` au-delà de 10 personnes ;
   - plusieurs personnes du même studio : même format pour toutes ;
   - translittération : å→a, ä→a, ö→o, é→e, ü→u ; minuscules ; nom composé → garder le premier nom de famille sans espace (ex. « Högberg Jenelius » → hogberg), et le dire en note ;
   - si la personne n'a qu'un prénom connu, prenom@ seulement.
4. **Pas de domaine trouvé** → `email` vide, `statutEmail` = `sans email`, et une note sur ce que tu as cherché.
5. Si tu tombes sur un fait qui change le dossier (studio fermé, racheté par un groupe, personne partie), écris-le en note : c'est important.

## Format de sortie

CSV UTF-8 (module csv de Python), une ligne par contact de ton fichier d'entrée, colonnes dans cet ordre :

companyName,firstName,lastName,companyDomain,domaineSourceUrl,email,statutEmail,format,note

- statutEmail : `publiée` | `devinée` | `sans email`
- format : « format observé : prenom@ (URL) » ou « aucun format observé, prenom@ par défaut (petite équipe) » ou « aucun format observé, prenom.nom@ par défaut (> 10 personnes) »
- note : une phrase (source du domaine, réserve, signal important)

## Rapport final (dernier message, en français, court)

Domaines trouvés / studios ; adresses devinées / publiées / toujours sans email ; signaux importants (fermeture, rachat, départ) ; chemin du fichier.
