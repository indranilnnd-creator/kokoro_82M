---
license: apache-2.0
language:
- en
base_model:
- yl4579/StyleTTS2-LJSpeech
pipeline_tag: text-to-speech
---
🚨 **This repository is undergoing maintenance.**

✨ Model v1.0 release is underway! Things are not yet finalized, but you can start [using v1.0 now](https://huggingface.co/hexgrad/Kokoro-82M#usage).

✨ You can now [`pip install kokoro`](https://pypi.org/project/kokoro/), a dedicated inference library: https://github.com/hexgrad/kokoro

✨ You can also [`pip install misaki`](https://pypi.org/project/misaki/), a G2P library designed for Kokoro: https://github.com/hexgrad/misaki

♻️ You can access old files for v0.19 at https://huggingface.co/hexgrad/kLegacy/tree/main/v0.19

❤️ Kokoro Discord Server: https://discord.gg/QuGxSWBfQy

### Kokoro is getting an upgrade!

| Model | Published | Training Data | Compute (A100 80GB) | Released Voices | Released Langs |
| ----- | --------- | ------------- | ------------------- | --------------- | -------------- |
| v0.19 | 2024 Dec 25 | <100 hrs | 500 hrs @ $400 | 10 | 1 |
| **v1.0** | 2025 Jan 27 | Few hundred hrs | 1000 hrs @ $1000 | [27+](https://huggingface.co/hexgrad/Kokoro-82M/blob/main/VOICES.md) | [2+](https://huggingface.co/hexgrad/Kokoro-82M/blob/main/VOICES.md) |

Training is continuous. The v0.19 model was produced "on the way" to the v1.0 model, so the Compute footprints overlap.

### Voices and Languages

Voices are listed in [VOICES.md](https://huggingface.co/hexgrad/Kokoro-82M/blob/main/VOICES.md). Not all voices are created equal:
- Subjectively, voices will sound better or worse to different people.
- Objectively, having less training data for a given voice (minutes instead of hours) lowers inference quality.
- Objectively, poor audio quality in training data (compression, sample rate, artifacts) lowers inference quality.
- Objectively, text-audio misalignment alignment (too much text i.e. hallucinations, or not enough text i.e. failed transcriptions) lowers inference quality.

Support for non-English languages may be absent or thin due to weak G2P and/or lack of training data. Some languages are only represented by a small handful or even just one voice (French).

### Usage

The following can be run in a single cell on [Google Colab](https://colab.research.google.com/).
```py
# 1️⃣ Install kokoro
!pip install -q kokoro soundfile
# 2️⃣ Install espeak, used for out-of-dictionary fallback
!apt-get -qq -y install espeak-ng > /dev/null 2>&1
# You can skip espeak installation, but OOD words will be skipped unless you provide a fallback

# 3️⃣ Initalize a pipeline
from kokoro import KPipeline
from IPython.display import display, Audio
import soundfile as sf
# 🇺🇸 'a' => American English
# 🇬🇧 'b' => British English
pipeline = KPipeline(lang_code='a') # make sure lang_code matches voice

# The following text is for demonstration purposes only, unseen during training
text = '''
The sky above the port was the color of television, tuned to a dead channel.
"It's not like I'm using," Case heard someone say, as he shouldered his way through the crowd around the door of the Chat. "It's like my body's developed this massive drug deficiency."
It was a Sprawl voice and a Sprawl joke. The Chatsubo was a bar for professional expatriates; you could drink there for a week and never hear two words in Japanese.

These were to have an enormous impact, not only because they were associated with Constantine, but also because, as in so many other areas, the decisions taken by Constantine (or in his name) were to have great significance for centuries to come. One of the main issues was the shape that Christian churches were to take, since there was not, apparently, a tradition of monumental church buildings when Constantine decided to help the Christian church build a series of truly spectacular structures. The main form that these churches took was that of the basilica, a multipurpose rectangular structure, based ultimately on the earlier Greek stoa, which could be found in most of the great cities of the empire. Christianity, unlike classical polytheism, needed a large interior space for the celebration of its religious services, and the basilica aptly filled that need. We naturally do not know the degree to which the emperor was involved in the design of new churches, but it is tempting to connect this with the secular basilica that Constantine completed in the Roman forum (the so-called Basilica of Maxentius) and the one he probably built in Trier, in connection with his residence in the city at a time when he was still caesar.
'''

# 4️⃣ Generate, display, and save audio files in a loop.
generator = pipeline(
    text, voice='af_bella',
    speed=1, split_pattern=r'\n+'
)
for i, (gs, ps, audio) in enumerate(generator):
    print(i)  # i => index
    print(gs) # gs => graphemes/text
    print(ps) # ps => phonemes
    display(Audio(data=audio, rate=24000, autoplay=i==0))
    sf.write(f'{i}.wav', audio, 24000) # save each audio file
```

### Model Facts

**Architecture:**
- StyleTTS 2: https://arxiv.org/abs/2306.07691
- ISTFTNet: https://arxiv.org/abs/2203.02395
- Decoder only: no diffusion, no encoder release

**Architected by:** Li et al @ https://github.com/yl4579/StyleTTS2

**Trained by**: `@rzvzn` on Discord

**Supported Languages:** American English, British English

**Model SHA256 Hash:** `496dba118d1a58f5f3db2efc88dbdc216e0483fc89fe6e47ee1f2c53f18ad1e4`

### Training Details

**Compute:** About $1000 for 1000 hours of A100 80GB vRAM

**Data:** Kokoro was trained exclusively on **permissive/non-copyrighted audio data** and IPA phoneme labels. Examples of permissive/non-copyrighted audio include:
- Public domain audio
- Audio licensed under Apache, MIT, etc
- Synthetic audio<sup>[1]</sup> generated by closed<sup>[2]</sup> TTS models from large providers<br/>
[1] https://copyright.gov/ai/ai_policy_guidance.pdf<br/>
[2] No synthetic audio from open TTS models or "custom voice clones"

**Total Dataset Size:** A few hundred hours of audio

### Creative Commons Attribution

The following CC BY audio was part of the dataset used to train Kokoro v1.0.

| Audio Data | Duration Used | License | Added to Training Set After |
| ---------- | ------------- | ------- | --------------------------- |
| [Koniwa](https://github.com/koniwa/koniwa) `tnc` | <1h | [CC BY 3.0](https://creativecommons.org/licenses/by/3.0/deed.ja) | v0.19 / 22 Nov 2024 |
| [SIWIS](https://datashare.ed.ac.uk/handle/10283/2353) | <11h | [CC BY 4.0](https://datashare.ed.ac.uk/bitstream/handle/10283/2353/license_text) | v0.19 / 22 Nov 2024 |

<img src="https://static0.gamerantimages.com/wordpress/wp-content/uploads/2024/08/terminator-zero-41-1.jpg" width="400" alt="kokoro" />
