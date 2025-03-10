ComfyUI examples
[Comfy Examples](https://comfyanonymous.github.io/ComfyUI_examples/)

# Image Models
- SD1.x, SD2.x,
- SDXL, SDXL Turbo
- Stable Cascade
- SD3 and SD3.5
- Pixart Alpha and Sigma
- AuraFlow
- HunyuanDiT
- Flux
- Lumina Image 2.0
- PonyXL

# SD1.5
- has the most choices and variety as it's been around longer
- popular for creators as they take less GPU hours to train, so it's literally cheaper & quicker for community members to make them on their own home GPUs vs leasing expensive cloud servers
- optimized for 512x512 (0.5MP) photos in a handful of certain landscape and portrait aspect ratios. Tends to produce artifacts if you go outside these boundaries, but there are ways to lessen/avoid.
- can achieve high quality, but may take more effort
- originally not easy to prompt, but the popular models have improved this greatly so that high quality is not hard to achieve
- typically requires the use of negative prompts, eg. "ugly, bad hands, low light, blurry" to describe attributes you don't want in the image. Can also use embeddings eg FastNegative or BadPrompt, also in CivitAI

# SDLX
- optimized for 1024x1024 (1MP) and several non-square aspect ratios. Still can produce artifacts outside of these, but you can apply the same workarounds as 1.5
- much better at understanding plainly written prompts, easier to achieve high quality
- negative prompts not necessary, but can still come in handy to steer away from concepts you don't want to see, eg "hat"
- plenty in the community to choose from, but fewer than 1.5 as it takes more GPU hours
