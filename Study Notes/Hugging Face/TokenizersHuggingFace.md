# Tokenizers - Hugging Face NLP Course

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
> **Highlight:** Tokenizers are one of the core components of the NLP pipeline. They serve one purpose: to translate text into data that can be processed by the model.
> 

> [!quote] **Page **
> **Highlight:** The goal is to find the most meaningful representation — that is, the one that makes the most sense to the model — and, if possible, the smallest representation.
> 💬 _“Smallest representation” means representing the input text with the <b>fewest tokens possible</b>. Fewer tokens reduce model input length and computational cost. For example, “tokenization” split into “token” + “ization” is smaller and more efficient than splitting it into characters._

> [!quote] **Page **
> **Highlight:** Word-based
> 💬 _<b>Tokenizer 类型</b> <b>原理</b> <b>优点</b> <b>缺点</b> <b>Word-based</b> 以空格或规则划分成单词简单直观，词义完整词表巨大，OOV（未知词）多 <b>Character-based</b> 每个字符为一个 token 词表小，几乎无 OOV 序列长，单个字符语义少 <b>Subword</b> 高频词不拆，低频词拆成有意义的子词，如 “token”+“ization” 兼顾 OOV 和词表大小，效率高，语义保持较好构建和训练更复杂_

> [!quote] **Page **
> **Highlight:** This is known as the “unknown” token, often represented as ”[UNK]” or ”<unk>”. It’s generally a bad sign if you see that the tokenizer is producing a lot of these tokens, as it wasn’t able to retrieve a sensible representation of a word and you’re losing information along the way.
> 

> [!quote] **Page **
> **Highlight:** Character-based
> 💬 _<b>| Tokenizer Type      | Principle                                                   | Advantages                                       | Disadvantages                                 |
|---------------------|-------------------------------------------------------------|--------------------------------------------------|----------------------------------------------|
| **Word-based**      | Splits text into tokens at word boundaries (spaces/punctuation) | Simple, preserves full word meanings             | Huge vocabulary, lots of OOV (out-of-vocabulary) |
| **Character-based** | Each character is treated as a token                        | Tiny vocabulary, almost no OOV                   | Very long sequences, little semantic info per token |
| **Subword**         | Splits rare words into smaller subword units, frequent words stay whole | Balances OOV handling and vocab size, retains meaning better | More complex to train and build              |</b>_

> [!quote] **Page **
> **Highlight:** Subword tokenization
> 

> [!quote] **Page **
> **Highlight:** And more!
> 💬 _| Method                   | Explanation                                                    | Common Usage                   |
|--------------------------|----------------------------------------------------------------|--------------------------------|
| **Byte-level BPE**       | Splits at byte-level (character encodings), handles all text types including non-standard symbols | Used in GPT-2, GPT-3           |
| **WordPiece**            | Splits based on statistical frequency of word pieces, smaller frequent units | Used in BERT, RoBERTa          |
| **SentencePiece/Unigram**| Treats the sentence as raw input without preprocessing, probabilistically selects subwords | Used in T5, XLM-R for multilingual tasks |_

> [!quote] **Page **
> **Highlight:** from transformers import BertTokenizer tokenizer = BertTokenizer.from_pretrained("bert-base-cased")
> 💬 _<b>AutoTokenizer</b> works the same but is more flexible. It automatically selects the correct tokenizer class (e.g., BertTokenizer) based on the checkpoint._

> [!quote] **Page **
> **Highlight:** Translating text to numbers is known as encoding. Encoding is done in a two-step process: the tokenization, followed by the conversion to input IDs.
> 

> [!quote] **Page **
> **Highlight:** The second step is to convert those tokens into numbers, so we can build a tensor out of them and feed them to the model. To do this, the tokenizer has a vocabulary, which is the part we download when we instantiate it with the from_pretrained() method. Again, we need to use the same vocabulary used when the model was pretrained.
> 


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

‘Tokenizers - Hugging Face NLP Course’. Accessed: Mar. 16, 2025. [Online]. Available: [https://huggingface.co/learn/nlp-course/en/chapter2/4](https://huggingface.co/learn/nlp-course/en/chapter2/4)