# Flux
is a family of diffusion/image models by [black forest labs](https://blackforestlabs.ai/announcing-black-forest-labs/). By people who were behind Stability AI (company that developed SDXL).

#### What is Flux?
is a cutting-edge AI image generator created by Black Forest Labs, the same team behind popular Stable Diffusion. its designed to push the boundaries of whats possible with Artificial intelligence in a visual creativity. At its core, FLUX.1 utilizes advanced algorithms to transform text prompts into highly detailed and visually stunning images. 

# Model Variants
To strike a balance between accessibility and model capabilities, FLUX.1 comes in three variants: FLUX.1 pro, FLUX.1 dev and FLUX.1 schnell

#### 1. FLUX.1 pro
The best of FLUX.1, offering state-of-the-art performance image generation with top of the line prompt following, visual quality, image detail and output diversity.
- Its closed licensed model accessible via APIs only.
- Its ultimate tool for professional and big companies.
- Its great at following instructions and creating super-detailed high-quality images. 

#### 2. FLUX.1 dev
is an open-weight, guidance-distilled model for non-commercial applications. Directly distilled from FLUX.1 pro, FLUX.1 dev obtains similar quality and prompt adherence capabilities, while being more efficient than a standard model of the same size.
- Its perfect for playing around with ideas and testing creative concepts for non-commercial use.
- good for training LoRAs 

#### 3. FLUX.1 schnell
its the fastest model, is tailored for local development and personal use. FLUX.1 schnell is openly available under an Apache2.0 license.
- It takes 4 steps to generate images
- There are slight distortion but the output is better than SDXL.

#### Comparing Variants 

| Qualifier | FLUX.1 pro | FLUX.1 dev | FLUX.1 schnell |
| :---:         |     :---:      |    :---: |    :---: |
| Image Quality   | Best     | Better    | Good    |
| Speed   | Good     | Good    | Best    |
| Usability & Licensing   | Paid. Cloased. for Ent & Pros. high Quality images. Commercial purpose     | Non-commerical. for Student, Hobbyist & Researchers    | Open. Personal & Local development. rapid prototyping    |

# Flux workflow basics

- Load checkpoint node has 3 components i.e. MODEL, CLIP & VAE. For Flux workflow, these components has to be loaded seperately as induvidual nodes.
    - Load Diffusion Model node
    - DualClip Loader
    - Load VAE
  - Flux Guidance
 ![image](https://github.com/user-attachments/assets/a21466d7-3424-49ce-8e76-a5d20a10af5a)

#### Load Diffusion Model 
- choose flux Dev as unet model
- Weight Type as fp8. weight type is the compression of the model associated with size. smaller model have distortions, but very very negligible
  
#### DualClip Loader
- connect both Positive and Negative clips to Dual Clip Loader
- Only positive clip is considered in Flux architecture
- Negative clip is required for ComfyUI architecture, but it does not make any difference to Flux WF. its suggest to keep empty.
- 

#### Flux Guidance 
- add strength to the prompt i.e. its addition or adding strength to CFG
- only added to Positive CLIP

#### kSampler
- Make CFG to 1.0 as the strength is determined by Flux guiance node.  




      
