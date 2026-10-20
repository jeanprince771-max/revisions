# Lot 13 (master prompt v12) : Royaume-Uni, studios d'animation et de jeu vidéo indépendants

Lot livré pour validation par Garry. Rien n'a été importé ni lancé dans Lemlist. Lemlist et HubSpot ont seulement été consultés, en lecture.

## Résultat : 16 sociétés, objectif de 25 non atteint

Le lot compte 16 sociétés, une personne par société. **4 sont en COLD_OK, 12 en HOLD, aucune en PRIORITY. Seules 2 sont importables tout de suite.**

| Société | Ville | Contact | Score | Décision | Adresse |
|---|---|---|---|---|---|
| Team FOLON | Brighton | Dean Carter | 78 | COLD_OK | format inconnu (générique business@teamfolon.com) |
| Saltstone Studios | Belfast | Jessica Campbell | 78 | COLD_OK | jess@saltstonestudios.com (A) |
| inkle | Cambridge | Jon Ingold | 68 | COLD_OK | format inconnu (générique info@inklestudios.com) |
| Pocket Sized Hands | Dundee | Alan Yeats | 67 | COLD_OK | alan@pocketsizedhands.com (A, communiqué de 2023) |
| 12 autres sociétés | | | 50 à 70 | HOLD | voir `hold.csv` |

**Pourquoi 16 et pas 25.** Six agents ont travaillé, soit environ 300 recherches.
- **L'animation britannique était déjà épuisée par le lot 11.** Il en reste 2 studios, et un hybride : la plupart des studios restants sont rachetés, en liquidation, trop petits ou sans actualité.
- **Le jeu vidéo compense, comme prévu par le brief :** 13 studios sur 16.
- **Le vrai frein est l'adresse.** La règle v12 interdit de deviner sans format observé, et les extraits de recherche masquent presque toujours les adresses des fondateurs. Une page dédiée à la recherche d'adresses n'en a trouvé aucune de plus.
- **Aucune ligne n'a été forcée.**

## Répartition

- **Par secteur :** 13 jeu vidéo, 2 animation (Engine House, Educational Voice), 1 hybride (Goldborough Studio).
- **Par palier :**

| Palier | Sociétés |
|---|---|
| 1. Animation | 2 |
| 2. Hybride | 1 |
| 3. Jeu vidéo | 13 |
| 4 et 5 | 0 |

## Déclencheurs : l'indicateur de qualité

| Type | Sociétés |
|---|---|
| FACT fort | 12 |
| FACT moyen | 3 |
| SIGNAL | 1 |
| Phrase de repli | 1 (Engine House) |

- **Âge moyen :** environ 4 mois (date de référence : 20/10/2026).
- **Déclencheurs de plus de 6 mois (3) :** Educational Voice (2026-02), Second Star Games et Goldborough (2026-01, Ukie Video Games Growth Programme).
- **Déclencheurs à 6 mois juste :** inkle et Pocket Sized Hands (2026-04).
- **Sources principales :**
  - UK Games Fund : Prototype Fund de juillet 2026 et round 20 de septembre 2026 ;
  - aide BFI International Business Development ;
  - MCV/Develop Awards ;
  - révélations sur Steam.

## Adresses

| Qualité | Lignes (sur 22, seconds contacts compris) |
|---|---|
| A (publiée) | 5 : Saltstone (jess@), Pocket Sized Hands (alan@), Engine House (mike@, jason@, tash@) |
| B | 0 |
| C1 | 0 |
| C2 (reconstruite) | 1 : thomas@saltstonestudios.com, 2e contact |
| Sans email (format inconnu) | 16 |

- **Seul motif observé : prenom@**, vu sur 6 adresses et 3 domaines (saltstonestudios.com, pocketsizedhands.com, engine-house.co.uk). Chez Engine House, ce sont même des diminutifs (mike@, tash@). C'est cohérent avec le lot Irlande, où prenom@ est passé 4 fois sur 4 dans Lemlist.
- **Format inconnu, PRIORITY ou COLD_OK :** 2 lignes dans `contacts-format-inconnu.csv` (Team FOLON, inkle). Les 12 sociétés en HOLD sans adresse sont dans `hold.csv`.
- **Reconstruites, donc bloquées tant que le MX n'est pas vérifié :** 1 ligne dans `contacts-serveur-muet.csv`.
- **MX :** le DNS de l'environnement est hors service, donc `verificationMX` vaut « non vérifié (DNS) » partout. Les 2 adresses importables sont des adresses publiées.
- **Génériques relevés :**
  - business@teamfolon.com
  - info@inklestudios.com et pr@inklestudios.com
  - contact@nyamyam.com
  - info@bitloomgames.com
  - info@educationalvoice.co.uk
  - studio@goldboroughstudio.com
  Ils peuvent servir à demander le bon interlocuteur.

## Effectifs

| Tranche | Sociétés |
|---|---|
| 1-4 | 3 : Saltstone 4, Bit Loom 4, Exabyte 3. Retenues pour IP propre et jeu sorti. |
| 5-9 | 1 : Engine House 6 |
| 10-29 | 2 : Pocket Sized Hands 16, Second Star Games 18 |
| Non trouvée | 10 |

**Écartés pour taille ≥ 30 :**
- Team Junkfish : 37 (LinkedIn)
- Hyper Luminal Games : 85
- Outplay Entertainment : plus de 30, « le plus grand studio indépendant d'Écosse »
- Dlala Studios : 40 (LinkedIn)
- Halon Entertainment : jusqu'à 250 emplois annoncés
- Factory : plus de 40 emplois annoncés
- Fireslug Studios : 21 à 50, source tierce

## Écartés pour actionnariat ou éditeur

| Société | Propriétaire ou raison |
|---|---|
| Zaratan (Glasgow) | Aniventure, majoritaire depuis 09/2025 |
| Emanata Studios (Dundee) | DC Thomson / Beano |
| Stirling Animation Studio | Magic Light Pictures |
| Halon Entertainment | groupe américain |
| Stormcloud Games | 4J Studios |
| Wheel In Motion | coentreprise avec Superprod Group (France) |
| Pretty Cool Games | financé par Coreblazer (Hypergryph), EXCLUDE |
| Screen Burn Interactive | jeux faits pour Konami et Devolver, pas d'IP propre |
| Draknek & Friends, Chucklefish | aussi éditeurs, besoin couvert |

**Contre-signaux sur les sociétés retenues :**
- Friday Sundae recrute un international marketing manager (structure partielle, Besoin à 12).
- Pocket Sized Hands fait surtout du co-développement.
- Bit Loom (*PHOGS!*) et Kaizen Game Works ont publié chez des éditeurs tiers, mais pas d'éditeur exclusif.
- Second Star Games et Evil Twin Artworks travaillent sur des IP sous licence.
- Goldborough a surtout une activité de services.

Chacun est noté dans `contreSignal`, avec le score Besoin ajusté.

## Doublons et exclusions

- Les 215 sociétés du lot 11 et le lot Irlande ont été exclus **avant** toute recherche. 7 doublons du lot 11 ont été rencontrés et écartés : Paper Owl, Sixteen South, Bumpybox, Axis, Red Kite, Sun & Moon, Wyndley Animation (liée aux Brothers McLeod).
- Outlier Games (lot 12, République d'Irlande) a aussi été écarté.
- **Lemlist (par nom) et HubSpot (par domaine et par nom) :** aucune des 16 sociétés n'y figure.

## Concentration géographique

| Nation | Sociétés | Villes |
|---|---|---|
| Angleterre | 10 | Brighton 2, Bristol 2, Cambridge, Redruth, Broadstairs, Manchester, Swindon, Sheffield |
| Écosse | 2 | Dundee |
| Irlande du Nord | 2 | Belfast |
| Pays de Galles | 2 | Pontypridd, Lawrenny |

## Cas limites

- **Statut « active » à confirmer :** Friday Sundae et Second Star Games.
- **Rubrique PSC non lue :** pour la plupart des sociétés, faute de pouvoir ouvrir Companies House. « Indépendant » veut dire « aucun groupe vu ».
- **Meaning Machine :** une société sœur, Meaning Machine Games Ltd (16142915), a les mêmes directeurs. Il faut vérifier laquelle porte la subvention du UK Games Fund.
- **Deceptive Games :** domaine probable deceptive-games.co.uk (et non .com).
- **Saltstone :** jess@ est publiée comme contact pour le blog et les réseaux sociaux, pas explicitement comme adresse de direction.
- **Pocket Sized Hands :** adresse de 2023, à reconfirmer.
- **Nihil Declarandum** (stop-motion, long métrage *Heads*) n'est pas retenu : société très probablement américaine.

**Pistes non traitées, faute de budget :**
- round 20 du UK Games Fund : Buried Things, Maximalist, Wristwork, Gibbonix, Valentine Games ;
- cohorte Ukie : Outer Pixels, Mercurial Dance, Miami Avalon ;
- délégation écossaise à Gamescom 2026.

## Fichiers

- `royaume-uni-animation-jeu-video.csv` : 16 lignes, 47 colonnes.
- `import-lemlist-lot13.csv` : **2 lignes** (Saltstone Studios, Pocket Sized Hands).
- `contacts-format-inconnu.csv` : 2 lignes (Team FOLON, inkle), COLD_OK sans adresse nominative.
- `contacts-serveur-muet.csv` : 1 ligne (thomas@saltstonestudios.com, C2).
- `contacts-sans-email.csv` : 0 ligne.
- `hold.csv` : 12 sociétés.
- `contacts-second-par-societe.csv` : 6 contacts.
- `reserve.csv` : vide.
- `ecartes-consolides.csv` : 63 lignes écartées, avec le motif.
- `adresses-u6.csv` : résultat de la recherche d'adresses dédiée.

## Checkpoint

| Champ | Valeur |
|---|---|
| Campaign | Lot 13 Royaume-Uni, animation et jeu vidéo indépendants (campagne non créée) |
| Status | livré pour validation |
| Target | 25 |
| Added | 16 sociétés (0 ajoutée dans Lemlist) |
| Remaining | 9 ; quelques pistes UK Games Fund et Ukie restent à qualifier |
| Excluded | 63 |
| HOLD | 12 |
| Credits used | 0 |
| Sequence | à définir (motion WLFG Consulting ; angle jeu : partenaire, éditeur ou financeur hors Royaume-Uni) |
| Launch | non |
| Next action | 1. Garry valide. 2. Tester dans Lemlist les 2 adresses publiées et thomas@saltstonestudios.com. 3. Pour Team FOLON et inkle, écrire au générique (business@, info@) pour obtenir le bon contact, ou tester prenom@ si Garry l'autorise (motif majoritaire du lot). 4. Qualifier les pistes UK Games Fund round 20 restantes. |
