# 🧠 Training a Multilingual Translator

A practical and extensible project for fine-tuning multilingual translation models using LoRA. Covers English ↔ Chinese, English ↔ Nepali, and combines both for multi-task learning on a compact LLaMA-3.2-3B base.

---

## 🚀 Project Highlights

- ✅ Fine-tuned translation models on:
  - **English ↔ Chinese** (WMT19)
  - **English ↔ Nepali** ([iamTangsang/Nepali-to-English-Translation-Dataset](https://huggingface.co/datasets/iamTangsang/Nepali-to-English-Translation-Dataset))
  - **Combined multilingual model** (Chinese ↔ English ↔ Nepali)
- ✅ English ↔ Chinese, English ↔ Nepali fine-tuning performed via **LoRA (Low-Rank Adaptation)** on top of "Qwen/Qwen2.5-0.5B"
- ✅ Combined multilingual model (Chinese ↔ English ↔ Nepali) fine-tuning performed via **LoRA (Low-Rank Adaptation)** on top of `meta-llama/Llama-3.2-3B`
- ✅ Used Hugging Face Transformers and Trainer APIs for reproducible training on Jupyter Notebook
- ✅ Evaluation metrics: BLEU and chrF++ (details below)

---

## 📊 Evaluation Results (Multilingual Model)

| Language Pair | BLEU Score Progression        | chrF++ Score Progression      |
|---------------|-------------------------------|-------------------------------|
| **ZH → EN**   | 2.86 → 18.63 → **19.05**      | 14.10 → 45.92 → **45.81**     |
| **EN → ZH**   | 0.00 → - → **0.00**           | 1.42 → 18.80 → **19.21**      |
| **NE → EN**   | 0.00 → 19.34 → **20.42**      | 8.73 → 41.94 → **42.01**      |
| **EN → NE**   | 0.00 → - → **0.00**           | 0.12 → 27.90 → **30.38**      |

> 📎 These improvements were achieved through progressive fine-tuning with LoRA using merged datasets.

---

## 📁 Notebooks

You can open and run each notebook for training or inference:

- `En-Zh.ipynb`: English ↔ Chinese LoRA fine-tuning
- `En-Ne.ipynb`: English ↔ Nepali LoRA fine-tuning
- `Zh-En-Ne.ipynb`: Multilingual fine-tuning with merged datasets

> 🧪 All training done using Jupyter Notebook & Hugging Face Trainer  
> 🧠 Easily extendable to new language pairs by updating the `lang_pair` field in dataset format:  
> `{"input": ..., "output": ..., "lang_pair": "en-zh"}`

---

## ✨ Future Plans

- 🔄 Investigate the use of **English as a bridging high-resource language** to enhance zero-shot or few-shot performance on unseen language translation between low-resource pairs (e.g., Nepali ↔ Chinese via English)
- 🧪 Experiment with **pivot translation** and **triangular training** setups to evaluate whether they improve generalization
- 🔗 Explore multilingual token alignment and shared embedding space techniques for better bridging

---

## 🙏 Acknowledgements

- [meta-llama/Llama-3.2-3B](https://huggingface.co/meta-llama/Llama-3.2-3B) for the base model
- [WMT19](https://huggingface.co/datasets/wmt/wmt19) and [iamTangsang](https://huggingface.co/datasets/iamTangsang/Nepali-to-English-Translation-Dataset) for dataset resources

---

## 📄 License

This project is open-sourced under the **MIT License**.  
Please credit the original dataset providers and model creators when reusing.
