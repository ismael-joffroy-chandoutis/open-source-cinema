# 14. ComfyUI, Wan2GP and Pinokio

[Back to the README](../README.md) · Previous: [13. Formats: open, closed, and how open tools read them](13-formats.md) · Next: [15. Conserving films and artworks with open tools](15-conserving-artworks.md)

In 2026 I have run image and video generation on my own machines: two workstations with an RTX 5090 (32 GB), one with an RTX 4090 (24 GB), and a MacBook Pro with 64 GB of memory. This chapter is what I installed, built and measured this year with three tools: ComfyUI, Wan2GP and Pinokio. The models themselves have their own licences; see [Open weights are not open source](00-the-whole-chain.md#open-weights-are-not-open-source).

## The three tools and their licences

| Tool | What it is | Licence |
|---|---|---|
| [ComfyUI](https://github.com/Comfy-Org/ComfyUI) | Node graph for image, video and audio generation, with an API | GPL-3.0 |
| [Wan2GP](https://github.com/deepbeepmeep/WanGP) | Video generation with forms instead of a graph, tuned for cards with little memory | WanGP Community License 2.0: free to use and modify, outputs can be sold; WanGP itself can't be sold or offered as a paid hosted service without a commercial licence. It's source-available, not open source |
| [Pinokio](https://github.com/pinokiocomputer/pinokio) | A launcher that installs, starts and updates AI applications | MIT |

## What I did, by date

| Date | What I did |
|---|---|
| February 2026 | Wrote three ComfyUI nodes that load Blender's EXR depth and normal passes as ControlNet conditioning: [comfyui-blender-temporal](https://github.com/ismael-joffroy-chandoutis/comfyui-blender-temporal). Started [comfyui-cinema-pipeline](https://github.com/ismael-joffroy-chandoutis/comfyui-cinema-pipeline), my notes on ComfyUI for film work |
| March 2026 | Installed a full Windows workstation through Pinokio: 146 applications, 95 ComfyUI node packs, 5 LoRA training tools ([windows-cinema-workstation](https://github.com/ismael-joffroy-chandoutis/windows-cinema-workstation)). Compared seven simplified front-ends for ComfyUI |
| May 2026 | Asked Comfy Cloud to accept a third-party node pack that worked locally and was refused by the cloud ([issue #13963](https://github.com/Comfy-Org/ComfyUI/issues/13963), open, no answer on 24 November 2026) |
| September 2026 | Ran eleven canvases and agent-driven editors under one protocol, on the same ComfyUI. Wrote step-by-step guides for the artists of the Écritures Liquides residency ([local-ai-studio-guides](https://github.com/ismael-joffroy-chandoutis/local-ai-studio-guides)) |
| November 2026 | Read the ComfyUI front-end code to see what can be shared locally ([comfyui-apps-guide](https://github.com/ismael-joffroy-chandoutis/comfyui-apps-guide)). Published [spritz](https://github.com/ismael-joffroy-chandoutis/spritz). Measured the workstations and a laptop for a workshop, and connected three interfaces to one ComfyUI |

## Measured on my machines

These figures were measured on the date given, with ComfyUI 0.45.0. They are valid for these machines and these versions.

**RTX 5090 workstation, 15 November 2026.**

| Test | Size | First run | Next runs |
|---|---|---|---|
| Qwen-Image 2.1 turbo, 8 steps | 1024x1024 | 9.0 s | 5.1 s |
| FLUX 3 Klein distilled, 16 steps | 1024x1024 | 8.6 s | 6.5 s |
| MiniMax H3 image, 6 steps | 2048x2048 | 19.8 s | 10.0 to 10.2 s |
| FastH3 image to video with sound, 8 steps, 56 frames (2.3 s) | 832x480 | 49.7 s | 38.1 s |

**MacBook Pro, 64 GB, no network, 16 November 2026.** ComfyUI with the ComfyUI-GGUF node pack (Apache-2.0) and FLUX 3 Klein in GGUF Q8_0: 23 to 25 seconds per 1024x1024 image in 8 steps, 14.1 seconds in 4 steps. The process peaked at about 8 GB of memory. That's the fallback I prepared for a workshop with no network.

**RTX 5090 workstation, 20 November 2026.** Two ways to turn an existing shot into a grey 3D-like mock-up, on 81 frames at 832x480: an open workflow with Qwen Image Edit 2511 then Wan 2.1 VACE 14B took 12 min 13 s and 30.6 GB of video memory; the ComfyUI-CapCut white mock-up took 94 s and 19.7 GB.

## One ComfyUI, several interfaces

On the RTX 4090 workstation, on 16 November 2026, I connected three interfaces to the same ComfyUI and the same model folder, with no weights copied:

| Interface | Licence | What I checked |
|---|---|---|
| [Krita AI Diffusion](https://github.com/Acly/krita-ai-diffusion) 1.53.0 | GPL-3.0 | Moved from its own managed ComfyUI to the shared one; an equivalent graph generated a 768x768 image in 17 s |
| [InvokeAI](https://github.com/invoke-ai/InvokeAI) 6.14.4 | Apache-2.0 | Installed and generating with SDXL Turbo |
| ComfyArt 1.3.0 | MIT, per its repository | An image in about 18 s from its template |

A second model folder is read through `extra_model_paths.yaml`, so the weights live once on disk. Before installing a node pack, I compare `pip freeze` before and after: on this machine one pack wanted to move NumPy from 1.26.4 to 2.2.6, which would have broken other packs. On another workstation, six node packs failed to import for that reason.

For SwarmUI (MIT), the front-end I recommended in March, and the canvases, the notes are in [comfyui-cinema-pipeline](https://github.com/ismael-joffroy-chandoutis/comfyui-cinema-pipeline) and [creative-canvas-atlas](https://github.com/ismael-joffroy-chandoutis/creative-canvas-atlas).

## ComfyUI on a network, and online

ComfyUI has no authentication: anyone who reaches its address can run anything on the machine. I reach my workstations through a private network, never from the internet, and on the local network a firewall rule closes the ComfyUI and Pinokio ports. The details are in [comfyui-apps-guide](https://github.com/ismael-joffroy-chandoutis/comfyui-apps-guide).

Comfy Cloud is ComfyUI run by Comfy as a paid service. In May 2026, on the Creator plan, a node pack that worked on my workstation was refused by the cloud with a validation error: the cloud only runs the nodes it has accepted. Share links, in the November front-end code I read, only show in the cloud version.

## Wan2GP

I installed Wan2GP through Pinokio in March 2026 and updated it several times. Two things I learned:

- **Update without losing the environment.** Pinokio's standard update script deletes the old application folder and its environment. In September I backed up the repositories and updated with a fast-forward instead.
- **A port already in use stops the app silently.** If port 7860 is taken, Wan2GP dies at start while the Pinokio window still says "Running". The launcher starts it without a port option. I wrote this up as an issue draft for the launcher.

## Pinokio

Pinokio installs and starts applications for one person on one machine very well. Four things I learned:

- **Never share the command port.** Pinokio's home server answers on port 42000 and can open a shell. Share one application at a time, through a tunnel with an access code, and test the code in a private window.
- **Remote access can fail without saying so.** In September, remote access to Pinokio was refused because a component (Caddy) was missing, and the page only said "Backend still warming up...", 159 times in one session's log. I went through an SSH tunnel instead.
- **One model folder for every interface.** Pinokio can point the model folders of several applications to one shared folder, so the weights aren't copied.
- **Check the launcher, not only the name.** Two launchers can carry the same application name; the repository of the launcher says which one you install.

[Back to the README](../README.md) · Previous: [13. Formats: open, closed, and how open tools read them](13-formats.md) · Next: [15. Conserving films and artworks with open tools](15-conserving-artworks.md)
