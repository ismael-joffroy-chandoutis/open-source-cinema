<picture><source media="(prefers-color-scheme: dark)" srcset="banner.svg"><img src="banner-light.svg" alt="Open Source Cinema" width="100%"></picture>

[English](README.md) · **Français**

<div align="center">

# Open Source Cinema

**Faire un film de l'écriture à l'archive avec des outils libres, à bas coût, et où en est chaque étape.**

[![License: CC BY-NC-ND 4.0](https://img.shields.io/badge/License-CC_BY--NC--ND_4.0-lightgrey.svg)](https://creativecommons.org/licenses/by-nc-nd/4.0/)
![Magic Lantern](https://img.shields.io/badge/Magic_Lantern-RAW-cc0000?style=flat-square)
![MLV App](https://img.shields.io/badge/MLV_App-GPL--3.0-green?style=flat-square)
![DCP-o-matic](https://img.shields.io/badge/DCP--o--matic-GPL--2.0-green?style=flat-square)
![Blender](https://img.shields.io/badge/Blender-GPL-orange?style=flat-square&logo=blender&logoColor=white)
![Ardour](https://img.shields.io/badge/Ardour-GPL--2.0-green?style=flat-square)

</div>

## Ce qu'est ce dépôt

J'ai tourné en vidéo RAW sur un Canon 5D Mark III avec Magic Lantern, un firmware libre, à partir de 2013 : un long métrage documentaire en Inde en 2017, les scans de Maalbeek en 2019, des parties d'Ondes Noires. Aujourd'hui, un boîtier d'occasion se vend entre 249 et 489 € ([MPB France](https://www.mpb.com/fr-fr/produit/canon-eos-5d-mark-iii), 98 boîtiers en vente le 24 novembre 2026), et le firmware ne coûte rien.

Je cherche ici jusqu'où le reste du film peut aller de la même façon, de l'écriture à la copie de projection et à l'archive. Il suit les étapes d'un film dans l'ordre. Pour chacune, il dit ce que j'ai fait, avec quel outil, ce que ça coûte, et ce qu'il me reste à essayer. La caméra, Magic Lantern sur le 5D Mark III, est l'une de ces étapes.

Chaque outil des chapitres est rangé dans un de ces trois groupes :

- **Ce avec quoi j'ai tourné** : utilisé sur un vrai tournage.
- **Fiable, sur ma liste d'essais** : d'autres le font marcher ou le code le permet, je ne l'ai pas encore utilisé sur un film.
- **Pas prêt** : ça existe, mais on ne peut pas tourner avec aujourd'hui.

Les chiffres renvoient à leur source, ou sont signalés comme mes propres estimations. Un coût n'est donné que si j'ai trouvé un prix daté ; les outils libres se téléchargent gratuitement, sauf si la ligne dit autre chose.

## La chaîne, étape par étape

Les chapitres sont en anglais.

| Étape | Outil libre, et où il en est | Outil fermé utilisé sur mes films | Coût de la voie libre | Chapitres |
|---|---|---|---|---|
| Écriture | Story Architect et Trelby : sur ma liste d'essais | | Licences libres ; Story Architect a aussi une version payante | [11](docs/11-open-chain-test-list.md) |
| Prévisualisation et storyboard | Blender et Krita : sur ma liste d'essais ; un décor pour plans générés, construit dans Blender : pas prêt | | Gratuit | [10](docs/10-previs-3d-and-generated-images.md), [11](docs/11-open-chain-test-list.md) |
| Caméra | Magic Lantern sur le 5D Mark III : j'ai tourné avec, à partir de 2013. AXIOM Beta, la caméra en matériel ouvert : pas prête | | Boîtier 5D Mark III d'occasion : 249 à 489 € (MPB France, 24 novembre 2026). Firmware : gratuit. AXIOM Beta Developer Kit : 3 990 € HT ([apertus°](https://www.apertus.org/pricelist.html), novembre 2026) | [02](docs/02-magic-lantern-5d-mark-iii.md), [06](docs/06-outlook-and-test-list.md), [07](docs/07-axiom-and-open-cinema.md) |
| Données du tournage | rsync (Inde, 2017), xxHash et rclone : utilisés sur mes films. ASC MHL : sur ma liste d'essais | | Gratuit | [09](docs/09-on-set-data.md) |
| Développement du RAW | MLV App : utilisé sur mes films. Les nouveaux outils qui montent les fichiers MLV pour Resolve et Final Cut Pro : sur ma liste d'essais | | Gratuit | [03](docs/03-raw-post-processing.md), [13](docs/13-formats.md) |
| Montage | Kdenlive, Shotcut, le séquenceur de Blender, OpenTimelineIO pour l'échange : sur ma liste d'essais | Final Cut Pro | Gratuit | [04](docs/04-offline-online-conform-and-grading.md), [11](docs/11-open-chain-test-list.md) |
| Étalonnage | vkdt et Blender : sur ma liste d'essais. L'étape où je n'ai pas trouvé d'outil libre au niveau dont j'ai besoin | DaVinci Resolve | Gratuit | [04](docs/04-offline-online-conform-and-grading.md), [05](docs/05-film-looks-and-restoration.md), [11](docs/11-open-chain-test-list.md) |
| Son et mixage | Ardour : sur ma liste d'essais | Pro Tools (mixage d'un documentaire de 30 minutes, 2017) | Le code source d'Ardour est gratuit ; les versions prêtes à installer sur [ardour.org](https://ardour.org/download.html) sont payantes | [12](docs/12-sound-and-mixing.md) |
| 3D, photogrammétrie, splats | COLMAP, Meshroom, OpenSplat, Blender et Godot : sur ma liste d'essais | Metashape et Unity (Maalbeek) | Gratuit | [01](docs/01-maalbeek-photogrammetry.md), [10](docs/10-previs-3d-and-generated-images.md), [11](docs/11-open-chain-test-list.md) |
| Effets, compositing et animation | Le compositeur de Blender : sur ma liste d'essais. Natron : pas prêt | EbSynth (Maalbeek, 2020 : une version bêta essayée sur le film, avec des retours à ses développeurs) | Gratuit | [01](docs/01-maalbeek-photogrammetry.md), [11](docs/11-open-chain-test-list.md) |
| Images générées | ComfyUI : installé et mesuré sur mes machines en 2026. Les modèles sont à poids ouverts, ce qui n'est pas de l'open source | | Logiciel gratuit ; il faut une carte graphique | [10](docs/10-previs-3d-and-generated-images.md), [14](docs/14-comfyui-wan2gp-pinokio.md) |
| Sous-titres | Subtitle Edit : sur ma liste d'essais | | Gratuit | [11](docs/11-open-chain-test-list.md) |
| Copie de projection (DCP) | DCP-o-matic : utilisé sur mes films, depuis 2017 | | Gratuit | [08](docs/08-delivery-and-archiving.md) |
| Archive et conservation | RAWcooked, FFmpeg avec FFV1 et Matroska : sur ma liste d'essais | | Gratuit | [08](docs/08-delivery-and-archiving.md), [15](docs/15-conserving-artworks.md) |

Trois chapitres traversent toutes les étapes : [00. La chaîne entière](docs/00-the-whole-chain.md), la carte de mes dépôts étape par étape ; [11. La chaîne libre : liste d'essais](docs/11-open-chain-test-list.md), comment j'essaierai chaque outil et ce que je mesurerai ; [13. Formats](docs/13-formats.md), les formats ouverts et la façon dont les logiciels libres lisent les formats fermés.

![La chaîne, du capteur à la livraison](schemas/01-chain-overview.svg)

## Chapitres

| # | Chapitre | Ce qu'il contient |
|---|---|---|
| 00 | [La chaîne entière](docs/00-the-whole-chain.md) | Chaque étape d'un film, ce que j'y ai fait, et le dépôt ou le chapitre qui le documente |
| 01 | [Maalbeek : des nuages de points à partir de plans-séquences en vidéo RAW](docs/01-maalbeek-photogrammetry.md) | Comment les scans de Maalbeek ont été tournés en vidéo RAW puis transformés en nuages de points |
| 02 | [Magic Lantern sur le 5D Mark III](docs/02-magic-lantern-5d-mark-iii.md) | Builds, lecture du capteur, modes et débits, cartes, proxy H.264, aperçu et HDMI, Dual ISO, le 7D et l'EOS M |
| 03 | [Post-traitement du RAW](docs/03-raw-post-processing.md) | MLV App et les autres outils pour développer le RAW |
| 04 | [Offline, conformation et étalonnage](docs/04-offline-online-conform-and-grading.md) | Monter sur les proxys, conformer sur le RAW, étalonner dans Resolve |
| 05 | [Rendus pellicule et restauration](docs/05-film-looks-and-restoration.md) | Émulation de pellicule et restauration avec des outils libres |
| 06 | [Perspectives et liste d'essais](docs/06-outlook-and-test-list.md) | L'état de Magic Lantern en novembre 2026 et les essais de caméra qu'il me reste à faire |
| 07 | [AXIOM et le cinéma ouvert](docs/07-axiom-and-open-cinema.md) | La caméra de cinéma en matériel ouvert et où elle en est |
| 08 | [Livraison et archivage](docs/08-delivery-and-archiving.md) | DCP, masters et formats d'archive ouverts |
| 09 | [Les données du tournage](docs/09-on-set-data.md) | Copier et vérifier les rushes, de l'Inde en 2017 à mon protocole de sauvegarde |
| 10 | [Prévisualisation, 3D et images générées](docs/10-previs-3d-and-generated-images.md) | De Maalbeek à Blender, les outils que j'ai construits, les bancs que j'ai mesurés |
| 11 | [La chaîne libre : liste d'essais](docs/11-open-chain-test-list.md) | Les outils libres à essayer à chaque étape, le protocole et ce que je mesurerai |
| 12 | [Son et mixage](docs/12-sound-and-mixing.md) | Ce que j'ai fait du son, Ardour, et l'essai de mixage à faire |
| 13 | [Formats](docs/13-formats.md) | Les formats ouverts de la chaîne, le MLV dans Resolve et Final Cut Pro, les formats fermés et comment les logiciels libres les lisent |
| 14 | [ComfyUI, Wan2GP et Pinokio](docs/14-comfyui-wan2gp-pinokio.md) | Ce que j'ai installé, construit et mesuré en 2026 |
| 15 | [Conserver les films et les œuvres](docs/15-conserving-artworks.md) | self-hosted-film-lab, et les outils libres de la conservation des œuvres à médias |

Les chapitres gardent leur numéro, pour que les liens vers eux continuent de marcher. Le tableau du haut donne l'ordre de la chaîne.

## Qui je suis

Je suis Ismaël Joffroy Chandoutis, cinéaste et artiste, et je vis à Paris. Je fais des films entre documentaire, fiction et animation. [Maalbeek](https://en.unifrance.org/movie/50347/maalbeek) (2020) a été présenté en première à la Semaine de la Critique à Cannes, il a reçu le Prix André-Martin à Annecy en 2021 et le César du meilleur court métrage documentaire en 2022. Swatted (2018, Le Fresnoy) a reçu une mention d'honneur à Ars Electronica en 2019 et s'est qualifié pour les Oscars. [Ondes Noires](https://en.unifrance.org/movie/45236/dark-waves) (2017) a remporté le Grand Prix à Regensburg.

<img src="monde.jpg" alt="open-source-cinema" width="100%">

Je n'écris pas de code. Sur le forum de Magic Lantern, où je poste sous le nom de [12georgiadis](https://www.magiclantern.fm/forum/index.php?action=profile;u=24232), je teste les builds, je signale les problèmes et je demande ce dont un montage professionnel a besoin. Entre 2013 et 2022 j'y ai écrit 213 messages dans 37 fils, la plupart en 2017 et 2018. Les liens vers ces messages sont dans les chapitres, à côté de ce qu'ils montrent. J'ai aussi testé une version bêta d'EbSynth, un outil fermé, pour le rendu 8K de Maalbeek ([chapitre 01](docs/01-maalbeek-photogrammetry.md)), et en 2020 j'ai écrit pour Fastvideo le cahier des charges d'un encodeur JPEG 2000 sur carte graphique pour le DCP ([chapitre 08](docs/08-delivery-and-archiving.md)).

![Proxy et conformation](schemas/04-proxy-and-conform.svg)

## Monter avec des agents

Je monte dans Final Cut Pro piloté par des agents grâce à [SpliceKit](https://github.com/elliotttate/SpliceKit), un serveur MCP, et dans DaVinci Resolve Studio, qui embarque son propre serveur MCP depuis la [version 21.1](https://www.blackmagicdesign.com/media/partial/release/20260908-03). Je construis aussi mon propre logiciel de montage, pensé dès le départ pour l'IA et les agents, autour de deux gestes : couper et générer.

## Cité par CineD

En novembre 2026, Nino Leitner a parlé de ce dépôt dans [Magic Lantern for Canon DSLRs in 2026](https://www.cined.com/magic-lantern-canon-2026-raw-video-film-roll-soup-engine-m-film), sur CineD. Il y écrit que les chiffres de dynamique du Dual ISO étaient mes propres estimations, et il avait raison. Ils sont maintenant signalés comme tels.

## Ce qui a changé en novembre 2026

Le dépôt a été réécrit en novembre 2026. Il était une longue page sur la vidéo RAW avec Magic Lantern ; il suit maintenant les étapes d'un film dans l'ordre. Les principaux changements :

- Le dépôt va maintenant de l'écriture à l'archive : écriture, prévisualisation, données du tournage, montage, étalonnage, son, 3D, effets et animation, images générées, sous-titres, DCP, archive et conservation des œuvres. Pour la plupart de ces étapes, c'est une liste d'essais : je n'y ai pas encore utilisé d'outil libre sur un film.
- Maalbeek a son propre chapitre. L'ancien README citait le César de Maalbeek sans rien dire de l'usage du 5D Mark III sur le film.
- Les chiffres ont une source ou sont signalés. Les chiffres de dynamique du Dual ISO sont mes propres estimations, et c'est maintenant écrit. Les débits sont calculés, et la formule est donnée.
- Le mode 3:2 est corrigé. À 1920 de large, c'est du 1920x1280. L'ancien README écrivait 1920x1200, une taille que le menu de Magic Lantern ne propose pas. L'enregistrement continu sur la carte CF seule et la sortie HDMI propre dans ce mode restent à confirmer : ils sont sur la liste d'essais.
- Le proxy H.264 a une section entière, avec mes essais de 2017, les limites inscrites dans le code et la question du firmware.
- Mon activité sur le forum est décrite par ce que montrent les messages, avec un lien vers chacun. Je teste, je signale et je demande. Le code, ce sont les développeurs du projet qui l'écrivent.
- Les builds et les outils sont à jour : la version de Danne du 7 juin 2025, la seule version officielle de Magic Lantern depuis le retour de l'équipe, MLV App 1.16, et les nouveaux outils qui montent les fichiers MLV pour Resolve.
- Les parties périmées ont été retirées, comme ma liste de matériel de février 2026.
- Six schémas ont été ajoutés dans [schemas/](schemas/).

## Autres documents de ce dépôt

| Document | Ce que c'est |
|---|---|
| [ML RAW Workflows: DaVinci Resolve & Final Cut Pro](ML-RAW-Workflows-Resolve-FCP.md) | Le guide de workflow, plus long : CinemaDNG dans Resolve, arbres de nœuds, raccord entre caméras, DCP et IMF, aller-retour avec Final Cut Pro |
| [Agent-Driven Editing](Agent-Driven-Editing-2026.md) | Des agents IA qui pilotent les logiciels de montage, les serveurs MCP pour Resolve et Final Cut Pro, OpenTimelineIO (février 2026) |
| [Generative Pipeline: March 2026](Generative-Pipeline-March-2026.md) | La suite du document sur les agents : chaînes de génération vidéo et audio (mars 2026) |
| [The Film Comes First](Strategy-Film-First.md) | Pourquoi le film doit passer avant la chaîne technique (mars 2026) |
| [Le montage en 2036](Editing-2036.fr.md) | Essai en français, suite du document sur les agents, révisé six mois plus tard |
| [L'auteur est celui qui arrête](L-auteur-est-celui-qui-arrete.fr.md) | Essai en français : notes sur la coupe, écrites quand la génération vidéo est devenue plus rapide que le temps réel (août 2026) |

Les quatre documents en anglais sont datés et décrivent l'état des choses à cette date.

## Comment citer

Les métadonnées sont dans [CITATION.cff](CITATION.cff). GitHub en tire un bouton « Cite this repository ». Dans un texte :

> Joffroy Chandoutis, Ismaël. *Open Source Cinema.* GitHub repository, 2026. https://github.com/ismael-joffroy-chandoutis/open-source-cinema

Si vous citez un chiffre, merci de citer le chapitre d'où il vient et de dire s'il est signalé comme mon estimation.

## Licence

Cette documentation est publiée sous licence [CC BY-NC-ND 4.0](https://creativecommons.org/licenses/by-nc-nd/4.0/). Le texte complet est dans [LICENSE.md](LICENSE.md).

Les outils décrits ont chacun leur licence, par exemple :

- [Magic Lantern](https://github.com/reticulatedpines/magiclantern_simplified) : GPL v2
- [MLV App](https://github.com/ilia3101/MLV-App) : GPL v3
- [DCP-o-matic](https://dcpomatic.com/) : GPL v2
- [Ardour](https://ardour.org/) : GPL v2
- [Blender](https://www.blender.org/) : GNU GPL
- [AXIOM / apertus](https://github.com/apertus-open-source-cinema) : GPL v3 (logiciel), CERN OHL (matériel)

Par [Ismaël Joffroy Chandoutis](https://ismaeljoffroychandoutis.com).
