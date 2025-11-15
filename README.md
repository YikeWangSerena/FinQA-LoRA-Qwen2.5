# Sentiment-Aware Financial Question Answering

This repository extends the original [FinQA](https://github.com/czyssrs/FinQA) framework by integrating **FinBERT-based sentiment analysis** into financial numerical reasoning. The goal is to build a sentiment-aware version of FinQA that incorporates linguistic tone—optimism, pessimism, or neutrality—into the reasoning pipeline, improving the model’s ability to interpret financial statements and answer numerical questions.

FinQA performs question answering over corporate financial reports using both textual evidence and tabular data. However, the original system treats all textual information as neutral and does not account for management tone, which often influences how quantitative results should be interpreted. This project adds sentiment signals extracted with FinBERT to enable more context-aware reasoning.

---

## Project Overview

**Objective:**  
To enhance FinQA by incorporating sentiment extracted from financial text using FinBERT, and evaluate whether these sentiment-aware features improve:

- **Program Accuracy**  
- **Execution Accuracy**  
- **Interpretability** of numerical reasoning tasks  

### Why Sentiment?
Financial documents combine:

- **Quantitative facts** — tables, ratios, YoY comparisons  
- **Qualitative tone** — management’s confidence, caution, or concerns  

Two statements may report the same numbers but communicate different implications depending on sentiment:

> “Revenue increased, but management remains cautious about next quarter.”  
> vs.  
> “Revenue increased, indicating strong performance momentum.”

A sentiment-aware model can more accurately interpret direction-sensitive questions such as increase/decrease or improvement/decline.

---

## Built on the FinQA Framework

This project is implemented on top of the official FinQA codebase (EMNLP 2021).  
We keep:

- Retriever  
- Program generator  
- Evaluation scripts  
- Dataset format  

We add:

- FinBERT sentiment inference  
- Sentiment-augmented preprocessing  
- A sentiment-aware generator architecture

---

## Contributions

1. **FinBERT Sentiment Extraction**  
   - Run FinBERT on retrieved evidence text  
   - Assign sentiment labels (positive / neutral / negative) or probability logits  

2. **Sentiment-Aware Reasoning Module**  
   - Integrate sentiment into FinQA’s generator via:  
     - special tokens  
     - sentiment embeddings  
     - auxiliary features for directional reasoning  

3. **Comprehensive Evaluation**  
   - Compare sentiment-enhanced models with baseline FinQA  
   - Analyze improvements in direction-sensitive questions

---

## Repository Structure (Planned)
```bash
FinQA_w_FinBert/
│
├── dataset/                      # Original FinQA dataset
├── retriever/                    # FinQA retriever
├── generator/                    # Modified generator with sentiment integration
├── evaluate/                     # Official FinQA evaluation scripts
│
├── sentiment/
│   ├── finbert_inference.py      # FinBERT inference wrapper
│   ├── sentiment_preprocess.py   # Add sentiment labels to evidence
│   └── utils.py
│
├── train_with_sentiment.py       # Training script for sentiment-aware FinQA
├── config_sentiment.py           # Experiment configuration
├── requirements.txt
└── README.md
```
---

## Expected Outcomes
- Better handling of direction-based reasoning (increase/decrease, improvement/decline)
- Improved interpretability through explicit sentiment annotations
- Higher Program Accuracy and Execution Accuracy compared to baseline FinQA

---

## Team

**Serena Wang** — Duke University, M.Eng. Electrical & Computer Engineering

**Mo Liu** — Duke University, M.A. Economics

**Zhiyi Xie** — Duke University, M.A. Economics

---

## Acknowledgments
- FinQA dataset and implementation: https://github.com/czyssrs/FinQA  
- FinBERT: ProsusAI’s financial-domain sentiment analysis model
