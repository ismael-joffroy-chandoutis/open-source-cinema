# 12. Sound and mixing

[Back to the README](../README.md) · Previous: [11. The open chain: test list](11-open-chain-test-list.md) · Next: [13. Formats: open, closed, and how open tools read them](13-formats.md)

## What I have done with sound

On the 5D Mark III, Magic Lantern records sound with the RAW (`mlv_snd.mo`), and it can record an H.264 proxy with its own sound on the SD card at the same time. In India in 2017 the proxy sound was about two seconds off from the RAW, with an offset that changed from clip to clip; the fix and the conform are in [chapter 02](02-magic-lantern-5d-mark-iii.md#the-h264-proxy-recorded-with-the-raw) and [chapter 04](04-offline-online-conform-and-grading.md).

On a 30-minute documentary shot with the same workflow, the sound was edited and mixed in Pro Tools, while the pictures were conformed in Resolve ([#71](https://www.magiclantern.fm/forum/index.php?topic=25880.msg191868#msg191868)). Pro Tools is closed. It's the step of my chain where I have never used an open tool.

For documentary voice recordings I built a voice repair pipeline, measured on real material, in [cinema-ai-toolkit](https://github.com/ismael-joffroy-chandoutis/cinema-ai-toolkit).

## Ardour

[Ardour](https://ardour.org/) is the open digital audio workstation I want to test for a film mix. It's under the GNU GPL v2, and version 9.10 came out on 10 November 2026 ([release notes](https://ardour.org/whatsnew.html)).

**Group: Reliable, on my test list.**

What the [features page](https://ardour.org/features.html) lists that matters for a film:

- a video timeline, with a frame-by-frame view locked to the audio and a video monitor with timecode;
- LTC to sync with other machines;
- a monitor section with dim, cut and mute;
- EBU R128 metering, loudness analysis, and a loudness assistant;
- stem export, one file per track, and export through FFmpeg for other formats;
- VST2, VST3, AU, LADSPA and LV2 plugins, and Lua scripting.

Ardour's source code also includes a library to import AAF files ([`libs/aaf`](https://github.com/Ardour/ardour/tree/master/libs/aaf)) and a reader for Pro Tools sessions ([`libs/ptformat`](https://github.com/Ardour/ardour/tree/master/libs/ptformat)). AAF is the usual way an edit goes from the editing software to the sound studio. I haven't tested either import.

## Other tools

- **Audacity** (GPLv3) edits audio files. It isn't a multitrack station to mix a film.
- **REAPER** is a commercial licence, not an open tool.
- **FFmpeg** measures loudness (`ebur128` filter) and detects silence: [self-hosted-film-lab](https://github.com/ismael-joffroy-chandoutis/self-hosted-film-lab) uses it for its quality reports.

## The test I will do

One scene whose final mix I already have:

1. Export the edit with its sound as AAF, and the reference picture as a video file.
2. Open the AAF in Ardour, with the video on the video timeline.
3. Edit the dialogue, the ambiences and the effects, and mix in stereo, then in 5.1.
4. Export the stems and the mix as WAV, one file per channel.
5. Put the 5.1 WAV files in [DCP-o-matic](08-delivery-and-archiving.md#dcp-with-dcp-o-matic) and play the DCP.

**Measure:** which clips and fades survive the AAF import, the sync with the picture at the end of the scene, and the time it takes compared with the Pro Tools mix.

[Back to the README](../README.md) · Previous: [11. The open chain: test list](11-open-chain-test-list.md) · Next: [13. Formats: open, closed, and how open tools read them](13-formats.md)
