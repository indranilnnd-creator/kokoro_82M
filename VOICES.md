# Voices

For each voice, the given grades are intended to be estimates of the **quality and quantity** of its associated training data, both of which impact overall inference quality.

Subjectively, voices will sound better or worse to different people.

**Target Quality**
- How high quality is the reference voice? This grade may be impacted by audio quality, artifacts, compression, & sample rate.
- How well do the text labels match the audio? Text/audio misalignment (e.g. from hallucinations) will lower this grade.

**Training Duration**
- How much audio was seen during training? Smaller durations result in a lower overall grade.
- 10 hours <= HH hours < 100 hours
- 1 hour <= H hours < 10 hours
- 10 minutes <= MM minutes < 100 minutes
- 1 minute <= M minutes < 10 minutes

### American English 🇺🇸

- [`misaki[en]`](https://github.com/hexgrad/misaki) `lang_code='a'` with `en-us` espeak-ng fallback

| Name | Traits | Target Quality | Training Duration | Overall Grade |
| ---- | ------ | -------------- | ----------------- | ------------- |
| af_alloy | 🚺 | B | MM minutes | C |
| af_aoede | 🚺 | B | H hours | C+ |
| af_bella | 🚺🔥 | **A** | **HH hours** | **A-** |
| af_jessica | 🚺 | C | MM minutes | D |
| af_kore | 🚺 | B | H hours | C+ |
| af_nicole | 🚺🎧 | B | **HH hours** | B- |
| af_nova | 🚺 | B | MM minutes | C |
| af_river | 🚺 | C | MM minutes | D |
| af_sarah | 🚺 | B | H hours | C+ |
| af_sky | 🚺 | B | M minutes | C- |
| am_adam | 🚹 | D | H hours | F+ |
| am_echo | 🚹 | C | MM minutes | D |
| am_eric | 🚹 | C | MM minutes | D |
| am_fenrir | 🚹 | B | H hours | C+ |
| am_liam | 🚹 | C | MM minutes | D |
| am_michael | 🚹 | B | H hours | C+ |
| am_onyx | 🚹 | C | MM minutes | D |
| am_puck | 🚹 | B | H hours | C+ |

### British English 🇬🇧

- [`misaki[en]`](https://github.com/hexgrad/misaki) `lang_code='b'` with `en-gb` espeak-ng fallback

| Name | Traits | Target Quality | Training Duration | Overall Grade |
| ---- | ------ | -------------- | ----------------- | ------------- |
| bf_alice | 🚺 | C | MM minutes | D |
| bf_emma | 🚺 | B | **HH hours** | B- |
| bf_isabella | 🚺 | B | MM minutes | C |
| bf_lily | 🚺 | C | MM minutes | D |
| bm_daniel | 🚹 | C | MM minutes | D |
| bm_fable | 🚹 | B | MM minutes | C |
| bm_george | 🚹 | B | MM minutes | C |
| bm_lewis | 🚹 | C | H hours | D+ |

### French 🇫🇷

- espeak-ng `fr-fr`
- Total French training data: <11 hours

| Name | Traits | Target Quality | Training Duration | Overall Grade |
| ---- | ------ | -------------- | ----------------- | ------------- |
| [ff_siwis](https://datashare.ed.ac.uk/handle/10283/2353) | 🚺 | B | <11 hours | B- |

### Hindi 🇮🇳

- espeak-ng `hi`
- Total Hindi training data: H hours

| Name | Traits | Target Quality | Training Duration | Overall Grade |
| ---- | ------ | -------------- | ----------------- | ------------- |
| hf_alpha | 🚺 | B | MM minutes | C |
| hf_beta | 🚺 | B | MM minutes | C |
| hm_omega | 🚹 | B | MM minutes | C |
| hm_psi | 🚹 | B | MM minutes | C |

### Japanese 🇯🇵

- [`misaki[ja]`](https://github.com/hexgrad/misaki)
- Total Japanese training data: H hours

| Name | Traits | Target Quality | Training Duration | Overall Grade |
| ---- | ------ | -------------- | ----------------- | ------------- |
| jf_alpha | 🚺 | B | H hours | C+ |

### Mandarin Chinese 🇨🇳

- [`misaki[zh]`](https://github.com/hexgrad/misaki)
- Total Mandarin Chinese training data: H hours

| Name | Traits | Target Quality | Training Duration | Overall Grade |
| ---- | ------ | -------------- | ----------------- | ------------- |
| zf_xiaobei | 🚺 | C | MM minutes | D |
| zf_xiaoni | 🚺 | C | MM minutes | D |
| zf_xiaoxiao | 🚺 | C | MM minutes | D |
| zf_xiaoyi | 🚺 | C | MM minutes | D |
| zm_yunjian | 🚹 | C | MM minutes | D |
| zm_yunxi | 🚹 | C | MM minutes | D |
| zm_yunxia | 🚹 | C | MM minutes | D |
| zm_yunyang | 🚹 | C | MM minutes | D |
