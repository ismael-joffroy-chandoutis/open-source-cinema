<picture><source media="(prefers-color-scheme: dark)" srcset="banner.svg"><img src="banner-light.svg" alt="Open Source Cinema" width="100%"></picture>

**English** · [Français](README.fr.md)

<div align="center">

# Open Source Cinema

**RAW video with Magic Lantern on the Canon 5D Mark III, and post-production with open tools.**

[![License: CC BY-NC-ND 4.0](https://img.shields.io/badge/License-CC_BY--NC--ND_4.0-lightgrey.svg)](https://creativecommons.org/licenses/by-nc-nd/4.0/)
![Magic Lantern](https://img.shields.io/badge/Magic_Lantern-RAW-cc0000?style=flat-square)
![Canon 5D III](https://img.shields.io/badge/Canon-5D_Mark_III-black?style=flat-square&logo=canon&logoColor=white)
![DaVinci Resolve](https://img.shields.io/badge/DaVinci-Resolve-3388FF?style=flat-square&logo=davinciresolve&logoColor=white)
![MLV App](https://img.shields.io/badge/MLV_App-Open_Source-green?style=flat-square)
![CinemaDNG](https://img.shields.io/badge/Format-CinemaDNG-purple?style=flat-square)

</div>

## Who I am

I'm Ismaël Joffroy Chandoutis, a filmmaker and artist based in Paris; my films move between documentary, fiction and animation. [Maalbeek](https://en.unifrance.org/movie/50347/maalbeek) (2020) premiered at the Semaine de la Critique in Cannes, won the Prix André-Martin at Annecy in 2021 and the César for Best Documentary Short Film in 2022. Swatted (2018, Le Fresnoy) received an honorary mention at Ars Electronica in 2019 and qualified for the Academy Awards. [Ondes Noires](https://en.unifrance.org/movie/45236/dark-waves) (2017) won the Grand Prix in Regensburg.

<img src="monde.jpg" alt="open-source-cinema" width="100%">

## What this repository is

I have shot RAW video with Magic Lantern on the Canon 5D Mark III since 2013, when RAW video arrived on this camera. This repository documents how I work with it: the camera, the cards, the proxy recorded with the RAW, the conform from the offline edit, the grade, and the delivery. It also documents how the point clouds of Maalbeek were made from RAW video long takes. Parts of Ondes Noires were shot in Magic Lantern RAW as well, and cut together with Blackmagic and RED Dragon footage.

I don't write code. On the Magic Lantern forum, where I post as [12georgiadis](https://www.magiclantern.fm/forum/index.php?action=profile;u=24232), I test builds, report problems and ask for what a professional edit needs. Between 2013 and 2022 I wrote 213 messages in 37 threads, most of them in 2017 and 2018. The links to these messages are in the chapters, next to what they show.

Every mode and tool in the chapters is in one of three groups:

- **What I have shot with**: used on a real shoot.
- **Reliable, on my test list**: reported to work by others or by the code, not yet used by me on a film.
- **Not ready**: exists, but not usable on a shoot today.

Figures are linked to their source, or marked as my own estimate.

![The chain, from the sensor to the delivery](schemas/01-chain-overview.svg)

## Chapters

| # | Chapter | What is in it |
|---|---|---|
| 01 | [Maalbeek: point clouds from RAW video long takes](docs/01-maalbeek-photogrammetry.md) | How the scans of Maalbeek were shot in RAW video and turned into point clouds |
| 02 | [Magic Lantern on the 5D Mark III](docs/02-magic-lantern-5d-mark-iii.md) | Builds, sensor readout, modes and data rates, cards, the H.264 proxy, preview and HDMI, Dual ISO, the 7D and the EOS M |
| 03 | [RAW post-processing](docs/03-raw-post-processing.md) | MLV App and the other tools to develop the RAW |
| 04 | [Offline, online conform and grading](docs/04-offline-online-conform-and-grading.md) | Edit on the proxies, conform on the RAW, grade in Resolve |
| 05 | [Film looks and restoration](docs/05-film-looks-and-restoration.md) | Film emulation and restoration with open tools |
| 06 | [Outlook and test list](docs/06-outlook-and-test-list.md) | The state of Magic Lantern in November 2026 and the tests I still have to do |
| 07 | [AXIOM and open cinema](docs/07-axiom-and-open-cinema.md) | The open hardware cinema camera and where it stands |
| 08 | [Delivery and archiving](docs/08-delivery-and-archiving.md) | DCP, masters and open archive formats |

![Proxy and conform](schemas/04-proxy-and-conform.svg)

## What changed in November 2026

The repository was rewritten in November 2026. The old README was one long page; it is now split into the chapters above. Main changes:

- Maalbeek has its own chapter. The old README named the César for Maalbeek but said nothing about how the 5D Mark III was used for the film.
- Figures are sourced or marked. The Dual ISO dynamic range figures are my own estimates and are now written as such. Data rates are calculated and the formula is given.
- The 3:2 mode is corrected. At 1920 wide it is 1920x1280. The old README wrote 1920x1200, a size the Magic Lantern menu doesn't offer. Continuous recording on the CF card alone and clean HDMI output in this mode are not confirmed, and are on the test list.
- The H.264 proxy has a full section, with my tests from 2017, the limits in the code and the firmware question.
- My forum activity is described by what the messages show, with a link to each message. I test, report and ask; I don't develop.
- Builds and tools are updated: Danne's release of 7 June 2025, the one official Magic Lantern release since the team came back, MLV App 1.16, and the new tools that mount MLV files for Resolve.
- Out-of-date parts were removed, such as my hardware list of February 2026.
- Six diagrams were added in [schemas/](schemas/).

## Cited by CineD

In November 2026, Nino Leitner wrote about this repository in [Magic Lantern for Canon DSLRs in 2026](https://www.cined.com/magic-lantern-canon-2026-raw-video-film-roll-soup-engine-m-film) on CineD. He wrote that the Dual ISO dynamic range figures were my own estimates, and he was right. They are now marked that way.

## Editing with agents

I edit in Final Cut Pro driven by agents through [SpliceKit](https://github.com/elliotttate/SpliceKit), an MCP server, and in DaVinci Resolve Studio, which has come with its own MCP server since [version 21.1](https://www.blackmagicdesign.com/media/partial/release/20260908-03). I'm also building my own editing software, designed for AI and agents from the start, around two actions: cut and generate.

## Other documents in this repository

| Document | What it is |
|---|---|
| [ML RAW Workflows: DaVinci Resolve & Final Cut Pro](ML-RAW-Workflows-Resolve-FCP.md) | The longer workflow guide: CinemaDNG in Resolve, node trees, multi-camera matching, DCP and IMF, FCP round trip |
| [Agent-Driven Editing](Agent-Driven-Editing-2026.md) | AI agents controlling editing software, MCP servers for Resolve and Final Cut Pro, OpenTimelineIO (February 2026) |
| [Generative Pipeline: March 2026](Generative-Pipeline-March-2026.md) | Follow-up to the agent document: generative video and audio pipelines (March 2026) |
| [The Film Comes First](Strategy-Film-First.md) | Why the film has to come before the pipeline (March 2026) |
| [Le montage en 2036](Editing-2036.fr.md) | Essay in French, follow-up to the agent document, revised six months later |
| [L'auteur est celui qui arrête](L-auteur-est-celui-qui-arrete.fr.md) | Essay in French: notes on the cut, written when video generation became faster than real time (August 2026) |

The four English documents are dated and describe the state of things at that date.

## How to cite

Use the metadata in [CITATION.cff](CITATION.cff). GitHub shows a "Cite this repository" button from it. In text:

> Joffroy Chandoutis, Ismaël. *Open Source Cinema.* GitHub repository, 2026. https://github.com/ismael-joffroy-chandoutis/open-source-cinema

When you quote a figure, please quote the chapter it comes from and say if it is marked as my own estimate.

## License

This documentation is released under [CC BY-NC-ND 4.0](https://creativecommons.org/licenses/by-nc-nd/4.0/). Full terms in [LICENSE.md](LICENSE.md).

The tools described are under their own licenses, for example:

- [Magic Lantern](https://github.com/reticulatedpines/magiclantern_simplified): GPL v2
- [MLV App](https://github.com/ilia3101/MLV-App): GPL v3
- [AXIOM / apertus](https://github.com/apertus-open-source-cinema): GPL v3 (software), CERN OHL (hardware)

By [Ismaël Joffroy Chandoutis](https://ismaeljoffroychandoutis.com).
