# Stable Horde for Web UI
[Stable Horde](https://stablehorde.net) client for AUTOMATIC1111's [Stable Diffusion Web UI](https://github.com/AUTOMATIC1111/stable-diffusion-webui)

## Notice
This extension is not maintained the original author [@natanjunges](https://github.com/natanjunges) [has lost interest](https://github.com/AUTOMATIC1111/stable-diffusion-webui-extensions/pull/380#issuecomment-2433496833) in this project and has deleted the original repository.

This repository is a re-uploaded fork up to the latest commit from the original repository, to allow easy access to this extension for those who wants it.

I'm just uploading and providing access but have no intention of maintaining this project if someone wish to continue this project please make contact.

## Features

- **txt2img**, **img2img**, **depth2img**, **pix2pix**, **inpaint** and **interrogation** (img2txt)
- **SFW and NSFW generations**
- **Share generated images with [LAION](https://laion.ai) for improving their dataset**
- <details><summary>Base models:</summary>

    - **stable_diffusion_1.4** (v1.4)
    - **stable_diffusion** (v1.5)
    - **stable_diffusion_inpainting** (v1.5): Generalist model specialized for modifying areas of existing images
    - **stable_diffusion_2.0** (v2.0)
    - **Stable Diffusion 2 Depth** (v2): Generalist model specialized for creating depth maps of existing images, for img2img creations
    - **stable_diffusion_2.1** (v2.1)
    </details>
- <details><summary>Custom models:</summary>

    <!-- [[[cog
    import cog
    import requests

    models = requests.get("https://raw.githubusercontent.com/Sygil-Dev/nataili-model-reference/main/db.json")
    models = models.json()
    models_out = []

    for model in models:
        if "config" in models[model] and "download" in models[model]["config"]:
            for file in models[model]["config"]["download"]:
                if "file_path" in file and file["file_path"] == "models/custom":
                    models_out.append("- **{}** (v{}): {}".format(model, models[model]["version"], models[model]["description"]))
                    break

    models_out.sort()
    cog.out("\n".join(models_out))
    ]]] -->
    - **3DKX** (v1.1): SFW model with limited nsfw capabilities (suggestive nsfw) that is highly versatile for 3D renders.
    - **ACertainThing** (v1.0): An improved version of Anything v3 made with ACertainThing, focusing on scenes rather than characters
    - **AIO Pixel Art** (v1): Stable Diffusion fine tuned on pixel art sprites and scenes
    - **Analog Diffusion** (v1.0): A dreambooth model trained on a diverse set of analog photographs
    - **Anygen** (v3.7): A best of both worlds - merging the anime of Anything v3 with Protogens photorealism - VAE is included
    - **Anything Diffusion** (v4.5): Highly detailed Anime styled generations
    - **App Icon Diffusion** (v1): Dreambooth model fine tuned on mobile app icons
    - **Arcane Diffusion** (v3): Based on the Arcane TV show
    - **Archer Diffusion** (v1): Based on the Archer's TV show animation style
    - **Asim Simpsons** (v1.0): The Simpsons dreambooth model
    - **Balloon Art** (v1.0): This is the fine-tuned Stable Diffusion model trained on Twisted Balloon images
    - **Borderlands** (v1): Based on Borderlands video game style, trained on characters and scenes
    - **BubblyDubbly** (v1): Dreamy sketched/painted portraits
    - **CharHelper** (v4): This model was trained on a digital painting style mainly with characters and portraits. The main objective is to train a model to be a tool to help with character design ideas
    - **ChromaV5** (v1.6): generates metalic/chrome looking images
    - **Classic Animation Diffusion** (v1): Popular animation studio classic style generations.
    - **Clazy** (v1): Generates clay-like figures
    - **Comic-Diffusion** (v2): Western Comic book style
    - **Concept Sheet** (valpha): This model is just the first dreambooth iteration for concept-sheet/old-books style. Based on SD 2.1
    - **Counterfeit** (v2.0): Counterfeit is anime style Stable Diffusion model
    - **Cyberpunk Anime Diffusion** (v1): Cyberpunk anime characters
    - **DGSpitzer Art Diffusion** (v1): Dreambooth model based on Vintedois, trained on a dataset of DGSpitzer art. Styles included are outline, sketch, anime, painting and landscape
    - **Dan Mumford Style** (v2): Model trained with a dataset of DanMumford Style images, courtesy of Flonix
    - **Dark Victorian Diffusion** (v2.0): finetuned on dark, moody, victorian imagery
    - **Darkest Diffusion** (v1.0): A free and open source Stable Diffusion model created by AI-Characters, trained on the artstyle of the game 'Darkest Dungeon'
    - **Deliberate** (v1.1): This model provides you the ability to create anything you want. The more power of prompt knowledges you have, the better results you'll get. It basically means that you'll never get a perfect result with just a few words. You have to fill out your prompt line extremely detailed
    - **DnD Item** (v1.0): This is a model (dnditem) for creating magic items, for the game Dungeons and Dragons! It was trained to be very similar to the official results that are available here: https://www.dndbeyond.com/magic-items
    - **Double Exposure Diffusion** (v2.0): The Double Exposure Diffusion model, trained specifically on images of people and a few animals
    - **DreamLikeSamKuvshinov** (v1): A mixture of Dreamlike Diffusion 1.0, SamDoesArt V3 and Kuvshinov style models.  Created mostly for exploring different character concepts with a focus on drawings, but the mix happened to be pretty good at realistic-ish images, all thanks to wonderful models that it uses.
    - **Dreamlike Diffusion** (v1.0): Dreamlike Diffusion 1.0 is SD 1.5 fine tuned on high quality art, made by dreamlike.art
    - **Dreamlike Photoreal** (v2.0): Dreamlike Photoreal 1.0 is a photorealistic Stable Diffusion 1.5 model fine tuned on high quality photos, made by dreamlike.art.
    - **Dreamshaper** (v3.3): Merged model mix of Midnight mixer, roboEtics, f222, elldrethSLucidMix, Seek.ART Mega, rpg, hassanBlend, modelshoot and roboDiffusion
    - **DucHaiten** (v1.1): DucHaiten's character generation model
    - **Dungeons and Diffusion** (v3): Generates D&D styled characters, trained on art commissions
    - **Eimis Anime Diffusion** (v1): This model is trained with high quality and detailed anime images
    - **Elden Ring Diffusion** (v2): Based on the Elden Ring video game style
    - **Elldreth's Lucid Mix** (v1.0): It's an all-around easy-to-prompt general purpose semi-realistic to realistic model that cranks out some really nice images. No trigger words required
    - **Epic Diffusion** (v1.1): Epic Diffusion is a general purpose model based on Stable Diffusion 1.x intended to replace the official SD releases as your default model. It is focused on providing high quality output in a wide range of different styles, with support for NFSW content.
    - **Eternos** (v1.0): A surrealist / Minimalist model
    - **Fantasy Card Diffusion** (v1): fantasy trading card style art, trained on all currently available Magic: the Gathering card art
    - **Funko Diffusion** (v1.0): Stable Diffusion fine tuned on Funko Pop, by PromptHero.
    - **Furry Epoch** (v4): Furry styled generations.
    - **Future Diffusion** (v1.0): This creates high quality 3D images with a futuristic Sci-Fi theme
    - **GTA5 Artwork Diffusion** (v1.0): This model was trained on the loading screens, gta storymode, and gta online DLCs artworks. Which includes characters, background, chop, and some objects. The model can do people and portrait pretty easily, as well as cars, and houses. For some reasons, the model stills automatically include in some game footage, so landscapes tend to look a bit more game-like.
    - **GTM Ultimate Blend** (v3): GalaxyTimeMachine's GTM Ultimate Blend - a generalist model good at portraits, scenery with a fantasy vibe
    - **Ghibli Diffusion** (v1): fine-tuned Stable Diffusion model trained on images from Studio Ghibli feature films
    - **Guohua Diffusion** (v1): fine-tuned Stable Diffusion model trained on traditional Chinese paintings
    - **HASDX** (v1.0): He merged a few checkpoints and got something buttery and amazing. Does great with things other then people too. It can do anything really. It doesn't need crazy prompts either. Keep it simple. No need for all the artist names and trending on whatever.
    - **Hassanblend** (v1.5): This model was for creating people
    - **Healy's Anime Blend** (v1.0): This is a blend of some anime models mixed with 'realistic' stuff
    - **Hentai Diffusion** (v19): Anime focused model with better hands, obscure poses/camera angles and consistent style
    - **Inkpunk Diffusion** (v2): inspired by Gorillaz art, FLCL and Yoji Shinkawa. Trained on images generated from Midjourney
    - **JWST Deep Space Diffusion** (v1): Stable Diffusion fine tuned on JWST imagery
    - **Knollingcase** (v1): generates a glass display case with objects inside, inspired by Sean Preston. Trained on Midjourney images
    - **Lawlas's yiff mix** (v1): Based on yiffy-e18 and Anything, produces sfw/nsfw furry anthro artworks of different styles with consistant quality, while maintaining details on stuff like clothes, background, etc. with simpler prompts.
    - **Marvel Diffusion** (v2): This model was trained on images from the animated Marvel Disney+ show What If, which includes characters, background, and some objects
    - **Mega Merge Diffusion** (v1): SD 1.5 merged with 17 other models
    - **Microscopic** (v1.0): This is the fine-tuned Stable Diffusion model trained on microscopic images
    - **Microworlds** (v1): Isometric microworlds
    - **Midjourney Diffusion** (v1): Stable Diffusion fine tuned on Midjourney v4 images
    - **Midjourney PaintArt** (v1): Midjourney v4 painting style
    - **Min Illust Background** (v1.0): This fine-tuned Stable Diffusion v1.5 model was trained on a selection of artistic works by Sin Jong Hun
    - **ModernArt Diffusion** (v1.0): You can use this model to generate modernart style images
    - **Moedel** (v2): Moe.del produces cute female characters. It is also a mix of Stable Diffusion 1.4/1.5 in different proportions so you can challenge it to generate for you pretty much anything using regular SD prompts (like cute dogs, cats etc.)
    - **MoistMix** (v1.0): A do (almost) anything model
    - **Nitro Diffusion** (v1): Multi-Style model trained on Arcane, Archer and Mo-Di
    - **Openniji** (v1.0): The Stable Diffusion model trained on Nijijourney images
    - **PFG** (v1.11): NSFW Model for realistic and Hentai images
    - **PPP** (v1.0): PPP is a realistic model merge, tested and tweaked for human females. Mostly based on NSFW models
    - **Papercut Diffusion** (v1): Stable Diffusion fine tuned on Paper cut images
    - **Papercutcraft** (v1): Paper Cut Craft is a fine tuned Stable Diffusion model trained on Midjourney images
    - **Pastel Mix** (v1): The model is trained with beautiful, artist-agnostic watercolor images using the midjourney method
    - **Poison** (v1): Anything Diffusion fine-tuned to produce high-quality realistic anime styled images
    - **Pokemon3D** (v1): This model was trained on Gen 1-8 Pokemon low poly renders
    - **PortraitPlus** (v1.0): This is a dreambooth model trained on a diverse set of close to medium range portraits of people.
    - **ProtoGen** (v5.3): One Step Closer to Reality
    - **Protogen Infinity** (v8.6): Protogens photorealism mixed with more science fiction, comic, and synthwave to make ultimate awesomeness
    - **RPG** (v2): portraits of charecters in the style of the game Baldur's Gate
    - **Ranma Diffusion** (v1): imitates the style of late '80s early 90's anime, Anything v3 base
    - **Realistic Vision** (v1.2): Model for creating photorealistic humans
    - **Redshift Diffusion** (v1): Dreambooth model trained on high resolution 3D artworks
    - **Robo-Diffusion** (v1): Robot oriented drawing style
    - **Samdoesarts Ultmerge** (v1): Portraits in the style of Sam Yang, merged with chewtoy and orange code's models
    - **Sci-Fi Diffusion** (v1.0): A Sci-Fi themed model trained on SD 1.5 with a 26K+ image dataset
    - **Seek.art MEGA** (v1.0): Seek.art MEGA is a general use 'anything' model that significantly improves on 1.5 across dozens of styles. Created by Coreco at seek.art
    - **Smoke Diffusion** (v1.0): This is the fine-tuned Stable Diffusion model trained on images of smoke
    - **Sonic Diffusion** (v2): SonicDiffusionV2.ckpt was trained on AnythingV3 for 200 epochs of 203 hand captioned Sonic images from various artists
    - **Spider-Verse Diffusion** (v1): Based on the Into the Spider-Verse movie's animation style
    - **Squishmallow Diffusion** (v1): Squishmallows
    - **Supermarionation** (v2.0): This is a fine-tuned Stable Diffusion model (based on v1.5) trained on screenshots from Gerry Anderson Supermarionation stop motion animation movie, basically from Thunderbirds tv series
    - **Sygil-Dev Diffusion** (v0.2): This model is a Stable Diffusion v1.5 fine-tune trained on the Imaginary Network Expanded Dataset. It is an advanced version of Stable Diffusion and can generate nearly all kinds of images, no matter humans, reflections, cities, architecture, fantasy, digital arts, landscapes, or nature views.
    - **Synthwave** (v1): Stable Diffusion model to create images in Synthwave/outrun style
    - **T-Shirt Diffusion** (v1): Generates t-shirt logos, base model is vintedois-diffusion with additional training on t-shirt logos size 640x640px
    - **Trinart Characters** (v2.0): Derrida (formerly TrinArt Characters v2) is a stable diffusion v1-based model that was further improved on the previous characters v1 model. While this is still a versatility and compositional variation anime/manga model like other TrinArt models, when compared to the v1 model, Derrida was focused on more anatomical stability and slightly less on variation due to further multi-epoch training and finetuning.
    - **Tron Legacy Diffusion** (v1): Tron Legacy movie style
    - **Ultraskin** (v0.9): This model will add a LOT of skin detail compared to SD 2.1. Sometimes this makes images look more realistic, sometimes less realistic!
    - **Valorant Diffusion** (v1.0): This model was trained on the Valorant agents splash arts, and some extra arts on the official website
    - **Van Gogh Diffusion** (v1): Stable Diffusion model trained on screenshots from the film Loving Vincent, best results with k_euler sampler
    - **Vintedois Diffusion** (v0.1): Vintedois (22h) Diffusion model trained by Predogl and piEsposito with open weights, configs and prompts (as it should be).  This model was trained on a large amount of high quality images with simple prompts to generate beautiful images without a lot of prompt engineering.
    - **Vivid Watercolors** (v1): The model is trained with beautiful, artist-agnostic watercolor images using the midjourney method
    - **Voxel Art Diffusion** (v1): Stable Diffusion fine-tuned on voxel art style
    - **Wavyfusion** (v1): dreambooth model trained on a very diverse dataset ranging from photographs to paintings
    - **Xynthii-Diffusion** (v1): Xynthii-Diffusion (cyclops monster girls)
    - **Yiffy** (v18): Furry styled generations.
    - **Zack3D** (v1): Kink/NSFW oriented furry styled generations.
    - **Zeipher Female Model** (v222): For creating images of nude solo women. Also known as f222
    - **Zelda BOTW** (v1): based off work of great artworks from Legend of Zelda: Breath of The Wild
    - **colorbook** (v1): Minimalist coloring book style images
    - **kurzgesagt** (v1): A DreamBooth finetune of Stable Diffusion v1.5 model trained on a bunch of stills from Kurzgesagt videos
    - **mo-di-diffusion** (v1): Popular animation studio modern style generations.
    - **pix2pix** (v1): Model specifically trained for pix2pix use
    - **trinart** (v1): Manga styled generations.
    - **vectorartz** (v1): Generate beautiful vector illustration
    - **waifu_diffusion** (v1.3): Anime styled generations.
    <!-- [[[end]]] -->
    </details>
- <details><summary>Post processing:</summary>

    - **CodeFormers** (v0.1.0): Face restoration
    - **GFPGAN** (v1.4): Face restoration
    - **RealESRGAN_x4plus** (v0.1.0): Upscaling
    </details>

## How to install it

In the Web UI, go to the `Extensions` tab, `Available`, load the list, find `Stable Horde Client` and click `Install`.

## How to use it

**To prevent loading the local models, add `--ui-debug-mode` to `COMMANDLINE_ARGS`**. *This will raise an exception `AttributeError: 'NoneType' object has no attribute 'process_texts'` whenever the prompts change, but it can be safely ignored*.

1. If you [registered an account](https://stablehorde.net/register), go to the `Stable Horde Settings` tab and set your `API key`. Leaving the default value will connect anonymously, which is limited.
2. Go to either the `txt2img` or the `img2img` tab and select `Run on Stable Horde` in the `Script` option. Without this option, it will run locally.
3. Set all parameters, both regular and Stable Horde's, and click `Generate`.

For more information about Stable Horde, workers or kudos, check [their FAQ](https://github.com/db0/AI-Horde/blob/main/FAQ.md).
