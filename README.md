# 🧠 medical-qa-qwen-model 

A fine-tuned Qwen LLM designed for **medical question-answering** in English and Turkish.
Built using domain-specific datasets and LoRA-based parameter-efficient fine-tuning.

## 🔍 Project Overview

This project trains a **custom medical QA model** using the [Qwen1.5-0.5B](https://huggingface.co/Qwen/Qwen1.5-0.5B) architecture.
Medical datasets are cleaned, merged, tokenized, and used for fine-tuning via LoRA adapters.
The result is a lightweight model capable of answering medical questions reliably.

## 📁 Directory Structure

```
documents/
├── datasets_base/        # Raw, split, and merged datasets
├── tokenize_datasets/    # Tokenized datasets (5k, 25k, 200k, 380k)
```

Project root directory:

```
├── finetuned_qwen_model_200k/  # Trained LoRA adapter (output of fine-tuning)
├── clean_datasets.py           # Removes invalid samples
├── convert_to_alpaca.py        # Converts datasets to Alpaca format
├── download_dataset.py         # Downloads public medical datasets
├── fine_tune_final.py          # Alternative training script for initial experiments
├── fine_tune_qwen.py           # Final and optimized LoRA fine-tuning script
├── merge_datasets.py           # Merges TR and EN datasets
├── load_qwen_model.py          # Loads local Qwen model + adapter
├── medical_qa_model.py         # QA inference script
├── merge_datasets.py           # Merges multilingual datasets into one file
├── split_dataset.py            # Splits merged dataset into smaller chunks
├── tokenize_all_datasets.py    # Tokenizes all datasets
├── tokenize_dataset.py         # Tokenizes a single dataset file
```

## 🚀 How to Run

1. **Prepare the Data**

   ```bash
   python download_dataset.py
   python clean_datasets.py
   python convert_to_alpaca.py
   python merge_datasets.py
   ```

2. **Tokenize**

   ```bash
   python tokenize_all_datasets.py
   ```

3. **Train the Model**

   ```bash
   python fine_tune_qwen.py
   ```

4. **Load and Run Inference**

   ```bash
   python load_qwen_model.py         # Load base + adapter
   python medical_qa_model.py        # Ask medical questions
   ```

## 📌 Example Usage

```text
Question: What are the symptoms of diabetes?
Answer: Excessive thirst, frequent urination, fatigue, and weight loss are common symptoms of type 2 diabetes.
```

## 🧠 Model Details

* Base Model: `Qwen/Qwen1.5-0.5B`
* LoRA Config: `r=8`, `alpha=32`
* Training Samples: \~200,000 examples
* Training Time: \~12 hours (on 8GB VRAM GPU)
* Tokenizer: Same as base model tokenizer

## 📦 Installation

Install required packages:

```bash
pip install -r requirements.txt
```

---

## 📄 License

Distributed under the [MIT License](LICENSE).

## 🙋‍♂️ Author

* GitHub: [@RucoH](https://github.com/RucoH)
* Live Site: [https://rucoh.github.io/](https://rucoh.github.io/)

---
