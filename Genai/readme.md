## Music 

```python
from transformers import AutoProcessor, MusicgenForConditionalGeneration

processor = AutoProcessor.from_pretrained("facebook/musicgen-small")
model = MusicgenForConditionalGeneration.from_pretrained("facebook/musicgen-small")

inputs = processor(
    text=["80s pop track with bassy drums and synth", "90s rock song with loud guitars and heavy drums"],
    padding=True,
    return_tensors="pt",
)

audio_values = model.generate(**inputs, max_new_tokens=256)

from IPython.display import Audio

sampling_rate = model.config.audio_encoder.sampling_rate
Audio(audio_values[0].numpy(), rate=sampling_rate)

```




## Recipe Generater
```python


import gradio as gr
from PIL import Image
from transformers import BlipProcessor, BlipForConditionalGeneration
from transformers import GPT2LMHeadModel, GPT2Tokenizer
import torch


caption_processor = BlipProcessor.from_pretrained("Salesforce/blip-image-captioning-base")
caption_model = BlipForConditionalGeneration.from_pretrained("Salesforce/blip-image-captioning-base")


recipe_tokenizer = GPT2Tokenizer.from_pretrained("gpt2")
recipe_model = GPT2LMHeadModel.from_pretrained("gpt2")

def image_to_recipe(image):
    image = image.convert("RGB")
    inputs = caption_processor(images=image, return_tensors="pt")
    caption_ids = caption_model.generate(**inputs)
    caption = caption_processor.decode(caption_ids[0], skip_special_tokens=True)

    
    prompt = f"Write a detailed recipe for: {caption}\n\nIngredients:\n"
    inputs = recipe_tokenizer(prompt, return_tensors="pt")
    output = recipe_model.generate(**inputs, max_length=250, do_sample=True, temperature=0.9)
    recipe = recipe_tokenizer.decode(output[0], skip_special_tokens=True)

    return f"**Caption:** {caption}\n\n **Recipe:**\n{recipe}"

gr.Interface(
    fn=image_to_recipe,
    inputs=gr.Image(type="pil", label="Upload Food Image"),
    outputs=gr.Markdown(),
    title="AI Image to Recipe Generator",
    description="Upload a food image, and the AI will generate a caption + Recipe"
).launch()

```



## Voice Generation
```python

from transformers import AutoProcessor, AutoModel

processor = AutoProcessor.from_pretrained("suno/bark-small")
model = AutoModel.from_pretrained("suno/bark-small")

inputs = processor(
    text=["Hello, my name is Suno. And, uh — and I like pizza. [laughs] But I also have other interests such as playing tic tac toe."],
    return_tensors="pt",
)

speech_values = model.generate(**inputs, do_sample=True)

from IPython.display import Audio

sampling_rate = model.generation_config.sample_rate
Audio(speech_values.cpu().numpy().squeeze(), rate=sampling_rate)
```


## text to image

```python
from transformers import pipeline
import torch
from diffusers import DiffusionPipeline

# Load the image generation pipeline using diffusers
generator = DiffusionPipeline.from_pretrained("CompVis/stable-diffusion-v1-4")
generator.to("cuda")

# Generate an image from the text prompt
prompt = "A beautiful landscape with mountains and a lake"
image = generator(prompt).images[0]
display(image)

```



## Pac Man Controll 
https://storage.googleapis.com/tfjs-examples/webcam-transfer-learning/dist/index.html


## Filter
https://holobooth.flutter.dev/















## Text To Image

<img width="1104" height="736" alt="image" src="https://github.com/user-attachments/assets/d73afeba-8e05-4bea-8b11-c68b1631bfda" />

## Text To Audio

<img width="1211" height="494" alt="image" src="https://github.com/user-attachments/assets/37437b61-640d-485d-9e83-9530e3398c74" />


## Suno Bark/Voice Generation


