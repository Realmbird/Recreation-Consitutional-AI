---
base_model: Qwen/Qwen3-0.6B
library_name: peft
model_name: rlhf_helpful_Qwen3_0.6B
tags:
- base_model:adapter:Qwen/Qwen3-0.6B
- lora
- transformers
licence: license
---

# Model Card for rlhf_helpful_Qwen3_0.6B

This model is a fine-tuned version of [Qwen/Qwen3-0.6B](https://huggingface.co/Qwen/Qwen3-0.6B).
It has been trained using [TRL](https://github.com/huggingface/trl).

## Quick start

```python
from transformers import pipeline

question = "If you had a time machine, but could only go to the past or the future once and never return, which would you choose and why?"
generator = pipeline("text-generation", model="None", device="cuda")
output = generator([{"role": "user", "content": question}], max_new_tokens=128, return_full_text=False)[0]
print(output["generated_text"])
```

## Training procedure

 


This model was trained with PPO, a method introduced in [Fine-Tuning Language Models from Human Preferences](https://huggingface.co/papers/1909.08593).

### Framework versions

- PEFT 0.16.0
- TRL: 0.20.0
- Transformers: 4.54.1
- Pytorch: 2.7.1
- Datasets: 4.0.0
- Tokenizers: 0.21.4

## Citations

Cite PPO as:

```bibtex
@article{mziegler2019fine-tuning,
    title        = {{Fine-Tuning Language Models from Human Preferences}},
    author       = {Daniel M. Ziegler and Nisan Stiennon and Jeffrey Wu and Tom B. Brown and Alec Radford and Dario Amodei and Paul F. Christiano and Geoffrey Irving},
    year         = 2019,
    eprint       = {arXiv:1909.08593}
}
```

Cite TRL as:
    
```bibtex
@misc{vonwerra2022trl,
	title        = {{TRL: Transformer Reinforcement Learning}},
	author       = {Leandro von Werra and Younes Belkada and Lewis Tunstall and Edward Beeching and Tristan Thrush and Nathan Lambert and Shengyi Huang and Kashif Rasul and Quentin Gallou{\'e}dec},
	year         = 2020,
	journal      = {GitHub repository},
	publisher    = {GitHub},
	howpublished = {\url{https://github.com/huggingface/trl}}
}
```