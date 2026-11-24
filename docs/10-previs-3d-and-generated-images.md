# 10. Previs, 3D and generated images

[Back to the README](../README.md) · Previous: [09. On-set data](09-on-set-data.md) · Next: [11. The open chain: test list](11-open-chain-test-list.md)

## From Maalbeek to Blender

The first time I built the images of a film in 3D was Maalbeek. The places were filmed in RAW video long takes, the frames became point clouds, and the point clouds were rendered in Unity with shaders written for the film. That chapter is [01](01-maalbeek-photogrammetry.md). Two tools of that chain are closed: Metashape for the photogrammetry, Unity for the render.

Since then, the 3D tools I have built are around Blender, which is open (GNU GPL), and connect it to image generation in ComfyUI, which is open too (GPL-3.0). This chapter says where these pieces are documented and what state they are in. The models themselves are another question: see [Open weights are not open source](00-the-whole-chain.md#open-weights-are-not-open-source).

## Blender passes as a guide for generation

[comfyui-blender-temporal](https://github.com/ismael-joffroy-chandoutis/comfyui-blender-temporal) is a set of ComfyUI nodes that read the depth and normal passes Blender writes in OpenEXR, and use them to condition the generation with ControlNet. Blender's depth pass is exact because it comes from the 3D scene. A depth estimated from an image is a guess. It is for sequences where I control the 3D scene.

The repository is under the PolyForm Noncommercial licence. It can be read and used, but not for commercial work, so it isn't free software in the strict sense.

## A film set for generated shots

[spritz](https://github.com/ismael-joffroy-chandoutis/spritz) (MIT) organises generated video like a shoot: projects, shots and takes, over ComfyUI. The camera move can come from Blender: a script exports the first frame, a guide video and the camera path. The edit leaves as an FCP7 XML for Premiere and Resolve. Everything runs on your own machine, with no account.

**Group: Not ready.** The state was verified on 7 November 2026 with a mock engine and no GPU, most ComfyUI templates are placeholders to adapt, and under Blender 5.2 the exporter stops at the guide video. The sound part (speech, music, effects with local models) is not wired yet.

## Tests I measured on my own machine

Two benches measured on my own workstation, an RTX 5090 with 32 GB of video memory.

- **Upscalers, June 2026.** [ai-upscaler-benchmark](https://github.com/ismael-joffroy-chandoutis/ai-upscaler-benchmark) gives the speed and memory of video and image upscalers, measured on 16 June 2026. Only speed and memory are measured, on a synthetic frame. The quality on real shots is not measured.
- **Who is on screen, September 2026.** [vlm-shot-labeling-2026](https://github.com/ismael-joffroy-chandoutis/vlm-shot-labeling-2026) compares open-weight vision models running on the workstation with Gemini, a paid API, on the 116 shots of one scene of Mindhunter (season 1, episode 3). It's a tool for the edit: knowing who is on screen in each shot. One scene is a small sample.

## Guides for artists

[local-ai-studio-guides](https://github.com/ismael-joffroy-chandoutis/local-ai-studio-guides) (texts under CC BY-SA 4.0, in French) are step-by-step guides I wrote in September 2026 for the artists of the Écritures Liquides residency at the CENTQUATRE-Paris, where I am the mentor: training a LoRA, making images and videos in ComfyUI, installing with Pinokio, organising your tests. Each guide is meant to be followed by the artist alone, on one workstation with a 32 GB graphics card.

## Open photogrammetry and splats

I haven't used open photogrammetry on a film yet. In [chapter 01](01-maalbeek-photogrammetry.md#how-i-would-do-it-today-not-tried) I wrote what I would test if I scanned the places of Maalbeek again: COLMAP for the camera poses, and Gaussian splats in place of a point cloud. Since then, Blender 5.3 (10 November 2026) has added Gaussian splat import. The tools and the protocol are in the [test list](11-open-chain-test-list.md#3d-photogrammetry-and-splats).

[Back to the README](../README.md) · Previous: [09. On-set data](09-on-set-data.md) · Next: [11. The open chain: test list](11-open-chain-test-list.md)
