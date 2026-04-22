# Small Langugage Model Finetuning
### 1. Fine_TuneSLM_Classification.ipynb
   
   In this notebook I create Small Language Model (SLM) with GPT2 configuration, finetune GPT-2 model to classify input text into two classes - Spam or Non-Spam


The model layers are coded from scratch (including multi-head attention, layernorm, GELU, LoRA)
   GPT2 weights are loaded from open source model
   
This Small Language Model is used for binary classification and results evaluated:
   
       a) As-is without fine-tuning
       
       b) Parameter Efficient Fine Tuning (PEFT) - Frozen layers except last transformer block
       
       b) Parameter Efficient Fine Tuning (PEFT) - Finetuning GPT2 model with LoRA (low rank adaptation).
    

Loss function / Objective: Cross Entropy for logits of last output token

Optimization: AdamW

Evaluation: Accuracy of Spam not Spam Classification

Results: 
- The GPT2 model as is has ~ 50% accuracy
- With PEFT (last block unfrozen) the accuracy increases to ~87%
- With PEFT - LoRA we have ~92%
- LoRA is very efficient next to full model finetuning.
- Moreover, LoRA layers can be tuned for a specific task and added or removed as needed.
- This means we can train different LoRA layers for each task on the same base model and load them at inference time based on the usage


To Do:
- Multiclass classification
- Multilabel classification


Reference:
   - Data Donated on 6/21/2012 from UCIrvine Machine Learning Repository
     ```https://archive.ics.uci.edu/dataset/228/sms+spam+collection```
   - From Hugging face: ``` https://huggingface.co/datasets/ucirvine/sms_spam/blob/main/plain_text/train-00000-of-00001.parquet ```
   - GPT2 weights from: ``` https://openaipublic.blob.core.windows.net/gpt-2/models ```
   - Attention Is All You Need: ``` https://arxiv.org/abs/1706.03762 ```
   - LoRA: Low-Rank Adaptation of Large Language Models: ``` https://arxiv.org/abs/2106.09685 ```
   - Andrej Karapathy: ```https://www.youtube.com/watch?v=kCc8FmEb1nY&list=PLAqhIrjkxbuWI23v9cThsA9GvCAUhRvKZ&index=7&pp=iAQB```
   - Sebastian Rashka: ```https://www.youtube.com/watch?v=5PFXJYme4ik```

