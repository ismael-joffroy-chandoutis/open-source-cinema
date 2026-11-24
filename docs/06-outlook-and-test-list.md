# 06. Outlook and test list

[Back to the README](../README.md) · Previous: [05. Film looks and restoration](05-film-looks-and-restoration.md) · Next: [07. AXIOM and open cinema](07-axiom-and-open-cinema.md)

## Where I stand

In 2020 and again in 2022 I asked on the forum for a real-time preview in the 5.7K anamorphic modes of the 5D Mark III ([#201](https://www.magiclantern.fm/forum/index.php?topic=25180.msg229685#msg229685), [#211](https://www.magiclantern.fm/forum/index.php?topic=23041.msg240650#msg240650)). In 2022 the answer was that nobody was working on it ([#213](https://www.magiclantern.fm/forum/index.php?topic=23041.msg240661#msg240661)). That is still where I am. I will use the 5.7K modes more when there is a correct preview on the camera. Until then, the modes with a real-time colour image on the camera are the 3x3 binning modes (1080p and 3:2).

Dual ISO is the other open question for me. My tests in 2018 were not good with the debayering I tried ([#158](https://www.magiclantern.fm/forum/index.php?topic=19300.msg206101#msg206101)). The processing has changed since, so I want to test it again before I say anything about it.

## The goal: a 5D Mark III that matches a Blackmagic Pocket 6K

That is the challenge I set for this camera. I make auteur films, short and feature, and for this kind of cinema I want tools I can master and keep for years. The 5D Mark III came out in 2012. With Magic Lantern it records full-frame RAW, and its 5.7K anamorphic mode gives an image above 4K wide. Keeping it in use is permacomputing: working with what already exists.

Three things are needed to shoot a whole film with it:

| What a film shoot needs | Where the 5D3 is in November 2026 |
|---|---|
| A RAW image above 4K wide | Done. 5.7K anamorphic, 12-bit lossless, continuous on both cards. The numbers are in [chapter 02](02-magic-lantern-5d-mark-iii.md#the-57k-anamorphic-mode-in-numbers) |
| A preview to frame and pull focus during the take | Missing. In 5.7K the screen shows a slow greyscale image. This is the one thing that stops me |
| Playback of a take on set | Not solved on the camera. The fallback works: take the card out and open the clip on a laptop |

**What blocks the preview.** Bilal's Crop mood already gives a real-time preview in the 1x3 anamorphic modes of the 650D, 700D, EOS M and 100D: "All of these presets have Full Real-Time preview" ([thread 26851](https://www.magiclantern.fm/forum/index.php?topic=26851.0)). On the 5D3 the preview is set by a second processor core, EEKO, which overwrites what Magic Lantern writes. Bilal's own steps, in his words:

- 18 May 2022: the place to start is "to capture DebugMsg log from 5D3, between x5 and x10 mode" ([post](https://www.magiclantern.fm/forum/index.php?topic=25287.msg238876#msg238876)).
- 16 April 2024: "I finally found the missing piece", and "The next step for now is to implement a way to hook EEKO code easily" ([post](https://www.magiclantern.fm/forum/index.php?topic=25287.msg246619#msg246619)).
- 7 June 2025: "There are no plans to work on the 5D3 currently, sorry." ([post](https://www.magiclantern.fm/forum/index.php?topic=26851.msg247673#msg247673)).

**What I can bring.** Logs from my camera, following the recipe Bilal gave in April 2024 ([post](https://www.magiclantern.fm/forum/index.php?topic=19336.msg246645#msg246645)). Money, on the model of Crop mood: paid when the feature works and is released for everyone. And this documentation, so that what is known is in one place.

**What exists today to try.** arnaud-sintes' "ultrafast framed preview" makes the software preview faster. On his 5D3, the colour preview goes from 4.5 to about 12 frames per second at quarter resolution ([thread 26998](https://www.magiclantern.fm/forum/index.php?topic=26998.0)). I have not tried it in 5.7K yet. It is test 8 below.

## The state of Magic Lantern in November 2026

**One official release.** Since the team came back in 2025, one official version has been published, the "Midsummer" builds of June 2025 ([forum announcement](https://www.magiclantern.fm/forum/index.php?topic=27315.0)). Work continues in the [official repository](https://github.com/reticulatedpines/magiclantern_simplified) on the `dev` branch, without a new build.

**What has gone into the code since.** For the 5D Mark III, two things matter:

- the SD overclock module in the official packages ([14 September 2025](https://github.com/reticulatedpines/magiclantern_simplified/commit/9c1cd0a3c910313f30d0dbdfe5a4035cf3c32538)), renamed `sd_clock` in [September 2026](https://github.com/reticulatedpines/magiclantern_simplified/commit/4dca98d6327e1ca4384bd00c935f08a317a93112);
- writing on both cards in `mlv_lite` ([30 September 2025](https://github.com/reticulatedpines/magiclantern_simplified/commit/f0dc17db9bad4c6058901452c1ac448e0ba6c91a)).

There are also Dual ISO fixes for the 100D, 650D, 700D and EOS M ([2 October 2026](https://github.com/reticulatedpines/magiclantern_simplified/commit/9b065960e44c494b5b1edbc7381cbd78b6de9811)). None of this exists as an official build yet.

**No Crop mood on the 5D3.** Bilal's "Crop mood" gives a real-time preview in crop modes on the 650D, 700D, EOS M, M2 and 100D ([thread 26851](https://www.magiclantern.fm/forum/index.php?topic=26851.0)). There is no port for the 5D Mark III. In June 2025 Bilal wrote that there are no plans for it. The details are in the section above.

**HDMI in crop modes is still broken on the 5D3.** arnaud-sintes wrote in May 2023 that HDMI output doesn't work properly when switching to any crop mode ([thread 26910](https://www.magiclantern.fm/forum/index.php?topic=26910.0)). A user was still asking for a fix in February 2026.

**EOS R and R8.** On the EOS R, RAW recording ran 1080p60 continuously in February 2024, in the development thread ([thread 22770](https://www.magiclantern.fm/forum/index.php?topic=22770.0)). On 6 November 2026, Bilal published a video of an R8 recording RAW ([Canon R8 runs Magic Lantern and records RAW video!](https://www.youtube.com/watch?v=LcsfldNuZuc)), and said it is not ready yet for users. Neither camera has a build for filmmakers.

**Post-processing.** MLV App 1.16 came out on [2 June 2026](https://github.com/ilia3101/MLV-App/releases/tag/Qtv1.16), with an improved Dual ISO algorithm. MLVFS, which I used in 2017 to mount MLV files as CinemaDNG folders for Resolve, has not moved since 2016. Two new tools do the same job: [MLV Drive](https://github.com/bouncyball-git/mlvdrive) by bouncyball, which uses FSKit on recent macOS without macFUSE ([thread 27485](https://www.magiclantern.fm/forum/index.php?topic=27485.0)), and [CineFS](https://github.com/ozcancelik/CineFS), version 0.2.0 of 22 November 2026, for macOS and Windows. The details are in [03-raw-post-processing.md](03-raw-post-processing.md).

**The project's policy on LLMs.** On 20 August 2026 the Magic Lantern team published an [LLM policy](https://github.com/reticulatedpines/magiclantern_simplified/blob/e15e0c2d2bece6285dde0e4528c364980c348018/LLM_POLICY.md). Contributors must say which parts of their work were produced or guided by an LLM. Code generated by an LLM is not accepted beyond a small size, following the GNU guideline of about 15 lines, for copyright reasons. You can learn from LLM output, but the code you contribute has to be your own and you have to understand it.

**To follow, too early to plan a shoot on.** Autofocus during RAW recording, tested by a forum member on the 5D Mark III with a 24-105 ([thread 27458](https://www.magiclantern.fm/forum/index.php?topic=27458.0)). The port to the 5D Mark IV, worked on by Corebee_ on a `5d4/port` branch for firmware 1.3.3.

## Test list

None of these tests has been done yet. Each one is in the group **Reliable, on my test list** until I have the result. When a test is done, the result goes in the chapter concerned, with the date, the build and the card.

| # | Test | What it will measure |
|---|---|---|
| 1 | **3:2 (1920x1280), 14-bit lossless, 24 fps, CF only** | How long the camera records before it stops, at ISO 100 and ISO 1600, with one card model. Same test in 1920x1080 to compare |
| 2 | **3:2 with the H.264 proxy on the SD** | Whether RAW and proxy both record continuously, the sync offset between the two, and whether the proxy framing matches the RAW. On firmware 1.2.3 and 1.1.3 |
| 3 | **Test 2 with an HDMI monitor connected** | Whether the camera stays stable, and what the monitor shows (colour, framing, delay) |
| 4 | **Dual ISO processed in MLV App 1.16** | On the same shot: dynamic range gained in practice, aliasing and moiré, compared with my 2018 results |
| 5 | **MLV Drive or CineFS on my Mac** | Whether Resolve reads the mounted CinemaDNG folders in real time, and whether the conform from the proxy edit works on them |
| 6 | **A spektrafilm LUT on my CinemaDNG** | Whether a LUT exported with [spektrafilm](https://github.com/andreavolpato/spektrafilm) gives a usable film look on 5D3 footage in Resolve, and where it breaks (skin, highlights, saturated light) |
| 7 | **5.7K anamorphic, 12-bit lossless, on both cards, with the H.264 proxy on the SD** | Whether RAW and proxy both record for 3 minutes, the write speed on each card, and what the proxy shows: the whole frame squeezed, or a cropped band. I found nobody who reported this combination |
| 8 | **arnaud-sintes' ultrafast preview in 5.7K anamorphic** | Frames per second of the preview before and during recording, in colour and in greyscale, and whether I can frame with it |
| 9 | **5.7K anamorphic, 14-bit lossless** | Whether it records continuously at ISO 100 and ISO 1600, and the real data rate |
| 10 | **15-minute takes in 5.7K, several in a row** | Whether the camera stays stable and how warm it gets, for interviews |
| 11 | **Debug logs for the preview** | Build the logging version from the official repository and capture the logs Bilal described for the 5D3 |

Tests 1 to 3 decide whether 3:2 becomes a mode I shoot with. Test 4 decides what I write about Dual ISO. Tests 5 and 6 are post-production, see chapters [03](03-raw-post-processing.md) and [05](05-film-looks-and-restoration.md). Tests 7 to 10 decide how far I can shoot in 5.7K today. Test 11 is my part in the preview work.

[Back to the README](../README.md) · Previous: [05. Film looks and restoration](05-film-looks-and-restoration.md) · Next: [07. AXIOM and open cinema](07-axiom-and-open-cinema.md)
