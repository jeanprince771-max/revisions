# Règles du lot 11 : Royaume-Uni, 4 segments (master prompt v9)

Le brief complet est dans `/home/user/revisions/prospection/lot11/master-prompt-v9.txt`. Lis-le en entier : il fait foi. Ce fichier ajoute les contraintes techniques, la façon de scorer et le format exact.

## Contraintes techniques

- Le proxy réseau bloque l'ouverture des pages (WebFetch et curl : 403). N'essaie pas de le contourner. Utilise uniquement WebSearch (ToolSearch, `select:WebSearch`). `allowed_domains` permet de lire les extraits d'un site précis (ex. `["find-and-update.company-information.service.gov.uk"]` pour Companies House, `["animationuk.org"]`, `["linkedin.com"]`).
- **Liens** : on ne peut pas ouvrir les pages. Un lien n'est livré que s'il apparaît **tel quel dans un résultat de recherche** (c'est notre « vérification »). Ne construis jamais une URL. Écris dans la note « liens vus en résultat de recherche, non ouverts ».
- **DNS hors service** : pas de vérification MX. `verificationMX` = « non vérifié (DNS) » partout.
- Budget : celui de ta mission. Plusieurs agents partagent le même plafond de recherches : ne le dépasse pas.
- Pas de commit git. N'écris que dans tes deux fichiers de sortie, avec le module csv de Python (UTF-8).
- Ne touche pas à Lemlist ni à HubSpot.

## Règles non négociables

1. **N'invente jamais** un nom, un poste, un domaine, un fait, une taille ou une forme juridique. Une personne est retenue si un extrait la cite dans son rôle actuel (idéalement 2 sources, dont une de 2025-2026). Sinon dis-le en note.
2. **Forme juridique (règle UK)** : cherche la société sur Companies House (`"<nom>" site:find-and-update.company-information.service.gov.uk` ou `"<nom>" "company number"`). Note `Ltd`, `PLC`, `LLP`, `CIC`, `association incorporée` (CIO, company limited by guarantee…). **Sole trader ou partenariat non incorporé → écarté.** Si Companies House ne remonte rien : `formeJuridique` = « non trouvée » et la ligne passe en HOLD (pas d'import possible sans forme juridique confirmée).
3. **Taille** (LinkedIn « X employees », site, Companies House) : segment A strictement < 30 personnes (sinon écarté) ; segment B 10 à 500. Taille introuvable → « non trouvée », priorité C.
4. **Actionnariat** : vérifie qu'aucun groupe exclu ne détient la société (voir brief et `exclusions.txt`).
5. **Activité ou édition 2025-2026** (C : prochaine édition 2026 ou 2027 annoncée ; D : promotion ou appel 2025-2027). Sinon C / HOLD selon le brief.
6. **Contacts nominatifs** (fonctions du brief selon le segment). Pas de générique en contact principal ; un générique publié se note dans `note`.
7. **Emails** :
   - `publiée` : l'adresse exacte de la personne apparaît dans un extrait (site, fiche festival, programme, presse). URL en note.
   - `devinée` : uniquement si le domaine de la société est confirmé par un extrait. Cherche d'abord un format observé (`"@domaine.co.uk"`). Format observé → applique-le ; sinon prenom@ (< 10 personnes) ou prenom.nom@ (≥ 10 personnes). **Une seule adresse devinée par domaine** ; les autres personnes de la même société : `sans email`, sauf adresse publiée.
   - `sans email` : domaine non confirmé, ou contact supplémentaire.
   - Garry veut des adresses : quand le domaine est confirmé, devine toujours l'adresse du 1er contact.
8. **Un 1er contact par société**, au plus 2 contacts supplémentaires notés « 2e contact (à envoyer plus tard) ».
9. **companyName propre** : un seul nom, sans virgule, sans « Ltd », tel qu'il apparaîtrait dans un objet de mail (ex. `Blue Zoo`, pas `Blue-Zoo Productions Ltd,`). La raison sociale complète va dans `note`.
10. Pas de valeur en français dans `secteur`, `icebreaker`, `firstName`, `companyName`, `eventName`, `jobTitle`, `ville`.

## FACT / SIGNAL et icebreaker

- `factSignal` : `FACT : <fait daté> (URL)` ou `SIGNAL : <indice daté> (URL)`. Une HYPOTHESIS (déduction sans source) ne sert jamais d'icebreaker ; tu peux l'ajouter en note.
- `icebreaker` : une phrase anglaise, sobre, fondée sur le FACT ou le SIGNAL, URL dans `icebreakerSourceUrl`, `icebreakerType` = `fait sourcé`. Sans fait sourcé : phrase de repli exacte du brief pour le segment, `icebreakerType` = `phrase de repli`.

## Score (sur 100) et décision

Note chaque critère, puis additionne. Détaille les 6 notes dans `note` (ex. `score: ICP 22/25, besoin 14/20, déclencheur 15/20, valeur 10/15, accès 8/10, stratégique 6/10`).
- ICP (25) : correspondance exacte au segment (taille, indépendance, activité, forme juridique).
- Besoin (20) : signes d'un besoin d'ouverture internationale, de partenariats, de financement, de business development.
- Déclencheur (20) : fait récent (6 derniers mois = maximum) qui justifie d'écrire maintenant.
- Valeur commerciale (15) : taille du compte, capacité à payer, volume d'affaires possible.
- Accès au décideur (10) : 10 = décideur nommé avec adresse publiée ; 6-8 = décideur nommé + adresse devinée ; 3-5 = sans adresse.
- Valeur stratégique (10) : effet de réseau, référence, visibilité.
Décision : ≥ 80 PRIORITY ; 65-79 COLD_OK ; 50-64 HOLD ; < 50 EXCLUDE. Ne gonfle pas les notes pour atteindre le quota. Un EXCLUDE va dans le fichier des écartés avec la raison, pas dans le fichier principal.

## Format de sortie

Fichier principal (nom indiqué dans ta mission), 29 colonnes dans cet ordre :

email,firstName,lastName,companyName,eventName,jobTitle,linkedinUrl,segment,secteur,typeStudio,icebreaker,icebreakerSourceUrl,icebreakerType,factSignal,score,decision,senderName,pays,nation,ville,langue,priorite,tailleEquipe,formeJuridique,actionnariat,prochaineEdition,statutEmail,verificationMX,note

- segment : A, B, C ou D ; secteur en anglais (« animation studio », « media group », « film festival », « games conference », « creative accelerator », « creative incubator »…)
- typeStudio : `animation` | `hybride animation-jeu` | `services` (segment A seulement, vide sinon)
- eventName : nom de l'événement (segment C, obligatoire) ; vide sinon
- senderName `Garry Yankson` ; pays `Royaume-Uni` ; nation `Angleterre` | `Écosse` | `pays de Galles` | `Irlande du Nord` ; langue `anglais`
- priorite : A (adresse publiée ou domaine confirmé + décideur confirmé par 2 sources + activité récente) | B | C (cas limite)
- score : nombre entier ; decision : PRIORITY | COLD_OK | HOLD
- prochaineEdition : date ou année (C et D), vide sinon
- statutEmail : `publiée` | `devinée` | `sans email` ; verificationMX `non vérifié (DNS)`
- linkedinUrl : seulement une URL vue telle quelle dans un résultat, sinon vide
- note : commence par `companyDomain=<domaine ou (non confirmé)> ; 1er contact.` ou `... ; 2e contact (à envoyer plus tard).` ; si la ligne dépasse ton quota : `... ; 1er contact ; réserve.` Puis : raison sociale et numéro Companies House, détail du score, sources, format email, générique publié, réserves.

Fichier des écartés `agent-XX-ecartes.csv` : colonnes `companyName,companyDomain,personne,motif,url`. Motifs : « taille ≥ 30 » / « taille hors 10-500 », « actionnariat : détenu par X », « forme juridique : sole trader / partenariat », « pas d'activité / d'édition 2025-2027 », « aucun dirigeant nommé », « déjà dans Lemlist », « hors périmètre », « EXCLUDE score X : raison ».

## Rapport final (dernier message, en français, court)

Contacts livrés / quota (1ers contacts, 2es contacts, réserve) ; PRIORITY / COLD_OK / HOLD ; publiées / devinées / sans email ; formes juridiques non trouvées ; écartés par motif ; chemins des deux fichiers.
