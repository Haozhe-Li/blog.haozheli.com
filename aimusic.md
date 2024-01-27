# Generative AI Audio

## Music generation

Although there are many AI music creation tools on the market, the vast majority of them can only generate Tracks based on a few selected Moods or Instruments, more for the convenience of the music creator (e.g. writing a Beat for a Rap). As a result most AI music generation tools don't support control via text, or if they do they have very little freedom to do so. Here are some options I've found so far that allow you to control music with text:

### MusicLM by Google

- **Links:** [MusicLM blog introduction](https://blog.google/technology/ai/musiclm-google-ai-test-kitchen/), [MusicLM (online text to muzic example using MuzicLM)]( https://aitestkitchen.withgoogle.com/tools/music-fx), [Unofficial Github open source project](https://github.com/lucidrains/musiclm-pytorch)

- **Introduction:** A model developed by **Google** to extend a melody, an existing work, or generate a melody from the input text from scratch.

- **Advantages**:

- Can be controlled by **Text**, i.e. music can be generated using a piece of Prompt.

- Can generate up to **48kHZ sample rate** music, to meet most of the digital music standards.

- You can select **seamless loop** music playback.

- **Disadvantages**:

- After entering text and clicking Generate, Google will "optimize" the entered Prompt. But this will miss many details of the Prompt: as far as experience goes, Google will only recognize Prompts like Optimistic Music, Guitar, Piano and other very specific music, style indications as keywords, and the subsequent generation will be based entirely on the previously mentioned **keywords**. This makes it **impossible** for us to fully control the generation of music using **Prompt.

- **Maximum 70 seconds of music generated**, but this can be compensated for with the previously mentioned seamless looping.

- The generated music is rather strange to listen to, and I personally think that at this stage MusicLM is still mainly in the **Playability stage**, e.g. typing: "Mozart music in the style of Beethoven" or something like that is problematic, but still mainly entertaining.

- There is no **external formal API**. I found [this project](https://github.com/armintum/MusicLM) on Github, but this is a reverse API based on Google login information.

### Musicgen by Meta

- **Links:** [Official website](https://musicgen.com), [Github](https://github.com/facebookresearch/audiocraft/blob/main/docs/MUSICGEN.md), [ HuggingFace Online Experience](https://huggingface.co/spaces/facebook/MusicGen)

- **Introduction:** Music generation model developed by Meta, GitHub open source, built-in ten pre-trained models, can be used on HuggingFace using the API to call directly or can be used locally.

- ** Advantages:** **.

- The **best** text-music program I've found so far that uses text control.

- There are **multiple sizes of models** from 300M to 3.3B.

- Music generation is clearly capable of being much stronger than MusicLM**** with the exact same Prompt.

- Supports **Stereo**.

- HuggingFace provides **API**, easy to use, the following is a call small model of the sample.

````python

import requests

API_URL = "https://api-inference.huggingface.co/models/facebook/musicgen-small"

headers = {"Authorization": "Bearer YOUR_API_TOKEN"}

def query(payload).

response = requests.post(API_URL, headers=headers, json=payload)

return response.content

prompt = f'''

Instrument: electro guitar, strings, orchestra, cello, violin and piano

Mood: upbeating, cinematic

Context: An explorer is climbing Mount Everest.

'''

audio_bytes = query({

"inputs": prompt,

})

output_file_path = "generated_music.wav"

with open(output_file_path, "wb") as audio_file.

audio_file.write(audio_bytes)

# will output a .wav audio file

````

- Available in the local **Transformers Library**.

- Supports your own **Training**, **Fine-Tuning**, and so on.

- **Disadvantages:**

- API is provided by a third party, **not very stable** and **hours are limited**, it is recommended to use it locally.

- Can not be **seamless**, actual use may need to do a cross-stacking.

- **Maximum support 32kHZ**, the sound quality is not as good as MusicLM, but it should be enough.

### MuseCoCo

- **Links:** [MuseCoCo Introduction](https://ai-muzic.github.io/musecoco/), [MuseCoCo Github](https://github.com/microsoft/muzic/blob/main/musecoco/ README.md)

- **Introduction:** MuseCoCo, a project under Microsoft Muzic, converts input text to Attributes and then to sheet music.

- **Advantages:**

- According to the Sample provided by MuseCoCo itself, it is definitely better than **Google Bard and GPT-4** in generating sheet music (to be played with other software), although I don't think the latter two have the ability to make music. Both the level of understanding of Prompt, the stylization of the finished product, and the musicality are better than Bard & GPT-4.

- **GitHub Open Source** and posted [Paper](https://doi.org/10.48550/arXiv.2306.00110).

- **Cons:**

- Generates **scores**, not music. If you want to use it you also need a third party software, technical platform to play the music.

### Bark by Suno AI

- **Links:** [Official website (can be experienced)](https://www.suno.ai), [Github](https://github.com/suno-ai/bark), [HuggingFace (can be experienced)](https://huggingface.co/ spaces/suno/bark)

- **Introduction:** A generative text-to-audio model developed by Suno AI.

- **Benefits:**

- The best **comprehensive program** found so far.

- Not only can you **generate music**, you can **generate vocals**, **sound effects**. The control of vocals is very free, you can use ``[]`` to control the tone of the vocals and so on.

- The quality of the generated **music** is good** and you can create your own music with lyrics given the Prompt. For classical and romantic music generation is slightly inferior, but in pop music generation results are very good, the level can reach the traditional sense of European and American music pop spit songs.

- **Github open source**, can be used locally, also provided in the Transformers Library.

- You can use HuggingFace's **API**, currently do not see the official provision of API.

- Support for many syntax can be generated at the same time sound effects, vocal music and so on, as follows:

````markdown

[laughter]

[laughs]

[sighs]

[music]

[gasps]

[clears throat]

- or ... for hesitations

♪ for song lyrics

♪ capitalization for emphasis of a word

MAN/WOMAN: for bias towards speaker

````

- **Weaknesses:**

- Music generation quality is not as good as **MusicGen**.

- No stable **API**.

## Sound generation

Here are some sound effect generation options I've found.

### Bark by Suno AI (previously mentioned, not to be repeated)

### Audiobox by Meta

- **Links:** [Official Website](http://audiobox.metademolab.com), [Blog](https://ai.meta.com/blog/audiobox-generating-audio-voice-natural-language- prompts/), [Paper](https://ai.meta.com/research/publications/audiobox-unified-audio-generation-with-natural-language-prompts/)

- **Introduction:** Text-to-audio modeling developed by Meta

- **Advantages:**

- Generates sound effects, speech, etc. directly from text and **works well**.

- For the generation of language, the effect of language (Prompt) and the actual content of the separation of input, more conducive to **Automation of access**.

- Can be based on the existing audio **secondary creation **.

- **Disadvantages:**

- Written **Open Source but not to find actual projects**, only Demos and Papers.

- Recently the site Demo seems to be **closed**, visit will prompt ``This site is not available in your region``.

## Practical use

Currently I think a more viable option is to use Suno AI's **Bark**, the general process is as follows:

### Music generation:

1. Give the in-game AI some prompts, so that it will output a text indicating the current atmosphere and background of the game (e.g. "Mysterious, the detective is working on a case", or "Exciting, the samurai are dueling", etc.).

2. For each game, the creator should set up the instruments needed for the soundtrack in advance. As of now, the AI (at least GPT-4) gives strange music orchestration, but of course this part can be generated by the AI.

3. Hand over the text from the AI above to Bark, where it can be automated using code, either by calling the Bark API given by HuggingFace, or by running it locally to generate the audio. Audio generation should start with the `♪ ` symbol.

4. Because it takes time to generate the audio, the actual music generated may need to be looped with stacking.

The above music generation can also be done using Meta's **MusicGen**.

### Sound generation or vocals:

1. Again, use Prompt to have the AI output a piece of text, the text that the character is speaking, and a sound effect, e.g. `Welcome to today's meeting [cough] [applause]`.

2. Give the above text to Bark to generate.

## End

Thanks for reading, these are some of my simple research on AI generated audio and music.
