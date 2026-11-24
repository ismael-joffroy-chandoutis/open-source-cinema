# 13. Formats: open, closed, and how open tools read them

[Back to the README](../README.md) · Previous: [12. Sound and mixing](12-sound-and-mixing.md) · Next: [14. ComfyUI, Wan2GP and Pinokio](14-comfyui-wan2gp-pinokio.md)

## The formats of an open chain

The file format decides which tools can open a shot, today and in thirty years. In my chain, these formats have a public specification:

| Step | Format | Who publishes it | Licence or terms |
|---|---|---|---|
| Camera | MLV, the Magic Lantern Video file | The Magic Lantern team, in the header file [`mlv.h`](https://github.com/reticulatedpines/magiclantern_simplified/blob/dev/modules/raw_video/mlv_rec/mlv.h) of the source code (format version 2.0) | GPL-2.0 or later |
| Developed RAW | DNG and CinemaDNG sequences | Adobe: [DNG specification 1.7.1.0](https://helpx.adobe.com/camera-raw/digital-negative.html), September 2023 | Royalty-free patent licence from Adobe, to read and write DNG files |
| VFX, 3D, generated frames | OpenEXR | Academy Software Foundation, [version 3.5.5](https://github.com/AcademySoftwareFoundation/openexr), 23 November 2026 | BSD-3-Clause |
| Colour | ACES | Academy Software Foundation, [ACES 2.0](https://github.com/aces-aswf/aces), released 4 April 2025 | Apache-2.0 |
| Archive | FFV1 in Matroska | IETF, RFC 9043 and RFC 9559 (see [chapter 08](08-delivery-and-archiving.md#open-formats-for-the-archive)) | Open specifications |
| Cinema copy | DCP: JPEG 2000 and PCM sound in MXF | SMPTE standards | Read and written by [DCP-o-matic](08-delivery-and-archiving.md#dcp-with-dcp-o-matic), GPL-2.0 |

Adobe's patent licence for DNG asks that any program that reads or writes DNG shows this sentence in its source code and documentation: "This product includes DNG technology under license by Adobe."

## Which open tools read MLV

| Tool | Licence | What it does with MLV |
|---|---|---|
| [MLV App](https://github.com/ilia3101/MLV-App) | GPL-3.0 | Develops the RAW, exports CinemaDNG and ProRes (see [chapter 03](03-raw-post-processing.md#mlv-app)) |
| [vkdt](https://github.com/hanatos/vkdt) | BSD-2-Clause, a few files GPLv3 | Reads MLV natively (`i-mlv` module, code taken from MLV App) and processes it on the GPU |
| [FFmpeg](https://ffmpeg.org/) | LGPL 2.1 or later | Has an MLV demuxer (`libavformat/mlvdec.c`) |

## MLV in Resolve and Final Cut Pro

I edit in Final Cut Pro and grade in Resolve, and neither reads MLV. Today I convert the MLV to CinemaDNG, or mount it as CinemaDNG folders (see [chapter 03](03-raw-post-processing.md#mlvfs-and-the-new-virtual-drives)). What I want is to put an MLV file in the timeline and have it decoded on the fly, on the graphics card, with nothing copied. This is where things stand on 24 November 2026. **Group: Reliable, on my test list.** I haven't tried any of it yet.

**Resolve.** Resolve has no documented way to add a decoder for a new format. It reads CinemaDNG sequences, so the way in is a virtual drive that shows each MLV as a CinemaDNG folder without writing those files to disk. Three new tools do it:

| Tool | Licence | Version | What its README says |
|---|---|---|---|
| [CineFS](https://github.com/ozcancelik/CineFS) | Apache-2.0 | 0.2.0, 22 November 2026 | macOS through the NFS client built into macOS, and Windows through WinFsp; an early release |
| [MLV Drive](https://github.com/bouncyball-git/mlvdrive) (bouncyball) | GPL-3.0 | 0.9.1, 22 November 2026 | Windows through WinFsp, macOS 26 or later through FSKit; a work in progress |
| [MLV Drive](https://github.com/charlie-schomp/MLVDrive) (charlie-schomp) | GPL-2.0 | 0.4.3, 6 November 2026 | Used day to day with Resolve on Windows |
| [mlv2Resolve](https://github.com/julienbeka/mlv2Resolve) | GPL-3.0 | 0.2.15, 1 November 2026 | Apple Silicon, needs FUSE-T; tested with Resolve Studio 21.1.1 |

Two unrelated projects share the name MLV Drive. The details of all four are in [chapter 03](03-raw-post-processing.md#mlvfs-and-the-new-virtual-drives).

Lossless MLV already stores its frames in LJ92, the same compression as compressed CinemaDNG. CineFS wraps these frames in DNG files without decoding them, so the virtual drive doesn't have to decompress anything. MLVFS, the tool I used in 2017, did all its processing on the CPU at each frame, which is why it was slow.

**Final Cut Pro.** Since macOS 15, Apple's Media Extensions let an application add a format reader and a RAW processor that Final Cut Pro, QuickTime Player and Compressor then use. BRAW Toolbox (version 3, April 2026) does this for Blackmagic RAW. I found no Media Extension for MLV. [SpliceKit](https://github.com/elliotttate/SpliceKit) (MIT), which I use to drive Final Cut Pro, contains a RAW processor for BRAW that plugs into Final Cut, which makes it a possible starting point for an MLV one.

**The test I will do:** my own MLV clips, mounted with CineFS, in a Resolve timeline; then an FCPXML from Final Cut Pro conformed on them. **Measure:** frames per second at playback, and whether the conform finds every clip at the right frame.

## The closed formats

The cinema cameras I may use on the next films record formats whose specification isn't public:

| Format | Who controls it | How an open tool can read it today |
|---|---|---|
| Blackmagic RAW (BRAW) | Blackmagic Design: an SDK, version 6.0 of 14 September 2026, for macOS, Windows and Linux ([developer page](https://www.blackmagicdesign.com/developer/products/braw/sdk-and-software)) | No open decoder found. The SDK runtime, installed by the user, can be loaded by an open program (see below) |
| ProRes RAW | Apple | FFmpeg has a ProRes RAW decoder since version 8.0 (["ProRes RAW decoder"](https://github.com/FFmpeg/FFmpeg/blob/master/Changelog) in the Changelog) |
| R3D | RED: an SDK under a licence agreement ([RED R3D SDK licence](https://www.reddigitalcinema.com/legal/red-r3d-sdk-license-agreement)) | FFmpeg has an R3D demuxer; what it decodes of the RAW, I haven't checked |
| ARRIRAW | ARRI: an SDK for members of its partner programme ([ARRIRAW page](https://www.arri.com/en/learn-help/learn-help-camera-system/pre-postproduction/file-formats-data-handling/arriraw)) | No open reader found |

The Blackmagic page shows no licence text; I haven't read the terms of the SDK, so I don't describe them.

## How open software deals with closed formats

Three ways, each with a real example.

**1. Write a decoder from the files.** FFmpeg's ProRes RAW decoder, added in version 8.0, is open code in an open program. FFmpeg's ProRes encoders are the same case: written without Apple's licence, as [self-hosted-film-lab](https://github.com/ismael-joffroy-chandoutis/self-hosted-film-lab) notes.

**2. Load a runtime that the user installs.** [warb](https://github.com/paolobarbolini/warb) (MIT, version 0.2.0 of 24 November 2026) reads Blackmagic RAW from Rust. Its README says that it doesn't link to the Blackmagic library when it is built: the runtime is loaded at run time with `dlopen`, and "each end user installs the BMD runtime on their own machine and accepts Blackmagic's license directly". warb needs Blackmagic RAW 6.0, runs on Linux x86_64 only, and its author writes that it "has not been tested for image-fidelity use cases": it's meant for proxies, thumbnails and previews.

**3. Convert in a closed tool first.** DaVinci Resolve reads BRAW for free; [self-hosted-film-lab](https://github.com/ismael-joffroy-chandoutis/self-hosted-film-lab) plans a conversion step in Resolve before ingest, because, as its README says, FFmpeg doesn't decode BRAW, ProRes RAW or R3D. The ProRes RAW part of that note is out of date: the decoder has been in FFmpeg since version 8.0.

For the GPL itself, the Free Software Foundation's [GPL FAQ](https://www.gnu.org/licenses/gpl-faq.html) has entries on plug-ins (#GPLPlugins), on system libraries (#SystemLibraryException) and on free software that uses nonfree libraries (#FSWithNFLibs). The last one says: "If you do this, your program won't be fully usable in a free environment." It asks to mention the dependency in the README as a drawback. I quote the FAQ and don't interpret it; I read it in the Wayback Machine copy of 1 January 2026, because gnu.org didn't answer on 24 November 2026.

## What it means for my next films

The 5D Mark III with Magic Lantern records a format that open tools read from the file to the archive. The cameras I am testing for the next films don't: the Blackmagic Pocket Cinema Camera 6K Pro records BRAW, and the iPhone 15 Pro Max records ProRes, a closed codec that FFmpeg decodes. With them, an open chain starts with a decoder or a conversion, and that step goes in the [test list](11-open-chain-test-list.md).

[Back to the README](../README.md) · Previous: [12. Sound and mixing](12-sound-and-mixing.md) · Next: [14. ComfyUI, Wan2GP and Pinokio](14-comfyui-wan2gp-pinokio.md)
