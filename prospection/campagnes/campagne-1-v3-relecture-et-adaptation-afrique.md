# Campagne 1 Animation/VFX (v3) : relecture et adaptation Afrique

## Relecture rapide

Le nouvel angle « studio à studio » colle mieux à la cible : nos contacts animation sont pour la plupart des fondateurs de petits studios (2 à 40 personnes), pas des directions achats. Six ajustements :

1. **[Region] ne correspond pas à notre liste.** Les notes citent Espagne / Amérique latine / Europe de l'Est / Canada. Nos 21 contacts de la campagne 1 sont en Afrique (Afrique du Sud, Kenya, Nigeria, Ouganda, Tanzanie, Maroc, Maurice…). Mettre « across Africa » ou le pays.
2. **« [CompanyName] caught my attention » reste générique.** Un fondateur sait que c'est un modèle. Nos fichiers ont une accroche précise par contact (colonne `note` : Jungle Beat 2, Kings of Jo'burg S3, Iwájú, Annecy, Fespaco…). Ajouter une variable Lemlist `{{accroche}}` d'une demi-ligne change la perception du premier mail.
3. **« Re: studio to studio » en objet du mail 2 simule une réponse.** Dans Lemlist, mieux vaut envoyer le mail 2 dans le même fil (option « répondre dans le fil ») : on garde l'effet conversation sans faux « Re: », que certains filtres et lecteurs repèrent.
4. **« Hey » avec des dirigeants seniors** (Mo Abudu, Stuart Forrest, Cecil Barry…) peut sembler trop familier. « Hi » garde le ton pair sans risque.
5. **« work closely with some of the bigger festivals » est vague.** Si Garry peut citer un nom (Annecy, Fespaco, Durban…), la crédibilité monte d'un cran. À n'écrire que si c'est exact.
6. **Les contacts francophones** (Maroc, Sénégal, Burkina, Maurice, Madagascar…) sont dans la campagne 5. Une version française est proposée plus bas pour eux.

Le reste tient : mails courts, une seule demande (15 min), sortie polie au mail 2 et au mail 3, aucun jargon d'agence.

---

## Version anglaise adaptée (Afrique anglophone)

Variables : `{{firstName}}`, `{{companyName}}`, `{{accroche}}` (une demi-ligne tirée de la colonne `note`), `{{country}}`.

### Mail 1 — J0
**Objet :** Quick one, {{firstName}} — studio to studio

Hi {{firstName}},

I run an animation studio myself and work closely with some of the bigger festivals, so I keep an eye on who's doing interesting work — {{accroche}} caught my attention.

I'm also helping a handful of studios like {{companyName}} with international business development: mainly opening doors to co-pros, distribution and B2B deals that are hard to reach from where you are.

Worth a 15-min call to see if there's a fit? No deck, no pitch — just two people in the industry comparing notes.

[Signature]

*Exemples de `{{accroche}}` : « Jungle Beat 2 » (Sandcastle) ; « your VFX work on Kings of Jo'burg S3 » (Luma) ; « the Toei co-production » (Comic Republic) ; « Sasa's Island at MIFA » (Studio Zubaa).*

### LinkedIn — J+1 (visite du profil), J+3 (invitation)
« Hi {{firstName}} — saw {{companyName}}'s work, would be good to connect. Also sent you a short note by email. »

*60 contacts sur 74 ont désormais une URL LinkedIn dans la compilation (colonne `linkedinUrl`).*

### Mail 2 — J+5 (dans le même fil)
{{firstName}},

Following up quickly — the short version: I help studios like {{companyName}} get in front of the right people internationally (co-production partners, buyers, bigger clients) without spending months chasing cold leads.

If timing isn't right, no worries at all — just tell me and I'll leave it there.

[Signature]

### Mail 3 — J+10 (A/B)
**A — Objet :** Last one from me, {{firstName}}
{{firstName}}, I'll keep this short — if opening up international business for {{companyName}} is something you'd want to explore this year, happy to jump on a call. If not, all good, I won't keep bugging you.

**B — Objet :** One more thought, {{firstName}}
{{firstName}}, one thing I keep seeing with studios across Africa: budgets for international co-pros and B2B deals are often there, just hard to reach without the right contacts in Europe and North America. That's the gap I help close. Open to a quick chat if useful.

---

## Version française (campagne 5, Afrique francophone et océan Indien)

### Mail 1 — J0
**Objet :** Une question rapide, {{firstName}} — de studio à studio

Bonjour {{firstName}},

Je dirige moi-même un studio d'animation et je travaille de près avec plusieurs grands festivals, donc je suis ce qui se fait d'intéressant — {{accroche}} a retenu mon attention.

J'accompagne aussi quelques studios comme {{companyName}} sur leur développement international : surtout pour ouvrir des portes vers des coproductions, de la distribution et des contrats B2B difficiles à atteindre seul.

Est-ce qu'un appel de 15 minutes vous dirait, pour voir s'il y a un intérêt ? Pas de présentation, pas de pitch : deux personnes du métier qui échangent.

[Signature]

### LinkedIn — J+1 / J+3
« Bonjour {{firstName}}, j'ai vu le travail de {{companyName}}, ce serait un plaisir d'échanger. Je vous ai aussi envoyé un court message par email. »

### Mail 2 — J+5 (dans le même fil)
{{firstName}},

Je me permets une courte relance. En deux mots : j'aide des studios comme {{companyName}} à se faire connaître des bons interlocuteurs à l'international (partenaires de coproduction, acheteurs, gros clients), sans passer des mois à démarcher à froid.

Si le moment ne s'y prête pas, aucun souci : dites-le-moi et je n'insisterai pas.

[Signature]

### Mail 3 — J+10 (A/B)
**A — Objet :** Un dernier message, {{firstName}}
{{firstName}}, je fais court : si développer l'international pour {{companyName}} vous intéresse cette année, je suis disponible pour un appel. Sinon, aucun problème, je ne vous relancerai plus.

**B — Objet :** Une dernière idée, {{firstName}}
{{firstName}}, je le constate souvent avec les studios d'Afrique francophone : les budgets pour les coproductions internationales et les contrats B2B existent, mais restent difficiles à atteindre sans contacts sur place en Europe et en Amérique du Nord. C'est précisément ce que j'aide à faire. Disponible pour en parler si c'est utile.

*Vouvoiement par défaut : c'est l'usage pour un premier contact professionnel en Afrique francophone, même entre pairs.*

---

## Ordre d'envoi conseillé
1. Test sur un petit lot : les 10 livrables animation les plus solides (une personne par maison).
2. Si les réponses viennent, élargir à la campagne 1 entière, puis décliner le même angle pour les campagnes 2 (fiction) et 3 (pub/doc) en remplaçant « animation studio » par le métier de Garry le plus proche.
