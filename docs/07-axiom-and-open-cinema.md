# 07. AXIOM and open cinema

[Back to the README](../README.md) · Previous: [06. Outlook and test list](06-outlook-and-test-list.md) · Next: [08. Delivery and archiving](08-delivery-and-archiving.md)

## A camera built open from the start

Magic Lantern opens a closed camera from the outside. The AXIOM, by the apertus° association, tried the other way: a cinema camera built open from the start, hardware and software. In September 2014 Magic Lantern and apertus° announced a partnership to work together on colour science and raw processing ([apertus° history](https://www.apertus.org/history.html)). In November 2026 the AXIOM is still not a camera you can order for a shoot. This chapter says where it is, and lists the other open projects I follow.

The three groups (**What I have shot with**, **Reliable, on my test list**, **Not ready**) are defined in the [README](../README.md).

## AXIOM in November 2026

**Group: Not ready.**

What the [apertus° site](https://apertus.org/axiom.html) shows today:

- **AXIOM Beta Developer Kit**: 3,990 € excluding VAT and shipping, "Shipping - Delivered inside six weeks". The [pricelist](https://www.apertus.org/pricelist.html) gives what is in it: the CMV12000 sensor on its board, the main, power and interface boards, a modified MicroZed, one HDMI module, an open aluminium frame with a passive E-mount, a 5 V mains supply and a microSD card with the firmware. The sensor board alone is 2,486 € including VAT, more than half of the kit. It's a development platform; I wouldn't take it on a shoot.
- **AXIOM Beta Compact**: 5,990 € excluding VAT, "In development", with a pre-order form and no shipping date. The [development status page](https://www.apertus.org/axiom-beta-roadmap.html) says the team is gathering a group of ten or more early adopters before it can quote the enclosure.
- **AXIOM Extended**: early development, no price.

The latest news article on the site is the [Google Summer of Code wrap-up of September 2021](https://apertus.org/google-summer-of-code-wrap-2021-article-september-2021.html). On GitHub, the [apertus° organisation](https://github.com/apertus-open-source-cinema) has 82 public repositories, and the last commit on [axiom-firmware](https://github.com/apertus-open-source-cinema/axiom-firmware) is from 23 December 2025. So the project is not dead, but it's very quiet.

The sensor is an ams CMV12000: 4096x3072, Super 35, global shutter. The [sensor page](https://apertus.org/axiom-beta-imagesensors.html) gives up to 300 fps in 10-bit and 132 fps in 12-bit, and "up to 15 F-stops (pseudo logarithmic response curve) / 10 F-stops (linear)". These are figures of the sensor, from its data sheet. They are not measurements made on the camera, and the same page says that the current hardware and software don't use the full frame rate of the sensor.

The camera has no internal recording. The standard output is HDMI 1080p60 ([tech specs](https://www.apertus.org/axiom-beta-tech-specs.html)). For RAW, the team sends a custom packed HDMI stream to a Magewell USB3 capture device and a computer next to the camera, which gives uncompressed 4K/UHD at 12 bits and 24, 25 or 30 fps ([development status](https://www.apertus.org/axiom-beta-roadmap.html)).

I backed the AXIOM Beta crowdfunding campaign in September 2014. Backers who hold a voucher can buy the Developer Kit at cost, 2,100 € excluding VAT at the moment, and apertus° writes that this offer doesn't expire ([crowdfunding information](https://www.apertus.org/axiom-beta-crowdfunding-backer-supporter-information.html)).

What I still find interesting in it: a reprogrammable FPGA for the image pipeline, a global shutter, and a camera where every step from the sensor to the file can be read and changed. The camera boots from a microSD card and the [firmware repository](https://github.com/apertus-open-source-cinema/axiom-firmware) can be built and run in an emulator, so a mistake costs a card to rewrite. What stops me from planning a film with it: there is no internal recording, the Compact has no shipping date, and the community has been very quiet since 2021.

## Other open cameras and capture

**CinePi and CineMate. Group: Reliable, on my test list.** CinePi is an open cinema camera on Raspberry Pi that records CinemaDNG. The original [cinepi-raw](https://github.com/cinepi/cinepi-raw) repository (BSD-2-Clause) has had no push since June 2024. The work continues in [CineMate](https://github.com/Tiramisioux/cinemate), version 3.4.1 (30 September 2026), for the Raspberry Pi 4 and 5: 10 and 12-bit CinemaDNG, and on the IMX585 sensor a 16-bit "ClearHDR" mode and a "CineMate Log" curve. It records on an SSD, an NVMe drive or a CFexpress card, and its README lists four sensors, from the Raspberry Pi HQ camera (IMX477) to the 1-inch IMX283. In November 2026 it's the open camera that is alive: a small sensor, but files that go straight into the chain of this repository.

**MotionCam Pro. Group: Reliable, on my test list.** [MotionCam Pro](https://www.motioncamapp.com/) records RAW video on a phone, in its own MCRAW format, on Android and on iPhone with iOS 18 or later. It's paid and proprietary. I list it because the open tools read its files: vkdt has an `i-mcraw` module, and CineFS mounts MCRAW as CinemaDNG (see [chapter 03](03-raw-post-processing.md)), the same as MLV.

**Kinograph. Group: Not ready.** [Kinograph](https://kinograph.cc/) is an open film scanner for 35 and 16 mm. The site says "Kinograph version 2, now in development".

## Open editing and finishing software

I edit in Final Cut Pro and finish in DaVinci Resolve (see [chapter 04](04-offline-online-conform-and-grading.md)), and neither of them is open. These are the open tools I watch, with their state on 24 November 2026.

| Tool | What it is | Version | Licence | Group |
|---|---|---|---|---|
| [Kdenlive](https://kdenlive.org/en/download/) | Desktop NLE, KDE | 26.08.3 | GPL | Reliable, on my test list |
| [Shotcut](https://github.com/mltframework/shotcut) | Desktop NLE on the MLT framework | 26.11.15 (16 November 2026) | GPL-3.0 | Reliable, on my test list |
| [OpenCut](https://github.com/OpenCut-app/OpenCut) | NLE in the browser | 0.3.0 (15 April 2026) | MIT | Not ready |
| [Olive](https://github.com/olive-editor/olive) | Desktop NLE | No release; last commit 5 December 2024 | GPL-3.0 | Not ready (stopped) |
| [Palmier Pro](https://github.com/palmier-io/palmier-pro) | NLE for macOS driven by AI agents | 1.0.0-beta.4 (20 November 2026) | GPLv3 up to 0.7.6; later binary releases are proprietary, per its README | Not ready |
| [Blender](https://www.blender.org/download/) | 3D, compositing, video sequencer | 5.3 (10 November 2026) | GPL | Reliable, on my test list |

Palmier Pro is often presented as open source. Only the releases up to 0.7.6 are under GPLv3. The code of those versions stays free, but the current builds are not.

## The whole chain with open tools

Can a film go from the sensor to the cinema screen with open tools only? In November 2026, almost. This is the chain, step by step, with where I stand on each tool.

| Step | Open tool | Where I stand |
|---|---|---|
| Camera | Magic Lantern on the 5D Mark III: free firmware on a closed camera | What I have shot with |
| Camera | CineMate on a Raspberry Pi | Reliable, on my test list |
| Camera | AXIOM Beta | Not ready |
| RAW development | [MLV App](https://github.com/ilia3101/MLV-App) (GPL-3.0) | What I have shot with |
| RAW development | [vkdt](https://github.com/hanatos/vkdt) (BSD-2-Clause) | Reliable, on my test list |
| Editing | Kdenlive, Shotcut, Blender | Reliable, on my test list |
| Timeline exchange | [OpenTimelineIO](https://github.com/AcademySoftwareFoundation/OpenTimelineIO) 0.18.1 (Apache-2.0) | Reliable, on my test list |
| Colour management | [OpenColorIO](https://github.com/AcademySoftwareFoundation/OpenColorIO) 2.6.0 (BSD-3-Clause) | Reliable, on my test list |
| Cinema copy | DCP-o-matic (see [chapter 08](08-delivery-and-archiving.md)) | Reliable, on my test list |
| Archive | CinemaDNG, FFV1, OpenEXR (see [chapter 08](08-delivery-and-archiving.md)) | CinemaDNG: what I have shot with. FFV1 and OpenEXR: on my test list |

Two steps are closed in my own chain today: the edit, in Final Cut Pro, and the grade, in DaVinci Resolve. The grade is the step where I have no open tool to put in the table.

The camera is the other limit. Magic Lantern is free software, but it runs on Canon's hardware, next to Canon's firmware. The 5D Mark III came out in 2012. In 2026 the same body still records 14-bit RAW, because the firmware around it is free and people keep working on it.

In all three cameras of the table the sensor itself is a proprietary chip: Canon's in the 5D Mark III, a Sony IMX in CineMate, the ams CMV12000 in the AXIOM. The open part is what surrounds it: boards, firmware, drivers and tools.

## Cameras for the coming films

I have already shot a little of my next feature on the 5D Mark III, and at the moment I'm testing a [Blackmagic Pocket Cinema Camera 6K Pro](https://www.blackmagicdesign.com/products/blackmagicpocketcinemacamera) for it. Two other cameras are on my list: an iPhone 15 Pro Max for discreet and run-and-gun shooting, and a Canon EOS R6 Mark III as a hybrid narrative camera. I give no figures here; the manufacturers' pages have the current specifications. All three shoot a log or RAW format that can be brought into the same DaVinci Wide Gamut grade as the 5D Mark III RAW, with the CST sandwich described in [chapter 04](04-offline-online-conform-and-grading.md).

[Back to the README](../README.md) · Previous: [06. Outlook and test list](06-outlook-and-test-list.md) · Next: [08. Delivery and archiving](08-delivery-and-archiving.md)
