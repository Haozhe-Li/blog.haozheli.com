# 生成式 AI 音频



## 音乐生成

虽然市面上有许多的AI音乐创作工具，但是绝大部分都只能根据几个选定的Mood或者是Instruments来生成Track，更多是为了方便音乐创作者（例如给Rap写Beat）。因此大多数的AI音乐生成工具都不支持通过文本进行控制，或者是即使可以但是自由度很低。以下是我目前找到的一些可以用文本控制音乐的方案：



### MusicLM by Google

- **链接：**[MusicLM 博客介绍](https://blog.google/technology/ai/musiclm-google-ai-test-kitchen/), [MusicLM（使用MuzicLM的在线text to muzic示例）](https://aitestkitchen.withgoogle.com/tools/music-fx)，[非官方的Github开源项目](https://github.com/lucidrains/musiclm-pytorch)
- **介绍：**由**Google**开发的模型，可以将旋律、已有的作品进行扩展，或者从输入的文本从零开始生成一段旋律。
- **优点**：
  - 可以通过**文本控制**，即使用一段Prompt可以生成音乐。
  - 最高可以生成**48kHZ采样率**的音乐，达到绝大部分数字音乐标准。
  - 可以选择**无缝循环**音乐播放。
- **缺点**：
  - 在输入文本点击生成后，Google会对于输入的Prompt进行“优化”。但是这会遗漏许多Prompt的细节：就目前经验来看，Google只会对Prompt中类似于Optimistic Music, Guitar, Piano等非常明确的乐曲、风格指示识别成关键词，并且后续的生成也是完全基于前文提及的的**关键词**。这样我们就**无法完全使用**Prompt控制音乐的生成。
  - **最多生成70秒的音乐**，但是这个可以用前文提及的无缝循环弥补。
  - 生成的音乐听感比较奇怪，个人认为现阶段MusicLM主要还是在**可玩性阶段**，例如输入：“贝多芬风格的莫扎特音乐”之类的问题，还是以娱乐为主。
  - 没有**对外正式的API**。我在Github上找到了[这个项目](https://github.com/armintum/MusicLM)，但这个是基于Google登录信息的反向API。



### Musicgen by Meta

- **链接：**[官网](https://musicgen.com)， [Github](https://github.com/facebookresearch/audiocraft/blob/main/docs/MUSICGEN.md)，[HuggingFace在线体验](https://huggingface.co/spaces/facebook/MusicGen)

- **介绍：**由Meta开发的音乐生成模型，GitHub开源，内置了十个预训练模型，可以在HuggingFace上使用API直接调用也可以本地使用。

- **优点：**

  - 目前我发现的用文本控制的**最好**的文本-音乐方案。
  - 有**多个大小的模型**，从300M到3.3B。
  - 音乐生成在Prompt完全一样的情况下明显能够比MusicLM**强很多**。
  - 支持**立体声Stereo**。
  - 有HuggingFace提供的**API**，使用便捷，以下是一个调用small模型的sample。

  ````python
  import requests
  
  API_URL = "https://api-inference.huggingface.co/models/facebook/musicgen-small"
  headers = {"Authorization": "Bearer YOUR_API_TOKEN"}
  def query(payload):
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
  with open(output_file_path, "wb") as audio_file:
      audio_file.write(audio_bytes)
  # will output a .wav audio file
  ````

  - 可以本地**Transformers Library**使用。
  - 支持自己**训练**、**Fine-Tuning**等等。

- **缺点：**

  - API是第三方提供的，**不是很稳定**且**时长有限制**，建议还是本地用。
  - 不能**无缝衔接**，实际使用可能需要做一个交叉叠化。
  - **最高支持32kHZ**，音质不如MusicLM但是应该够用。



### MuseCoCo

- **链接：**[MuseCoCo介绍](https://ai-muzic.github.io/musecoco/)，[MuseCoCo Github](https://github.com/microsoft/muzic/blob/main/musecoco/README.md)
- **介绍：**微软Muzic下的项目MuseCoCo，可以将输入的文本转换成Attributes然后在转换为乐谱。
- **优点：**
  - 根据MuseCoCo自己提供的Sample中，在生成乐谱（用其他软件演奏）上**绝对强于**Google Bard与GPT-4，虽然我并不认为后两者有做音乐的能力。无论是对Prompt的理解程度，还是成品的风格化以及音乐性都要比Bard与GPT-4强。
  - **GitHub开源**，并且发了[Paper](https://doi.org/10.48550/arXiv.2306.00110)。
- **缺点：**
  - 生成的是**乐谱**，而不是音乐。如果想要使用还需要第三方的软件、技术平台演奏乐曲。



### Bark by Suno AI

- **链接：**[官网（可以体验）](https://www.suno.ai)，[Github](https://github.com/suno-ai/bark)，[HuggingFace（可以体验）](https://huggingface.co/spaces/suno/bark)

- **介绍：**由Suno AI开发的一个生成性文字-音频的模型。

- **优点：**

  - 目前发现最好的**综合方案**。

  - 不仅仅可以**生成音乐**，可以**生成人声**、**音效**。对于人声的控制很自由，可以用``[]``来控制人声的语气等等。

  - 生成的**音乐质量不错**，可以在给定Prompt的条件下自己创造出有歌词的音乐。对于古典、浪漫主义音乐生成略逊，但是在流行音乐生成结果很不错，水平可以达到传统意义上欧美音乐的流行口水歌。

  - **Github开源**，可以本地使用，也提供在了Transformers Library中。

  - 可以使用HuggingFace的**API**，目前没见到官方提供API。

  - 支持很多语法可以同时生成音效、人声音乐等等，具体如下：

    ````markdown
    [laughter]
    [laughs]
    [sighs]
    [music]
    [gasps]
    [clears throat]
    — or … for hesitations
    ♪ for song lyrics
    capitalization for emphasis of a word
    MAN/WOMAN: for bias towards speaker
    ````

- **缺点：**

  - 音乐生成质量不如**MusicGen**。
  - 没有稳定的**API**。



## 音效生成

以下是我发现的一些音效生成的方案。

 ### Bark by Suno AI （前文已经提及，不再赘述）



### Audiobox by Meta

- **链接：** [官网](http://audiobox.metademolab.com)，[博客](https://ai.meta.com/blog/audiobox-generating-audio-voice-natural-language-prompts/)，[Paper](https://ai.meta.com/research/publications/audiobox-unified-audio-generation-with-natural-language-prompts/)
- **介绍：**由Meta开发的文本-音频模型
- **优点：**
  - 直接通过文本生成音效、语音等，且**效果不错**。
  - 对于语言的生成，语言的效果（Prompt）和实际内容分离输入，更利于**自动化的接入**。
  - 可以在现有的音频基础上进行**二次创作**。
- **缺点：**
  - 写的是**开源但是并为找到实际项目**，仅有Demo和Paper。
  - 近期网站Demo貌似**关闭**了，访问会提示``This site is not available in your region``。





## 实际使用

目前我认为比较可行的方案是使用Suno AI的**Bark**，大致流程如下：



### 音乐生成：

1. 给游戏中的AI一些Prompt，使其会输出一段文本，指明当前游戏的气氛以及背景（例如“神秘的，侦探正在办案”，或者是“激昂的，武士正在决斗”等）。
2. 对于每个游戏，创作者应该提前设置好背景音乐需要的乐器。以目前来看，AI（至少是GPT-4）给出的音乐配器会比较奇怪，当然这一部分也可以用AI生成。
3. 将上文AI输出的文本交给Bark。在这里可以使用代码进行自动化处理，可以调取HuggingFace所给的Bark的API，或者是本地运行生成音频。音频生成需要以`♪ `符号开头。
4. 因为生成音频需要时间，所以实际生成的音乐可能需要做叠化处理循环播放。



上述的音乐生成也可以采用Meta的**MusicGen**。



### 音效生成或者是人声：

1. 同样是使用Prompt让AI输出一段文本，人物说话的文本以及音效，例如`欢迎大家来到今天的会议[咳嗽][掌声]`。
2. 将上述文本交给Bark生成。





## 结束

感谢阅读，以上是我对于AI生成音频、音乐的一些简单的调研。

