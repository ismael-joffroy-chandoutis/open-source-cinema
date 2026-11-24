# 15. Conserving films and artworks with open tools

[Back to the README](../README.md) · Previous: [14. ComfyUI, Wan2GP and Pinokio](14-comfyui-wan2gp-pinokio.md)

## What I built for my films

A finished film has to stay readable for decades. In August 2026 I published [self-hosted-film-lab](https://github.com/ismael-joffroy-chandoutis/self-hosted-film-lab) (MIT), to keep my finished films alive without renting that service back from a lab: the services of a lab rebuilt with free software. A catalogue, transcoding, DCPs, screeners, delivery, chain of custody and cold storage.

I tested it on real material, a 4K ProRes master and an SMPTE DCP:

- the 4K ProRes master (19.5 GB, 4 minutes) became an H.264 screener at twice real time;
- 60 seconds of 2K DCP were encoded to JPEG 2000 in 54 seconds on a 16-core CPU;
- the DCP passed two validators, DCP-o-matic's and ClairMeta;
- extracting one 2K frame from the DCP's MXF took about 0.7 seconds.

The chain of custody uses ASC MHL at every move, a monthly check of the checksums, a block-level scrub, and a cross-check with the cold copy. The rule I wrote in its documentation: "A backup job that has been silently failing for three months is indistinguishable from a working one unless something screams."

## Why artworks need the same tools

An artist's video, an installation or a net art piece has the same problem as a film, with more parts: the files, and also the software, the hardware and the instructions that make it play. The audiovisual part uses the same open formats and tools as the film archive in [chapter 08](08-delivery-and-archiving.md#open-formats-for-the-archive): FFV1 in Matroska, a checksum next to each file, a validator.

I haven't conserved an artwork with these tools yet. My studio page lists the conservation of digital artworks as a service to come, and this chapter is where its tools are documented first.

## The open tools of the field

Read at the source on 24 November 2026.

| Tool | What it does | Licence | Version | Group |
|---|---|---|---|---|
| [Archivematica](https://github.com/artefactual/archivematica) | Digital preservation system, following the OAIS model | AGPL-3.0 | 1.18.0, 26 September 2025 | Reliable, on my test list |
| [AtoM](https://github.com/artefactual/atom) | Archival description and access | AGPL-3.0 | 2.10.2, 24 August 2026 | Reliable, on my test list |
| [CollectiveAccess](https://github.com/CollectiveAccess/providence) | Cataloguing and publishing museum and archive collections | GPL-3.0 | 2.0.12, 8 November 2026 | Reliable, on my test list |
| [ResourceSpace](https://github.com/resourcespace/resourcespace) | Digital asset management | Open source per its site; exact licence not checked | No release on GitHub | What I have used (in self-hosted-film-lab) |
| [RAWcooked](https://github.com/MediaArea/RAWcooked) | DPX, TIFF or EXR sequences to lossless FFV1 in Matroska, and back bit for bit | BSD-2-Clause | 26.11, 18 November 2026 | Reliable, on my test list |
| [MediaConch](https://mediaarea.net/MediaConch) | Conformance and policy checker for preservation files (Matroska, LPCM, FFV1) | BSD-2-Clause | 25.04 | Reliable, on my test list |
| [MediaInfo](https://github.com/MediaArea/MediaInfo) | Technical data and tags of video and audio files | BSD-2-Clause | 26.10, 6 October 2026 | Reliable, on my test list |
| [bagit-python](https://github.com/LibraryOfCongress/bagit-python) | Packages files with checksums (BagIt, RFC 8493) | CC0, per its README | 1.9.0, 13 June 2025 | Reliable, on my test list |
| [ASC MHL](https://github.com/ascmitc/mhl) | Media hash lists, chain of custody | MIT | 1.2, 4 July 2025 | Reliable, on my test list |
| [ReplayWeb.page](https://github.com/webrecorder/replayweb.page) | Plays web archives in the browser (Webrecorder) | AGPL-3.0 | 2.5.5, 19 November 2026 | Reliable, on my test list |
| [Browsertrix Crawler](https://github.com/webrecorder/browsertrix-crawler) | Crawls websites into web archives (Webrecorder) | AGPL-3.0 | 1.15.4, 11 November 2026 | Reliable, on my test list |

Conifer, the web archiving service that Rhizome ran for born-digital art, stopped in June 2026, according to its own page.

## A reference

The Electronic Arts Intermix [Online Resource Guide for Exhibiting, Collecting & Preserving Media Art](https://www.eai.org/resourceguide/) covers single-channel video, computer-based art and media installation, with a preservation section created by IMAP. The page is dated 2006 to 2013: it is a starting point, not a current guide.

## The test I will do

One of my own pieces, an installation or a video work, packaged for the archive: the media to FFV1 with RAWcooked, checked with MediaConch, the software and the instructions in a BagIt package, the whole thing described in CollectiveAccess. **Measure:** can someone else play the piece again from the package alone, without me.

[Back to the README](../README.md) · Previous: [14. ComfyUI, Wan2GP and Pinokio](14-comfyui-wan2gp-pinokio.md)
