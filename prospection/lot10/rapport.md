# Lot 10 (master prompt v7) : studios d'animation et de jeu vidéo, Suède

## Contacts par pôle

| Pôle | Contacts | Studios | dont réserve | A | B | C | Jeu | Animation |
|---|---|---|---|---|---|---|---|---|
| Stockholm | 33 | 22 | 0 | 0 | 12 | 10 | 13 | 9 |
| Malmö / Scanie | 23 | 13 | 0 | 0 | 10 | 3 | 13 | 0 |
| Göteborg (+ Trollhättan) | 13 | 9 | 0 | 0 | 9 | 0 | 8 | 1 |
| Skövde | 12 | 9 | 1 | 0 | 7 | 2 | 9 | 0 |
| Umeå / Skellefteå / Luleå | 7 | 6 | 1 | 1 | 4 | 1 | 6 | 0 |
| Visby / Gotland | 1 | 1 | 0 | 0 | 0 | 1 | 1 | 0 |
| **Total** | **89** | **60** | **2** | **1** | **42** | **17** | **50** | **10** |

Priorités et types comptés par studio (1er contact). 58 studios dans le quota de 60, plus 2 en réserve (Redbeet Interactive, Blamorama Games).

**Répartition : 50 jeu, 10 animation, 0 hybride.** Neuf des dix studios d'animation sont à Stockholm ; le dixième est Dockhus Animation (Trollhättan). Aucun studio d'animation trouvé à Malmö, Skövde ou dans le nord.

## Adresses

| Statut | Lignes |
|---|---|
| Publiée | 2 (samuel@brikk.se, tobias@turborilla.com) |
| Devinée | 22 (une par domaine) |
| Sans email | 65 |

Le DNS de l'environnement est hors service : aucun MX vérifié, `verificationMX` = « non vérifié (DNS) » partout.

Un seul format observé : prenom@ chez Turborilla. Toutes les autres adresses devinées sont au format par défaut (prenom.nom@ au-delà de 10 personnes, prenom@ en dessous).

## Fichiers

- `suede-{pole}-animation-jeu.csv` : un fichier par pôle, 21 colonnes.
- `suede-total-animation-jeu.csv` : les 89 lignes, avec une colonne `pole` en tête.
- `import-lemlist-lot10.csv` : **2 lignes**, les seules adresses publiées :
  - Samuel Fast Hurtigkarl (Brikk Animation, Stockholm) ;
  - Tobias Andersson (Turborilla, Umeå). Il est fondateur, maintenant au conseil d'administration. Son adresse publiée remplace celle du CEO John Wright, devinée et donc bloquée.
- `contacts-serveur-muet.csv` : 21 adresses devinées, à ne pas importer tant que le domaine n'a pas répondu. John Wright (Turborilla) y figure ; son format prenom@ est observé.
- `contacts-sans-email.csv` : 36 premiers contacts sans adresse, faute de domaine confirmé.
- `contacts-second-par-studio.csv` : 28 contacts supplémentaires des studios déjà représentés.
- `reserve.csv` : 2 studios au-delà du quota de leur pôle. Les deux sont en C.
- `agent-0X-ecartes.csv` : studios écartés, avec le motif.

## Studios écartés pour actionnariat (33)

- **Embracer et ses filiales :**
  - directement : Coffee Stain Studios, Palindrome Interactive, Pieces Interactive (THQ Nordic), Bitwave Games ;
  - via Amplifier Game Invest : Infinite Mana Games, Green Tile Digital, FRAME BREAK, River End Games, Tarsier Studios ;
  - via Saber Interactive : Tuxedo Labs.
- **Coffee Stain Group :** Box Dragon, Coffee Stain Gothenburg.
- **Thunderful :** Station Interactive, Thunderful Malmö, Thunderful Skövde, Stormteller Games, To the Sky.
- **Tencent :** Sharkmob, Stunlock Studios, The Outsiders (via Funcom).
- **Autres groupes :**
  - Massive (Ubisoft) ; King (Microsoft) ; EA Gothenburg (Electronic Arts) ;
  - Avalanche Malmö (Avalanche Studios Group) ; Paradox Thalassic (Paradox Interactive) ;
  - Embark Studios (Nexon) ; Coldwood Interactive (Stillfront) ; Toadman Interactive (Enad Global 7) ;
  - Cortopia (Beyond Frames) ; Fall Damage (Fragbite Group) ; Hello There Games (eBlitz Group, une seule source) ;
  - Windup Games (Kinda Brave) ; Antler Interactive (ChromaWay) ;
  - Spin-Off Games (House of Discs, un groupe d'équipement de disc golf).

**Autres motifs d'écart :**
- taille > 50 : Hazelight, Arrowhead, Milford, Crossbridge ;
- pas d'activité 2025-2026 : environ 15 studios ;
- aucun dirigeant nommé : environ 25 studios, dont Tableflip (Visby), The Bearded Ladies et Apog Labs (Malmö), actifs et à reprendre si un nom apparaît ;
- développeurs solo ;
- hors pôle.

## Cas limites (C) : 17 studios

- **Stockholm :**
  - Valiant Game Studio : une seule personne à temps plein, sous le seuil de 2 personnes du brief. **À retirer si Garry applique le seuil strictement.**
  - Liquid Swords : plus de 50 personnes avant les licenciements de février 2025, investissement minoritaire de NetEase.
  - Cinematic, Kaktus Film : pas d'activité datée 2025-2026.
  - Rightsized Games, Sinnema Animation Studio, Double Up Studio, Studio Konkret : une seule source (LinkedIn).
  - Studio Fyr : surtout post-production son et VFX.
  - Lionbite Games : pas d'activité récente, nom du fondateur incertain.
- **Malmö :** Illusion Labs (aucune sortie 2025-2026), Midnight Hub (dernière preuve 2018), Svargames (présence en Scanie non confirmée).
- **Skövde :** Angry Demon Studio (dernière sortie 2024), Redbeet Interactive (réserve).
- **Nord :** Blamorama Games (réserve).
- **Visby :** Eat Create Sleep (dernier jalon daté : Kickstarter 2020).

## Contrôles faits

- Aucune adresse en double dans le lot ni avec les lots 1 à 9. Aucun studio du lot n'apparaît dans les lots précédents.
- Un studio n'est livré que dans un seul pôle. Dazed Games est rattaché à Göteborg, Turborilla à Umeå.
- `firstName`, `companyName`, `icebreaker` et `senderName` sont remplis partout.
- Icebreakers en anglais : 46 faits sourcés avec URL, 14 phrases de repli (comptés par studio). La colonne `icebreakerType` est harmonisée en « fait sourcé » / « phrase de repli ».
- `secteur` = « game studio » ou « animation studio » : pas de valeur française dans une variable des textes anglais.

## Domaines non vérifiés (DNS hors service) : à tester dans Lemlist

- **Stockholm :** brikk.se, midjiwan.com, fasttravelgames.com, landfall.se, mightanddelight.com, chiefrebel.com, liquidswords.com, kaktusfilm.com, wrongorgan.com, groplay.com
- **Malmö :** frictionalgames.com, simogo.com, illusionlabs.com, somethingwemade.se
- **Göteborg :** moonhood.se, wishfully.se, faroutgamestudio.com, eldenpixels.com
- **Skövde :** irongatestudio.se, piktiv.com
- **Nord :** turborilla.com, goldtowngames.com, blamorama.se

## Points à revérifier avant envoi

- **Postes ou dirigeants à confirmer :**
  - le titre de CEO d'Accel Sjöström (Pathos) repose sur un communiqué de 2022 ;
  - le titre exact de Felix Ekenstam (Midjiwan) n'est pas connu ;
  - William Jutbring (Dofhouse) n'est cité que par une fiche automatique.
- **Dates à recouper :**
  - la sortie de février 2026 d'Elden Pixels n'est confirmée par aucun extrait ;
  - l'année de sortie de Samson (Liquid Swords), probablement 2026 ;
  - la date de la version 1.0 de Valheim (Iron Gate), qui sert d'icebreaker.
- **Localisations à confirmer :** Speldosa (Skövde), Cinematic et Filmic Animation (Stockholm).
- **Sources uniques :** Valley Lodge, Rototoco et Frozen Maracuyas reposent sur une seule page de Game Habitat.


## Mise à jour du 16/10/2026 : adresses devinées pour les contacts sans email

Garry a demandé de deviner les 65 contacts sans email. Résultat sur 63 contacts traités (les 2 autres sont écartés, voir plus bas) :
- **49 adresses devinées** : 11 sur des domaines déjà confirmés (même format que le 1er contact du studio), 38 après recherche du domaine du studio.
- **3 adresses publiées trouvées** : anna@valiant.se (Valiant Game Studio), andreas@filmic.se (Filmic Animation), linda@leefilm.se (LEE Film). Elles passent dans l'import.
- **22 contacts restent sans email** (15 premiers contacts, 6 seconds, 1 réserve) : aucun domaine propre trouvé (itch.io, Steam ou Behance seulement). Studios concernés : Double Up Studio, Studio Fyr, Valley Lodge Games, Rototoco, Frozen Maracuyas, Midnight Hub, Svargames, Dockhus Animation, Dazed Games, Nuggets Entertainment, Ember Paw Games, Speldosa Interactive, Solid Block of Power, Polysoup Interactive, Full Rogue.
- **Sinnema Animation Studio écarté** (2 contacts) : le studio est basé à Berlin, hors périmètre Suède.

Domaines sources fragiles (vus seulement dans une base tierce ou un wiki, pas sur le site du studio) : cinematic.se (AroundDeal), oddiko.com (PitchBook), keepsake.games et lionbite.se (Giant Bomb), eatcreatesleep.net (annuaires), studio-konkret.se (LinkedIn donne aussi studio-konkret.com). À tester en premier dans Lemlist.

**Fichiers après mise à jour** (87 lignes, 59 studios dont 2 en réserve) :

| Fichier | Lignes |
|---|---|
| import-lemlist-lot10.csv | 5 (adresses publiées : Brikk, Turborilla, Valiant, Filmic, LEE Film) |
| contacts-serveur-muet.csv | 38 (1ers contacts, adresse devinée) |
| contacts-sans-email.csv | 15 (1ers contacts sans adresse) |
| contacts-second-par-studio.csv | 27 (21 devinées, 6 sans email) |
| reserve.csv | 2 |

Les fichiers sont désormais disjoints : une adresse n'apparaît que dans un seul fichier de sortie. Aucune adresse devinée n'est importable avant que son domaine ait répondu.
