# Lot 9 (master prompt v6) : studios d'animation et hybrides animation/jeu, pays lusophones

## Contacts par pays

| Pays | Contacts | Studios (1er contact) | 2e contacts | Publiées | Devinées | Sans email | A | B | C |
|---|---|---|---|---|---|---|---|---|---|
| Brésil | 8 | 5 | 3 | 0 | 3 | 5 | 5 | 2 | 1 |
| Portugal | 20 | 12 | 8 | 0 | 19 | 1 | 0 | 17 | 3 |
| Angola | 3 | 2 | 1 | 1 | 1 | 1 | 0 | 0 | 3 |
| Moçambique | 3 | 2 | 1 | 0 | 1 | 2 | 0 | 0 | 3 |
| Cabo Verde | 2 | 1 | 1 | 0 | 1 | 1 | 0 | 0 | 2 |
| **Total** | **36** | **22** | **14** | **1** | **25** | **10** | **5** | **19** | **12** |

Objectif : 20 contacts par pays (100). Atteint au Portugal seulement, et avec 12 studios distincts. Le Brésil est épuisé par les lots 7 et 8 (studios déjà contactés exclus). L'Afrique lusophone est quasi vide : ce sont tous les studios d'animation trouvés dans ces trois pays.

Note sur la priorité : les agents ont utilisé A/B/C comme niveau de qualité du studio et du contact (A = studio actif et dirigeant confirmé ; B = studio actif, adresse devinée ; C = cas limite). Le statut de l'adresse est dans la colonne `statutEmail`.

## Hybrides animation + jeu vidéo : 1 studio

- Bonako (Cabo Verde), « oui - jeu dominant » : jeux et applis mobiles. Aucune production animée propre trouvée.
- Aucun hybride trouvé au Brésil, au Portugal, en Angola ou au Mozambique. Fly Moustache (Portugal) travaille pour des clients du jeu vidéo (Riot) mais ne développe pas de jeux : classé « non ».

## Cas limites (C) : 12 lignes, 9 studios

- **Portugal :** Ciclope Filmes (seul fait 2025 : une rétrospective), Praça Filmes (dernier film sorti en 2022), Fly Moustache (aucun projet daté 2025-2026).
- **Brésil :** Mandra Filmes.
- **Angola :** O Ilusionista (aucun fait daté, phrase de repli), Mwiloo (un seul fait 2026 : sélection Ottawa 2026, sans domaine).
- **Moçambique :** FX Animation Studios (dernière preuve en août 2024), ANIMA Estúdio Criativo (dernière animation datée en 2021).
- **Cabo Verde :** Bonako (dernier fait daté en 2019 ; c'est peut-être surtout un prestataire d'applications).

## Fichiers

- `bresil-`, `portugal-`, `angola-`, `mocambique-`, `cabo-verde-lot-animation-jeu.csv` : un fichier par pays, 18 colonnes.
- `import-lemlist-lot9.csv` : **1 ligne**, Eliete Pires (O Ilusionista, Angola), seule adresse publiée du lot. Elle remplace le 1er contact du studio, Carlos Guimarães, dont l'adresse est devinée et donc bloquée. Elle est « Gestora de contas », pas dirigeante : son rôle sera de transmettre le message.
- `contacts-serveur-muet.csv` : 25 adresses devinées, aucune à importer tant que le domaine n'a pas répondu. Le DNS de l'environnement est hors service depuis le 12 octobre, aucun MX n'a pu être vérifié. 17 sont des 1er contacts, 8 des 2e contacts (tous au Portugal) (voir colonne `note`).
- `contacts-sans-email.csv` : 10 contacts sans adresse.
- `agent-0X-ecartes.csv` : studios écartés, avec le motif.

## Contrôles faits

- Pas de doublon d'adresse entre pays, ni avec les lots 1 à 8.
- Aucun studio déjà contacté ou déjà écarté (`exclusions.txt`) n'est repris.
- `firstName`, `companyName`, `icebreaker` et `senderName` sont remplis partout. Mr. Plot (Brésil) : seul le surnom « Chaps » est connu, `lastName` est vide.
- Icebreakers : 31 faits sourcés avec URL, 5 phrases de repli (O Ilusionista ×2, Bonako ×2 en anglais, Fly Moustache). La phrase de repli est écrite « em Angola » ou « em Portugal », plus correct que le « no {pays} » du modèle.
- `secteur` = « estúdio de animação » partout (pas de valeur française dans les textes portugais).

## Domaines non vérifiés (DNS hors service) : à tester dans Lemlist

- **Brésil :** miralumo.com, mrplot.com.br, mandra.com.br
- **Portugal :** bapstudio.com, animais-avpl.com, sardinhaemlata.com, osfilmesdopinguim.pt, easylabanimation.com, filmesdogajo.pt, colaanimation.com, aimcreativestudios.com, animanostra.pt, ciclopefilmes.com, flymoustache.com
- **Angola :** oilusionista.net
- **Moçambique :** anima.co.mz
- **Cabo Verde :** bonako.com

Trois studios portugais publient leur contact sur une adresse gmail (Os Filmes do Pinguim, Easylab, Filmes do Gajo) : leur domaine ne reçoit peut-être pas de mail.

## Pistes pour compléter

- **Portugal :** OH! Multimedia (hybride possible), Bro Cinema, Bando à Parte, Filmógrafo, la liste complète de la Portugal Film Commission (novembre 2025), Lisboa Games Week pour les hybrides.
- **Moçambique :** les organisateurs de la mostra d'animation de la Casa Velha (Maputo, mars 2026).
- **Cabo Verde :** Mitheria Studios (série « Aventuras di Azul », 2026), à reprendre si une deuxième source apparaît.
