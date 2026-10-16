# Lot 11 (master prompt v9) : Royaume-Uni, 4 segments

Livré pour validation par Garry. Rien n'a été importé ni lancé dans Lemlist ; Lemlist et HubSpot ont seulement été consultés, en lecture.

## Contacts par segment et par décision

| Segment | Contacts | Sociétés | PRIORITY | COLD_OK | HOLD | Objectif 25 contacts |
|---|---|---|---|---|---|---|
| A, studios d'animation (< 30 pers.) | 30 | 21 | 1 | 5 | 15 | atteint |
| B, groupes médias (10-500 pers.) | 31 | 24 | 3 | 13 | 8 | atteint |
| C, organisateurs d'événements | 24 | 21 | 2 | 14 | 5 | **manqué d'un contact** |
| D, accélérateurs et incubateurs | 27 | 23 | 3 | 12 | 8 | atteint |
| **Total** | **112** | **89** | **9** | **44** | **36** | 100 atteint |

Décisions comptées par société (1er contact). Les 23 contacts supplémentaires suivent la décision de leur société.

- **PRIORITY (9) :**
  - A : Lupus Films (80)
  - B : Zinc Media (82), Audioboom (81), Kelsey Media (82)
  - C : Manchester Animation Festival (85), Edinburgh TV Festival (87)
  - D : Creative UK (83), Indielab (80), Royal Holloway / CoSTAR (84)
- **EXCLUDE :** voir la section « Sociétés écartées ». Le segment C a perdu 4 événements à la vérification Lemlist / HubSpot (Sheffield DocFest, Film London / London Games Festival, AIM Connected, Content London) : c'est ce qui le fait passer sous 25.

## Segment A : répartition et écarts

- **Répartition des 21 studios :** 17 animation, 2 hybrides animation-jeu (Pokedstudio, Atelier 11), 2 services (Flipbook Studio, Bomper Studio).
- **Écartés pour taille ≥ 30 :** Karrot, Studio AKA, Magic Light, Golden Wolf, CAKE (gardé au segment B comme distributeur), Blue Zoo, Blink Industries, Locksmith, Koala FX, Sun & Moon, Paper Owl, Cloth Cat, Mackinnon & Saunders, Fourth Wall, Axis, A Productions (51-200 sur LinkedIn), Aardman.
- **Écartés pour actionnariat :**
  - groupes de production : Strange Beast (Passion Pictures), Blinkink (groupe Blink), Wildseed (Mediawan), Flickerpix (groupe Waddell Media) ;
  - autres groupes : Animade (Duolingo, à confirmer), Studio Liddell (Immotion) ;
  - antennes britanniques de studios étrangers ou coentreprises : Brighton Zoo (Blue Zoo), Gutsy, Kavaleer, Brown Bag.
- **Le segment A est le plus fragile.** 15 studios sur 21 sont en HOLD : pas d'activité 2025-2026 prouvée, taille ou forme juridique introuvable. Beaucoup de petits studios britanniques ne publient ni effectif ni site à jour.

## Adresses

| Statut | Lignes |
|---|---|
| Publiées | 3 |
| Devinées | 102 |
| Sans email | 7 |

- **Publiées :**
  - steve@manchesteranimationfestival.co.uk : fiche de 2019 ;
  - dave@encounters.film : communiqué de 2020 ; une offre d'emploi « Festival Director » laisse penser que le poste change ;
  - une adresse chez Falmouth University, mais la société est en HOLD.
- **Devinées :** sur 102, 41 viennent de la passe de recherche de domaine du 16/10 (15 sur des domaines déjà connus, 26 après recherche du site). Formats réellement observés sur 3 domaines seulement :
  - spectator.co.uk : initiale+nom ;
  - bathspa.ac.uk et kent.ac.uk : initiale.nom ;
  - york.ac.uk : règle publiée prenom.nom.
  Ailleurs, format par défaut (prenom@ en dessous de 10 personnes, prenom.nom@ au-delà).
- **Sans email (7) :** Dog Ears (2), Cahoots Studios, King Banana (2), Bonnie and Braw, Atelier 11. Aucun site propre trouvé.
- **verificationMX = « non vérifié (DNS) » partout :** le DNS de l'environnement est hors service.
- **Liens :** les pages ne peuvent pas être ouvertes (proxy). Tous les liens livrés ont été vus tels quels dans un résultat de recherche, aucun n'a été ouvert.

## Fichiers

- **Fichiers par segment, 29 colonnes :**
  - `uk-a-studios-animation.csv` (30 lignes)
  - `uk-b-groupes-medias.csv` (31)
  - `uk-c-evenements.csv` (24)
  - `uk-d-accelerateurs-incubateurs.csv` (27)
- `uk-total.csv` : les 112 lignes.
- `import-lemlist-lot11.csv` : **2 lignes**, les seuls PRIORITY / COLD_OK avec une adresse publiée (Manchester Animation Festival, Encounters).
- `contacts-serveur-muet.csv` : **51 lignes**, des PRIORITY / COLD_OK (1er contact) dont l'adresse est devinée. Ils ne seront importables qu'après une réponse du domaine.
- `contacts-sans-email.csv` : 0 ligne. Les 7 contacts sans adresse sont tous en HOLD ou en 2e contact.
- `hold.csv` : 36 sociétés en HOLD (1er contact).
- `contacts-second-par-societe.csv` : 23 contacts supplémentaires.
- `reserve.csv` : vide. Aucun segment n'a dépassé son quota.
- `consolidation-ecartes.csv` : les 15 lignes retirées à la consolidation. `agent-*-ecartes.csv` : les 118 écarts des agents.
- `verif-crm-sortie.csv` : le résultat de la vérification Lemlist / HubSpot pour les 100 sociétés.

## Sociétés écartées et pourquoi

**Pendant la recherche (118 lignes dans les fichiers `agent-*-ecartes.csv`) :**

| Motif | Nombre |
|---|---|
| Pas d'activité ou d'édition 2025-2027 | 35 |
| Hors périmètre (événement de collectivité, accélérateur généraliste, autre segment, hors zone) | 26 |
| Taille (≥ 30 en A, hors 10-500 en B) | environ 20 |
| Actionnariat (groupes exclus, filiales) | 17 |
| Aucun dirigeant nommé | 11 |
| Déjà dans Lemlist (connus d'avance : Develop:Brighton, The Great Escape, Liverpool Sound City, SXSW London, Pocket Gamer Connects) | 5 |
| Forme juridique | 3 |

**Exemples d'actionnariat au segment B :** Firecrest (Channel 4), Stellify (Sony), Red Planet et Dancing Ledge (Fremantle), Initial (Banijay), Blast Films (Sky), KEO Films (Passion Pictures), Mortons (Kelsey Media).

**À la consolidation (15 lignes, `consolidation-ecartes.csv`) :**
- **Déjà dans Lemlist (7 sociétés, ajoutées entre le 15 et le 30/09/2026) :**
  - Goalhanger : harry@goalhanger.com dans « English Campaign » ;
  - Sheffield DocFest ;
  - AIM ;
  - C21Media / Content London ;
  - Ukie ;
  - Scottish Game Developers Association ;
  - Ravensbourne University London.
- **Déjà dans HubSpot (1 société) :** Film London, dernier contact le 19/06/2026.
- **Autres :**
  - A Productions : taille 51-200 ;
  - Flickerpix : groupe Waddell Media ;
  - Culture & Business Scotland : EXCLUDE, score 55 ;
  - Film London : doublon entre les segments C et D.
- **Forme juridique : aucun sole trader ni partenariat retenu.**

## Cas limites

- **Formes juridiques non trouvées (8, toutes en HOLD) :** Flipbook Studio, Red Star 3D, A+C Studios, Tortoise Media, Scottish Games Network (Scottish Games Week), Lakes International Comic Art Festival, FOCUS Wales, Falmouth University.
  - Piste pour Red Star 3D : RED STAR STUDIO LIMITED (05180819), à confirmer.
- **Universités : décision à prendre par Garry.** Pour Royal Holloway, Cardiff, UAL, Bath Spa, Teesside, York, Ulster et Kent, la forme juridique notée est la forme d'usage (corporation à charte royale ou équivalent), sans source Companies House. Une université est bien une personne morale (« corporate subscriber »). Mais si la règle « forme non trouvée = HOLD » s'applique strictement, Royal Holloway (PRIORITY), Cardiff, UAL et Bath Spa passent en HOLD.
- **Taille non trouvée :** 56 sociétés sont en priorité C, dont la plupart des groupes médias du segment B.
- **Contacts à revérifier :**
  - Wonderhood : David Abraham devient executive chairman après le rachat d'Elvis.
  - One6th : le duo est représenté par Strange Beast depuis janvier 2026.
  - Hoho : la co-fondatrice s'appelle Helen Howells sur le site, Helen Wilkes à Companies House.
  - Postes dont la source date de 2023-2024 : Encounters, UAL, Teesside, Screen Scotland, York.
  - Children's Media Conference : déménage à Londres en 2027.
  - Edinburgh TV Festival : déménage à Manchester en 2027.
- **Périmètre :**
  - Jungle Creations : détenue par un fonds, en partie agence sociale.
  - Wonderhood : agence et production TV.
  - Baltic Creative : d'abord un gestionnaire d'espaces.
  - Belfast XR Festival : gardé au segment D pour son programme Amplify:XR Labs.

## Ce qui reste à vérifier dans Lemlist avant import

1. **Tester les 81 domaines des adresses devinées.** C'est la règle bloquante : aucune adresse devinée n'entre dans l'import avant que son domaine ait répondu. Commencer par les PRIORITY / COLD_OK de `contacts-serveur-muet.csv`.
2. **Confirmer les 2 adresses publiées de l'import :** elles datent de 2019 et 2020. Pour Encounters, vérifier que le CEO est toujours en poste.
3. **Domaines incertains :**
   - hattrick.co.uk : une base tierce donne @hattrick.com ;
   - edfilmfest.org : l'ancien edfilmfest.org.uk circule encore ;
   - one6th.co ;
   - spectator.co.uk : le site est passé sur .com.
4. **Variables Lemlist :** `firstName`, `companyName`, `icebreaker`, `senderName` sont remplis partout, et `eventName` sur toutes les lignes du segment C. `companyName` ne contient ni virgule ni « Ltd ».
5. **Mention légale UK :** chaque envoi doit identifier l'expéditeur et proposer une désinscription.

## Checkpoint

| Champ | Valeur |
|---|---|
| Campaign | Lot 11 Royaume-Uni (segments A, B, C, D), campagnes non créées |
| Status | livré pour validation |
| Target | 100 contacts (25 par segment) |
| Added | 112 contacts nominatifs (89 sociétés) ; 0 ajouté dans Lemlist |
| Remaining | 1 contact pour le segment C ; 51 adresses devinées à valider |
| Excluded | 15 à la consolidation (dont 8 déjà dans Lemlist / HubSpot) + 118 pendant la recherche |
| HOLD | 36 sociétés |
| Credits used | 0 |
| Sequence | à définir par segment (motion WLFG Consulting pour A et B, WLFG événements 2027 pour C, WLFG Blueprint pour D) |
| Launch | non |
| Next action | Garry valide le lot et tranche le cas des universités ; tester les domaines dans Lemlist ; importer d'abord les PRIORITY / COLD_OK dont le domaine répond |
