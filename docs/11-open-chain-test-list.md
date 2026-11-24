# 11. The open chain: test list

[Back to the README](../README.md) · Previous: [10. Previs, 3D and generated images](10-previs-3d-and-generated-images.md)

I want my next films to go as far as I can toward open tools only, from the first page to the cinema copy. Today four steps of my own chain are closed: the edit, the grade, the mix, and the photogrammetry and real-time render of Maalbeek (see [00. The whole chain](00-the-whole-chain.md)). This page lists the open tools I want to try for each step, how I will test them, and what I will measure.

None of these tests has been done yet. So every tool here is in the group **Reliable, on my test list** (reported to work by others or by its documentation) or **Not ready**. When a test is done, the tool moves to **What I have shot with**, with a link to the result.

Versions, licences and dates were read at the source on 24 November 2026. They change quickly: check the link before you rely on one.

## How I will test

The same rule for every step: one scene I have already finished in my usual chain, and the open tool has to give the same result, or I write down what is missing. A test is only done when the file comes out the other end and opens in the next tool.

For each test I write down: the version of the tool, the machine, the time it took, what broke, and what I had to do by hand.

## Writing

| Tool | Licence | Version | Group |
|---|---|---|---|
| [Story Architect](https://github.com/story-apps/starc) | GPL-3.0 for the core; some modules are proprietary and there is a paid version | 0.8.3 on 22 September 2026 ([blog](https://starc.app/blog)) | Reliable, on my test list |
| [Trelby](https://github.com/trelby/trelby) | GPL-2.0 | 2.4.16.2, 3 October 2025 | Reliable, on my test list |

KIT Scenarist, often listed for this, is stopped: its repository was archived in 2023 and its developer points to Story Architect.

**Test:** write one scene in each, export to Final Draft (FDX) and PDF, open the FDX again. **Measure:** what is lost in the round trip.

## Previs and storyboard

| Tool | Licence | Version | Group |
|---|---|---|---|
| [Blender](https://www.blender.org/download/) | GNU GPL | 5.3.0, 10 November 2026 | Reliable, on my test list |
| [Krita](https://krita.org/en/download/) | GPL-3 | 5.3.4.1 installers, 7 October 2026 | Reliable, on my test list |

Storyboarder has no licence declared in its repository and no commit since June 2022. I don't count it as open.

**Test:** a 3D previs of one scene in Blender, with the camera exported to [spritz](https://github.com/ismael-joffroy-chandoutis/spritz) (see [chapter 10](10-previs-3d-and-generated-images.md)), and a drawn storyboard of the same scene in Krita. **Measure:** time to a first animatic.

## Editing

| Tool | Licence | Version | Group |
|---|---|---|---|
| [Kdenlive](https://kdenlive.org/en/download/) | GPL-3.0 | 26.08.3 | Reliable, on my test list |
| [Shotcut](https://github.com/mltframework/shotcut) | GPL-3.0 | 26.11.15, 16 November 2026 | Reliable, on my test list |
| Blender video sequencer | GNU GPL | in Blender 5.3.0 | Reliable, on my test list |
| [Olive](https://github.com/olive-editor/olive) | GPL-3.0 | alpha; last commit 5 December 2024 | Not ready |

**Test:** the offline edit of one scene on the H.264 proxies, then the conform on the RAW, the way I do it in Final Cut Pro (see [chapter 04](04-offline-online-conform-and-grading.md)). **Measure:** does the timeline open on the RAW at the exact frame; how responsive the timeline is with a full day of rushes.

## Timeline exchange

| Tool | Licence | Version | Group |
|---|---|---|---|
| [OpenTimelineIO](https://github.com/AcademySoftwareFoundation/OpenTimelineIO) | Apache-2.0 | 0.18.1 (marked pre-release on GitHub) | Reliable, on my test list |

OpenTimelineIO is the open format for moving an edit between tools. Blender 5.3 announces an initial import and export.

**Test:** the same edit from Final Cut Pro to Kdenlive, to Blender and to Resolve through OpenTimelineIO. **Measure:** cuts on the right frame, titles, sound, and the paths to the media.

## Grading

This is the weakest step of the open chain. I haven't found an open tool that has, together, colour wheels, masks, tracking, scopes, ACES, conform from an edit, a monitor output and control surfaces, like DaVinci Resolve.

| Tool | Licence | Version | Group |
|---|---|---|---|
| [vkdt](https://github.com/hanatos/vkdt) | BSD-2-Clause, a few files GPLv3 | 1.0.0, 13 December 2025 | Reliable, on my test list |
| Blender (colour management and compositor) | GNU GPL | 5.3.0 | Reliable, on my test list |
| [Natron](https://github.com/NatronGitHub/Natron) | GPL-2.0 | 2.5.0, 25 November 2022; a 2.6.0 is announced | Not ready |

vkdt reads MLV files natively and processes them on the GPU (see [chapter 03](03-raw-post-processing.md#vkdt)). Natron is a node compositor and has had no stable release since 2022, although its repository is active again.

**Test:** grade one ML RAW scene in vkdt, and the same scene in Blender with ACES, next to my Resolve grade. **Measure:** how close I get to the Resolve grade, and in how much time.

## 3D, photogrammetry and splats

| Tool | Licence | Version | Group |
|---|---|---|---|
| [COLMAP](https://github.com/colmap/colmap) | BSD | 4.2.1, 29 September 2026 | Reliable, on my test list |
| [Meshroom](https://github.com/alicevision/Meshroom) | MPL-2.0 | 2025.1.0, 19 August 2025 | Reliable, on my test list |
| [OpenSplat](https://github.com/pierotofy/OpenSplat) | AGPL-3.0 | 1.2.2, 16 September 2026 | Reliable, on my test list |
| Blender, Gaussian splat import | GNU GPL | 5.3.0 | Reliable, on my test list |
| [Godot](https://github.com/godotengine/godot) | MIT | 4.7.2, 18 August 2026 | Reliable, on my test list |

Postshot, which I listed in [chapter 01](01-maalbeek-photogrammetry.md), is proprietary. Blender 5.3 imports splats but doesn't export them, so there is no round trip between Blender and a real-time engine for splats yet.

**Test:** the Maalbeek method again on a new place: a RAW video long take, frames exported as CinemaDNG, camera poses in COLMAP, then a point cloud in Meshroom and splats with OpenSplat, rendered in Blender and in Godot. **Measure:** the same as for Maalbeek, how faithful the result is, on reflective surfaces too, next to what Metashape gave.

## Sound

| Tool | Licence | Version | Group |
|---|---|---|---|
| [Ardour](https://ardour.org/) | GPL v2 | 9.8, 23 August 2026; the home page announces 9.10 | Reliable, on my test list |

Ardour is the open multitrack station I want to test against Pro Tools, where the sound of a 30-minute documentary shot in ML RAW was edited and mixed (see [chapter 04](04-offline-online-conform-and-grading.md)). Audacity edits audio files; it isn't a multitrack mixing station for a film. REAPER isn't open.

**Test:** edit and mix the sound of one scene in Ardour, stems and a 5.1 mix. **Measure:** the import of the edit with its sound, the export of the stems for the DCP.

## Subtitles

| Tool | Licence | Version | Group |
|---|---|---|---|
| [Subtitle Edit](https://github.com/SubtitleEdit/subtitleedit) | MIT | 5.4.0, 6 November 2026 | Reliable, on my test list |

**Test:** subtitles of one scene, exported for DCP-o-matic. **Measure:** do they play correctly in the DCP.

## Cinema copy

| Tool | Licence | Version | Group |
|---|---|---|---|
| [DCP-o-matic](https://dcpomatic.com/download) | GPL-2.0 | 2.18.52, 21 November 2026 | Reliable, on my test list |

DCP-o-matic is in [chapter 08](08-delivery-and-archiving.md). It makes SMPTE and Interop DCPs and KDMs, and checks the package. I haven't found that it creates HDR or Dolby Vision DCPs. Its author doesn't recommend its player for commercial screenings without tests.

**Test:** a DCP of a short film from a master that went through the open chain only. **Measure:** the two validators, then a screening in a cinema.

## Archive

| Tool | Licence | Version | Group |
|---|---|---|---|
| [RAWcooked](https://github.com/MediaArea/RAWcooked) | BSD-2-Clause | 26.11, 18 November 2026 | Reliable, on my test list |
| [FFmpeg](https://ffmpeg.org/download.html) (FFV1, Matroska) | LGPL 2.1 or later, some parts GPL | 9.1, 20 November 2026 | Reliable, on my test list |

RAWcooked turns DPX sequences and WAV files into FFV1 in Matroska, and can give back the original files. The BFI National Archive presented its use of it in February 2023.

**Test:** the master of one film to FFV1 with RAWcooked, then back to the original sequence. **Measure:** checksums identical to the original, and the space saved.

## Review

| Tool | Licence | Version | Group |
|---|---|---|---|
| [Open RV](https://github.com/AcademySoftwareFoundation/OpenRV) | Apache-2.0 | 4.1.0, 20 November 2026 | Reliable, on my test list |
| [mrv2](https://github.com/ggarra13/mrv2) | BSD-3 | 1.8.6, 17 November 2026 | Reliable, on my test list |

**Test:** play back the EXR and the master of one scene, compare two versions side by side. **Measure:** real-time playback at full resolution on my machine.

## What I don't put on this list

The image and video generation models. Their licences are written by each publisher, often with limits on who can use them and for what, and the models change every month. My benches and the licences as the publishers write them are in [ai-upscaler-benchmark](https://github.com/ismael-joffroy-chandoutis/ai-upscaler-benchmark), [vlm-shot-labeling-2026](https://github.com/ismael-joffroy-chandoutis/vlm-shot-labeling-2026) and [modeles-ia-cinema-2026](https://github.com/ismael-joffroy-chandoutis/modeles-ia-cinema-2026).

[Back to the README](../README.md) · Previous: [10. Previs, 3D and generated images](10-previs-3d-and-generated-images.md)
