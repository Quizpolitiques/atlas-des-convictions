# Avancement de l'Atlas des convictions

Mis à jour le 29 octobre 2026, 12 h 50. Version 17 publiée : 60 axes, 300 questions, 980 profils, 79 doctrines (questionnaire v6, justice et pouvoir politique). Sert à reprendre le travail après une interruption
(limite d'utilisation, redémarrage de session).

## Terminé et publié (version 5)
- 50 axes (`data/axes.json`), 250 questions (`data/questions.txt` → `questions.json`).
- Catalogue français complet sur 50 axes : `data/catalogue/fr_*.json` (218 profils).
- 79 doctrines sur 50 axes : `data/ideologies/ideologies_1.json` à `_4.json`.
- Section 2027 : `data/presidentielle2027_*.json` ; courants : `data/courants*.json`.

## Vague mondiale (fichiers `data/catalogue/monde_*.json`)
Pour reprendre un lot interrompu : envoyer un message (SendMessage) à son agent pour qu'il
continue ; s'il ne répond plus, relancer un agent avec `data/BRIEF_MONDE.md` et la liste du lot
(dans la conversation ou `data/en_attente/monde_NN.txt`), en lui demandant de compléter le fichier
existant plutôt que de repartir de zéro.

| Lot | Fichier | Agent | État |
|---|---|---|---|
| 01 Allemagne, Autriche | monde_01_allemagne_autriche.json | a26a2371039aa0ba2 | terminé |
| 02 Royaume-Uni | monde_02_royaume_uni.json | acbe15c92b593b514 | terminé |
| 03 Italie, papauté | monde_03_italie.json | ace15eb0c9f0ec61f | terminé |
| 04 Espagne, Portugal | monde_04_espagne_portugal.json | a04c319dc76cf9f1a | terminé (45) |
| 05 Russie, Biélorussie, Ukraine | monde_05_russie_bielorussie_ukraine.json | a5fba692dcb30dc04 | terminé |
| 06 Grèce, Pologne, Hongrie | monde_06_grece_pologne_hongrie.json | ae680cbdb005aae5f | terminé |
| 07 Europe centrale et du Nord | monde_07_europe_centrale_nord.json | a9338798854561a6d | terminé |
| 08 États-Unis | monde_08_etats_unis.json | aada219d35ae9e2b7 | terminé |
| 09 Canada, Mexique, Australie | monde_09_canada_mexique_australie.json | a23ddfa04d219da14 | terminé (42) |
| 10 Amérique latine | monde_10_amerique_latine.json | aa8b6611ca6fb36c1 | terminé |
| 11 Asie de l'Est | monde_11_asie_est.json | ad256625243235ee7 | terminé (43) |
| 12 Asie du Sud et centrale | monde_12_asie_sud_centrale.json | a9c91be7fb020d461 | terminé |
| 13 Moyen-Orient | monde_13_moyen_orient.json | a3455433bdba61b91 | terminé |
| 14 Afrique du Nord et Sahel | monde_14_afrique_nord_sahel.json | a5cd4f6f1bfa4274b | terminé |
| 15 Afrique subsaharienne | monde_15_afrique_subsaharienne.json | af91eb6d3b49a2d9f | terminé (46) |

## Sauvegardes
`build/sauvegarde.py` copie chaque minute tout fichier du catalogue ou des doctrines qui change,
dans `sauvegardes/` (`NOM.dernier.json` + versions horodatées). Un fichier vide ou invalide n'est
jamais sauvegardé ; si un fichier perd des entrées, la version plus complète est conservée à part
(`NOM.plus-complet-HHMMSS.json`). Relancer le script après une interruption.

## Après la vague mondiale
1. Restaurer depuis `sauvegardes/` tout fichier `monde_*` plus court que sa sauvegarde.
2. `python3 build/review.py all` : remplissage, auto-reconnaissance, quasi-doublons ; vérifier la
   cohérence entre pays sur quelques axes (`review.py axis:regime`, etc.).
3. `python3 build/build.py` puis publier `atlas-des-convictions.html` (même chemin, même adresse).

## Version 6 du questionnaire (lancée le 28 octobre 2026, 20 h 30) : justice et pouvoir politique
52 axes, 260 questions. Nouveaux axes `independance` et `justice_elus`, axe `juridictionnel`
renommé « Dernier mot » (juge contre souverain) ; 3 questions reformulées (reformulees.json, clé 6).
Consignes : `data/BRIEF_V6.md`. Sauvegarde d'avant : `sauvegardes/avant_v6/`. Pour reprendre un lot :
SendMessage à l'agent ; sinon nouvel agent avec BRIEF_V6.md et les mêmes fichiers (il reprend aux
entrées sans `independance`). Avancement : `python3 -c` comptant les entrées ayant `independance`.

| Lot | Fichiers | Agent |
|---|---|---|
| fr_a | fr_regimes, fr_partis_historiques, fr_sapir | a4d9148fcdf9baab8 |
| fr_b | fr_partis_ve, fr_2027_a, fr_2027_b | ac6ab80d8a2152b38 |
| fr_c | fr_personnages_1, fr_personnages_2 | a1f3ebbf53f059532 |
| fr_d | fr_personnages_3 | a096d0d89a6b2deee |
| ideo_a | ideologies_1, ideologies_2 | a3beed4b28871ccd9 |
| ideo_b | ideologies_3, ideologies_4 | a7d4ad64a2eaf85fd |
| m01 | monde_01 | a680138ee402ba5e9 |
| m02_09 | monde_02, monde_09 | a51f0f33ddc9a9d22 |
| m03 | monde_03 | ae29ea5b03def09f8 |
| m04 | monde_04 | aa0b6c5d5c175372f |
| m05 | monde_05 | ab5a1667989242bbf |
| m06 | monde_06 | a6a06303144afdf5d |
| m07 | monde_07 | a99f83411e1273cbb |
| m08 | monde_08 | aa3998715a1d15365 |
| m10 | monde_10 | a5ac758d5ee2f6537 |
| m11 | monde_11 | a8794c2f3aad80f62 |
| m12 | monde_12 | a315f9efea8fb6a68 |
| m13 | monde_13 | a9810004b1ac106c4 |
| m14 | monde_14 | a87ba9d1db1d32a0a |
| m15 | monde_15 | a1d923293f681fbe5 |
Tous les lots v6 terminés, dirigeants français harmonisés avec leurs partis, Version 9 publiée. Axe `justice_elus` affiché « Justice et gouvernants ». Excel : `python3 build/excel.py`.

## Version 7 du questionnaire (lancée le 29 octobre 2026, 0 h 05) : axe `influences`
53 axes, 265 questions. Consignes : `data/BRIEF_V7.md`. Sauvegardes d'avant : `sauvegardes/avant_v7*`.
Template VERSION = 7 et note "7" déjà en place. Lots et agents : fr_a a556ba0f196b37eda, fr_b
a003bf94b624db96c, fr_c adb64b3ed885a3cea, fr_d ad17366d514bdc886, ideo aacf8bdfd6b46439c,
m01_03 ab4a8e671fe239a59, m02_09 af8383b2e93ff9ebf, m04_06 a0035ded15a19a167, m05_07
aa165c7dbd0a98d46, m08_10 a3bc9629a6b648891, m11_12 ae8a99d77e38272a4, m13 aff4213dd7875d7f8,
m14_15 a452350807749e6ed. Ensuite : build, excel.py, vérification, publication.
Lots v7 terminés, Version 10 publiée. Version 11 : Vue d'ensemble en 8 thèmes (build.py, THEMES ; template overviewHTML) publiée.
Version 12 : bouton « Exporter en PDF » (jsPDF 2.5.1 chargé à la demande depuis cdnjs, capacité downloads déclarée ; fonction buildPDF dans le template).
Version 13 : PDF avec courant de chaque correspondance et classement des 79 doctrines.

## Version 8 du questionnaire (lancée le 29 octobre 2026, 10 h 50) : 60 axes, 300 questions
Nouveaux axes concurrence, travail, dette, memoire, animal, climat, transition, nature ; `ecologie`
supprimé (les agents doivent retirer la clé). Consignes : `data/BRIEF_V8.md`. Sauvegarde d'avant :
`sauvegardes/avant_v8/`. Template VERSION = 8, note "8" et THEMES avenir -> climat déjà faits.
Lots : fr_a afbe76de7f0a4c9bd, fr_b a50d39cec4dda8c89, fr_c ab783cc9f4bc62a8d, fr_d a8cb7f31f44c612a6,
ideo_a a578c794af8b33064, ideo_b ab968044a08e97df9, m01 ac28875fb8fde13dd, m02_09 a6f79e001c40588dc,
m03 a5977ba12959c355e, m04 a3a4ec05f2c5557da, m05 aa03faec755747f78, m06 a7c16624735e80c10,
m07 ab8600ac286eb8e6e, m08 af1efe18be6550ad7, m10 a6def77fdb4e3f211, m11 aeb2175f4e82f9575,
m12 ae342bdaf4ea65323, m13 a92bb8822e21b5669, m14 a56fc738ed7e564b0, m15 a8e022ffb3369f249.
Ensuite : harmonisation France, build (vérifier THEMES et libellés Avenir), excel.py, test, publication.
Version 14 publiée : 60 axes, 300 questions (v8 du questionnaire) ; purge des réponses obsolètes au chargement ; libellés Avenir : « Écologie et précaution » / « Croissance et exploitation des ressources ».
Version 15 : transition-2, nature-1 (pesticides au lieu de sanctuarisation), nature-3 reformulées (reformulees clé 9, VERSION 9).

## Révision transversale (lancée le 29 octobre 2026, 11 h 15)
But : homogénéiser l'échelle entre lots, corriger les incohérences entrées liées / courants, combler
les null défendables. Les agents n'écrivent pas dans le catalogue : ils produisent des patchs dans
scratchpad/rev/<famille>/patch.json (format : id, axe, avant, apres, motif) et
scratchpad/rev/courants_<lot>/patch_courants.json. Consignes : data/BRIEF_REVISION.md,
data/BRIEF_COURANTS.md. Tables : data/revision/. Sauvegarde d'avant : sauvegardes/avant_revision/.
Application : python3 build/appliquer_patch.py <patchs> (journal dans data/revision/journal.json) ;
courants : à appliquer à la main (fr_* via data/courants.json, monde_* inline).
Agents : institutions a0115708d7374a361, ordre a2621a27b1a8b6fcb, economie ae84c2144523fadfe,
fiscalite a4d99cbfc4970a7a0, nation ae2ecd750c7f6c01d, international a183ee37a5b34ed94,
societe ab9750a46030b8dd0, avenir afc50f5fb194264d7, courants_europe a75f44aff9a3ab7b9,
courants_monde a5ccb0d28686c00bf.
Sauvegarde continue des patchs : `python3 build/sauvegarde_patchs.py` copie scratchpad/rev/*/patch*.json
vers data/revision/patchs/<lot>.json chaque minute. Pour reprendre un relecteur interrompu : SendMessage
à son agent ; sinon nouvel agent avec le même brief, en lui donnant data/revision/patchs/<lot>.json comme
point de départ (reprendre à l'axe suivant le dernier corrigé).
11 h 30 : limite d'utilisation atteinte (reprise 14 h 10). Terminés : avenir (65), courants_europe (13),
courants_monde (21). Partiels (sauvegardés dans data/revision/patchs/) : economie 69 (jusqu'à strategique,
reste commerce, capitaux, monnaie), institutions 11 (regime seulement), ordre 62 (reste armes), societe 71
(jusqu'à bioethique, reste vie, corps, moeurs, animal, egalite, education). Sans patch : nation,
fiscalite, international (vérifier scratchpad/rev/). À 14 h 10 : SendMessage aux agents « continue à
partir de ton patch, axes restants » ; si un agent ne répond pas, nouvel agent avec BRIEF_REVISION.md
+ patch existant comme point de départ.
12 h 15 : révision terminée et appliquée (555 corrections de valeurs + 34 courants ; journal
data/revision/journal.json et Journal_revision_catalogue.xlsx). Refusée : marine-le-pen justice_elus
0→1 (motif fondé sur sa propre procédure). Version 16 publiée. Points d'échelle signalés par les
relecteurs (à traiter si souhaité) : Transition trop centrée sur le nucléaire ; Condition humaine mêle
eugénisme d'État et transhumanisme libertaire ; Secteurs stratégiques sans repère -2 ; Port d'armes et
acteurs armés non étatiques ; Intégration régionale pour les fédérations internes et les empires
antiques ; Immigration pour les États fermés dans les deux sens ; Structure familiale (échelle absolue
pour le présent, relative pour le passé).

## V9 : précision des échelles (lancée 29 octobre 2026, 12 h 20)
Points 1 à 6 retenus (transition, transhumanisme, strategique, europe, armes, immigration) ; point 7
(structure familiale, échelle absolue pour le passé) EN ATTENTE de la décision d'Alexandre.
axes.json et question transition-3 modifiés (reformulees clé 10, VERSION 10). Sauvegarde : sauvegardes/avant_v9/.
Consignes : data/BRIEF_V9.md ; tables data/revision/table_v9_*.txt ; patchs scratchpad/rev9/<a|b|c>/patch.json,
copiés dans data/revision/patchs_v9/ par build/sauvegarde_patchs.py. Agents : a a643206e096ce6f31
(transition, transhumanisme), b afdf52e237bf3d1fb (strategique), c a87aece92cc1d7f4b (europe, armes, immigration).
Ensuite : appliquer_patch.py, build, test, publication, excel.py.
12 h 50 : V9 terminée et publiée (Version 17). 957 corrections (a 125, b 368, c 135, b2 329) +
Royaume-Uni 2026 strategique -1. Repères strategique affinés (7 niveaux). Journal complet :
Journal_revision_catalogue.xlsx (1 546 lignes). Point 7 (structure familiale, passé en échelle absolue)
toujours en attente de décision.

## V10 (lancée 29 octobre 2026, 12 h 45) : structure familiale en échelle absolue + interface
Agents bioethique : lot 1 af4036017f9f30c1c, lot 2 ae6fca5201bdf0fd9 (BRIEF_V10.md, tables
table_v10_bioethique_*.txt, patchs scratchpad/rev10/<1|2>/patch.json → data/revision/patchs_v10/).
Interface (template) : mode « compléter » (uniquement les affirmations sans réponse), étoile dans
l'édition rapide des résultats, code de partage pour comparer avec un proche (section Comparer).
13 h 10 : V10 bioethique appliquée (315 corrections), Version 19 publiée avec l'interface (mode compléter, étoile, code de partage).
13 h 15 : Version 20, export PDF : repli universel (lien blob « Ouvrir ou enregistrer le PDF » + doc.save) quand l'enregistrement direct de claude.ai est refusé au visiteur.
14 h 25 : Version 21, PDF : jsPDF embarqué dans la page (build/vendor, injecté par build.py), panneau de repli avec lien, affichage intégré (iframe blob) et impression (@media print).
14 h 55 : PDF bloqué pour les visiteurs hors organisation (restriction claude.ai, accès « Lecteur »). Ajout : restauration des réponses par code (accueil) ; copie autonome « Atlas des convictions.html » envoyée à Alexandre. Version 22.

## Hébergement public (29 octobre 2026, 15 h)
Site : https://quizpolitiques.github.io/atlas-des-convictions/ (compte renommé Quizpolitiques le 29/10 à 15 h ; ancienne adresse ablanchard06000.github.io caduque) (GitHub Pages, branche main, racine).
Dépôt : Ablanchard06000/atlas-des-convictions, clone local /home/claude/atlas-des-convictions.
Publier une mise à jour : python3 build/build.py, puis cp atlas-des-convictions.html
/home/claude/atlas-des-convictions/index.html, commit, git push (l'application GitHub Claude est
installée sur le dépôt). Pages se déploie seul en une à deux minutes. Le lien claude.ai reste actif
(même fichier publié avec l'outil Artifact).
Note : dans cette session, le dépôt est rattaché sous l'ancien nom (Ablanchard06000/atlas-des-convictions, la redirection git fonctionne). Une nouvelle session devra rattacher Quizpolitiques/atlas-des-convictions.

## V11 (1er novembre 2026, 19 h 30) : désancrage France/UE des questions + redéfinition de `normes`
29 affirmations réécrites (work/rev11/pairs.py, appliqué) ; 10 reposées (reformulees clé 11) ;
VERSION 11 et note "11" en place. Axe normes : Ordre juridique supérieur ↔ Souveraineté juridique
de l'État. Sauvegarde : sauvegardes/avant_v11/. Relecteurs normes : lot 1 acc41768308a54270, lot 2
abf000c03d2ac59b8 (BRIEF_V11.md, patchs dans work/rev11/<1|2>/patch.json, écrits au fil de l'eau
directement dans le projet). Ensuite : appliquer_patch.py, build, excel.py, tests, publication
claude.ai + git push (dépôt cloné sous /home/claude/atlas-des-convictions, remote Ablanchard06000 redirigé).
V11 terminée et publiée (1er novembre) : 130 corrections normes appliquées, site GitHub + claude.ai version 24, Excel à jour.

## Grille Excel des positions (1er novembre 2026)
- `build/grille_excel.py` → `Grille_positions_catalogue.xlsx` (980 profils + 79 doctrines ; 8 grands thèmes en formules + 60 axes ; onglets Pondérations et Légende). Relancer après toute modification du catalogue (puis recalc LibreOffice).

## V12 — axe Fondement du droit (terminée, 1er novembre 2026)
- Axe `fondement` (61 axes, 305 affirmations), définition de `normes` précisée, VERSION 12. Sauvegarde : sauvegardes/avant_v12.
- Catalogue coté par 4 agents (brief data/BRIEF_V12.md ; patchs data/revision/patchs_v12/1-4.json, 1_normes.json pour 8 doctrines, harmonisation.json pour Vichy, Pétain, Laval, Franco et l'Espagne franquiste). 5 null (mercantilisme, Vercingétorix, Keynes, Clisthène, Carthage).
- Auto-reconnaissance 943/980. Publié : GitHub (commit c08115f) et claude.ai (version 26). Excel : Questions et Grille régénérés.
- Comparer avec un proche : encadré rouge toujours ouvert en tête de la rubrique Comparer + bouton « Comparer mes résultats avec un proche ↓ » sous le titre des résultats (commit 736f472, claude.ai version 27).
- 1er nov. 22h45 : code de partage imprimé dans le PDF (encadré rouge + lien du site) ; decodeAnswers ignore espaces et retours à la ligne ; historique du navigateur (pushState/popstate entre accueil, questionnaire, résultats) ; vue sauvegardée (rechargement → résultats) ; « Voir mes résultats » en bouton principal sur l'accueil ; débordement mobile corrigé (.wrap, .demo, select). PUBLICATION GITHUB : utiliser build/publier_github.sh (ajoute doctype, charset, viewport) puis commit/push. Commit 44cc21b, claude.ai version 28.

## V13 — axes Sélection des gouvernants et Égalité des statuts + passe anachronismes (terminée, 2 nov.)
- Axes `selection` (Institutions) et `statuts` (Société), 63 axes, 315 affirmations, VERSION 13. Sauvegarde sauvegardes/avant_v13.
- Patchs data/revision/patchs_v13 : 1-4.json (cotation), anachronismes.json (100 null + Turgot), harmonisation_statuts.json (70 : orientation sexuelle et identité de genre hors du champ de `statuts` → -3 ; mesures visant une religion, une origine ou les binationaux → -2).
- Auto-reconnaissance 944/980. Publié : commit 50408e4, claude.ai v30. Excel régénérés.

## V14 — élargissement géographique du catalogue (en cours, 1er nov. 23h30)
- Demande : ~400 profils + ~20 sociétés anciennes. Brief data/BRIEF_V14.md (63 axes, calibrage data/revision/reference_v14.txt, doublons data/revision/index_catalogue.txt).
- 10 agents, fichiers work/rev14/<lot>.json réécrits toutes les 4 entrées : amlat, afouest, afest, asiese, asiesud, euouest, euest, moyorient, oceanie, anciennes. Si interruption : relancer un agent par lot manquant avec le même prompt (il reprend là où le fichier s'arrête).
- Sauvegarde externe : build/sauvegarde_v14.sh (en arrière-plan) pousse work/rev14/*.json toutes les 5 min sur la branche GitHub `sauvegarde-v14` (worktree /home/claude/atlas-sauvegarde, dossier rev14/). Pour récupérer après perte du conteneur : cloner la branche sauvegarde-v14.
- Ensuite : contrôle des doublons inter-lots, validation (63 axes, ≥ 15 valeurs), calibrage croisé, intégration en data/catalogue/monde_16..25, build, review, publier_github.sh + push main, Artifact, Excel, puis supprimer la branche sauvegarde-v14.
