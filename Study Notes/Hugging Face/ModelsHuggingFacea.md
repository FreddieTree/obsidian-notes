# Models - Hugging Face NLP Course

<!-- Collapsible Basic Information -->
<details>
  <summary>📌 Basic Information</summary>
  
  - **Authors:** 
  - **Publication Date:** Error: `format` can only be applied to dates. Tried for format object
  
  - **Tags:** 
  
</details>

---

## 📝 Summary
> We’re on a journey to advance and democratize artificial intelligence through open source and open science.

---

## ✏️ Annotations

> [!quote] **Page **
> **Highlight:** The AutoModel class and all of its relatives are actually simple wrappers over the wide variety of models available in the library. It’s a clever wrapper as it can automatically guess the appropriate model architecture for your checkpoint, and then instantiates a model with this architecture.
> 💬 _<b>Architecture</b> refers to the model’s structure, such as BERT or GPT, defining layers, attention heads, etc. • <b>Checkpoint</b> is a saved version of a model at a particular training stage, containing learned weights and configs. It’s called “checkpoint” because it marks a “save point” in training._

> [!quote] **Page **
> **Highlight:** the hidden_size attribute defines the size of the hidden_states vector, and num_hidden_layers defines the number of layers the Transformer model has.
> 💬 _Hidden size refers to the dimensionality of hidden states in the model
<b>Hidden layers</b> = depth of the Transformer, <b>attention heads</b> = number of attention heads per layer. More layers/heads generally improve model capacity but increase computation._

> [!quote] **Page **
> **Highlight:** Creating a model from the default configuration initializes it with random values:
> 💬 _The model initializes randomly because it has not been trained yet. You must either <b>train it from scratch</b> or <b>load pretrained weights</b>; otherwise, it will output meaningless results._

> [!quote] **Page **
> **Highlight:** As you saw earlier, we could replace BertModel with the equivalent AutoModel class. We’ll do this from now on as this produces checkpoint-agnostic code; if your code works for one checkpoint, it should work seamlessly with another. This applies even if the architecture is different, as long as the checkpoint was trained for a similar task (for example, a sentiment analysis task).
> 💬 _AutoModel automatically detects the correct architecture for the checkpoint (e.g., BERT, RoBERTa). This makes your code <b>checkpoint-agnostic</b>, meaning it works with different pretrained models as long as they target similar tasks._

> [!quote] **Page **
> **Highlight:** The weights have been downloaded and cached (so future calls to the from_pretrained() method won’t re-download them) in the cache folder, which defaults to ~/.cache/huggingface/transformers. You can customize your cache folder by setting the HF_HOME environment variable.
> 

> [!quote] **Page **
> **Highlight:** If you take a look at the config.json file, you’ll recognize the attributes necessary to build the model architecture. This file also contains some metadata, such as where the checkpoint originated and what 🤗 Transformers version you were using when you last saved the checkpoint.

The pytorch_model.bin file is known as the state dictionary; it contains all your model’s weights. The two files go hand in hand; the configuration is necessary to know your model’s architecture, while the model weights are your model’s parameters.
> 

> [!quote] **Page **
> **Highlight:** Using a Transformer model for inference
> 💬 _1. Prepare text: Write the input sentences to be processed. 
2. Tokenize: Use a tokenizer to convert the text into input IDs (numeric sequences). 
3. Convert to tensor: Convert input IDs into the tensor format required by the model. 
4. Input model: Use model(inputs) to input into the model. 
5. Obtain output: Get hidden states or logits, which serve as task features or final results. 

Purpose: Convert text into numbers that can be processed by the model, extract deep semantic information through Transformer, and provide it for downstream tasks._


---

## 🧐 Personal Notes

### 🔍 Key Takeaways  
- *Write your insights and reflections here.*

### 📌 Important Concepts  
- *Concept 1*  
- *Concept 2*

### ❓ Questions for Further Research  
- *List questions or points you need to explore further.*

---

## 📚 References
[1]

‘Models - Hugging Face NLP Course’. Accessed: Mar. 16, 2025. [Online]. Available: [https://huggingface.co/learn/nlp-course/en/chapter2/3](https://huggingface.co/learn/nlp-course/en/chapter2/3)