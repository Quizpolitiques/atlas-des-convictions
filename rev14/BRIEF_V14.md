# Élargissement géographique du catalogue (V14) : consignes

Tu ajoutes au catalogue d'un quiz politique en français des régimes, partis et personnages des pays de ta
mission. Lis d'abord en entier :
- `/home/claude/quiz/data/BRIEF_CATALOGUE.md` (échelle, neutralité, usage de null, format) ;
- `/home/claude/quiz/data/axes.json` (**63 axes**, définitions et repères de calibrage : ils priment sur tout) ;
- `/home/claude/quiz/data/ideologies_liste.json` (79 doctrines, pour le champ `courants`) ;
- `/home/claude/quiz/data/revision/reference_v14.txt` : les valeurs actuelles de ~50 profils de référence sur
  les 63 axes. **Calibre-toi dessus** : un parti social-démocrate de ton lot se place comme le SPD ou le PS, un
  État d'Afrique de l'Ouest actuel comme le Sénégal ou la Côte d'Ivoire 2026, un dirigeant communiste comme
  Staline ou Hô Chi Minh selon son profil, etc.

Interdiction absolue de lire quoi que ce soit dans `/home/claude/romancypherpunk/`.

## Doublons
`/home/claude/quiz/data/revision/index_catalogue.txt` liste les 980 profils existants (id, nom, pays, époque).
**Vérifie chaque entrée envisagée par grep (nom et variantes) avant de la créer** : n'ajoute jamais un profil
déjà présent, même sous un autre pays (par exemple Che Guevara est rattaché à l'Argentine, Simón Bolívar à la
Colombie, Tito à la Croatie). Ne crée pas non plus d'entrée d'avant 1500 hors du lot « sociétés anciennes ».

## Ce qu'on positionne
- **Régime ou État** : ce que le régime a institué et pratiqué. Pour chaque pays actuel, une entrée
  « Pays (2026) » (id `pays-2026`) qui décrit le droit et les politiques en vigueur.
- **Parti** : programme et pratique à sa période caractéristique ; pour un parti actuel, ses positions récentes.
- **Personnage** : sa pensée et son action ; s'il a évolué, sa période la plus marquante.
- Pour chaque pays, vise : l'État en 2026, son dirigeant actuel, les principaux partis ou forces (majorité et
  opposition, en couvrant l'éventail réel), et une à trois figures ou régimes historiques marquants. Les
  quotas de ta mission sont indicatifs (±20 %).

Nous sommes fin octobre 2026 : **vérifie par recherche web** qui dirige chaque pays actuel et les changements
récents (élections, coups d'État, guerres). Ne mentionne une fonction actuelle que si tu l'as vérifiée. Réserve
les autres recherches aux vrais doutes.

## Les axes
Renseigne les 63 axes. Mets null seulement quand l'entrée n'a aucune position identifiable (notion sans objet
à l'époque, aucune source) : pour un État ou un parti contemporain, la plupart des axes se renseignent. Pour une
société ancienne, n'applique pas les catégories de l'économie moderne sans objet (négociation collective,
barème de l'impôt, discrimination positive, monnaie là où il n'y en a pas). Retire une entrée si tu ne peux pas
renseigner au moins 15 axes de façon défendable.

Points d'attention sur les axes récents :
- `fondement` (Fondement du droit), `selection` (Sélection des gouvernants), `statuts` (Égalité des statuts) :
  lis bien leurs définitions et leurs « pièges » dans axes.json.
- `statuts` : l'orientation sexuelle et l'identité de genre n'y comptent pas (elles relèvent de `moeurs`) ;
  des mesures visant une religion, une origine ou les binationaux parmi les citoyens donnent -2 ; statut
  personnel religieux inégal (héritage, tutelle) de 0 à +2 selon l'ampleur.
- `normes` : ordre juridique institué extérieur à l'État (traités, juridictions internationales, union d'États).

## Neutralité
Décris ce que chaque entrée a dit et fait, avec des faits vérifiables, sans adjectifs connotés ni jugement.
Sur les sujets conflictuels (Israël et Palestine, Kurdes, Rwanda, guerres civiles, régimes militaires,
apartheid, crimes de masse), rapporte les faits établis avec la même rigueur et le même ton pour toutes les
parties. Les crimes documentés d'un régime se mentionnent comme des faits, sans emphase.

## Format
Tableau JSON au format de `BRIEF_CATALOGUE.md` (id, nom, type, pays, zone, periode, epoque, courants, role,
description ≤ 300 caractères, traits 3 à 5 × ≤ 90 caractères, pos avec les 63 axes), avec ces précisions :
- `pays` : nom français du pays actuel de rattachement ; `zone` : « Europe », « Amériques », « Asie »,
  « Moyen-Orient et Afrique du Nord », « Afrique subsaharienne » ou « Océanie ».
- `epoque` : `Antiquité` (avant 500), `Moyen Âge` (500–1492), `Époque moderne` (1492–1789), `XIXe siècle`
  (1789–1914), `XXe siècle` (1914–1991), `Contemporain` (depuis 1991).
- `courants` : 1 ou 2 ids de `ideologies_liste.json`, la doctrine principale en premier ; liste vide sinon.
- `id` unique dans tout `/home/claude/quiz/data/catalogue/` et dans les autres lots : ajoute le pays en suffixe en
  cas d'ambiguïté (`parti-socialiste-belgique`, `parti-national-nouvelle-zelande`).

## Sauvegarde
Écris ton fichier `/home/claude/quiz/work/rev14/<lot>.json` **après chaque pays et au plus tard toutes les
4 entrées** (réécris-le en entier, toujours valide JSON) : l'utilisateur peut atteindre sa limite d'usage à tout
moment et rien ne doit être perdu. Tes
scripts éventuels vont dans `/tmp/claude-0/-home-claude/bd4d9ddc-b8ef-544d-a868-0b2393bfeb28/scratchpad/rev14_<lot>/`,
jamais à la racine du scratchpad (d'autres agents travaillent en parallèle). Si tu es relancé, relis ton fichier
et reprends au pays suivant. Ne modifie aucun fichier existant du catalogue.

## Vérification finale
Avec Python : JSON valide ; 63 clés dans chaque `pos` (celles d'axes.json) ; entiers de -3 à 3 ou null ; au moins
15 valeurs non nulles par entrée ; ids uniques et absents de index_catalogue.txt ; courants valides ; époque et
zone dans les listes. Réponse finale : chemin du fichier, nombre d'entrées par pays, et les 3 à 5
positionnements sur lesquels tu as le plus hésité.
