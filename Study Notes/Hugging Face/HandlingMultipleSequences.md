# Handling multiple sequences - Hugging Face NLP Course

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
> **Highlight:** Transformers models expect multiple sentences by default.
> 💬 _“Multiple sentences” means the model expects inputs as batches (even if batch size = 1). Transformers expect a 2D tensor: [batch_size, seq_length]. A single sentence without batching would be 1D [seq_length], which breaks the model input convention.
Batching is key to efficient computation, enabling parallel processing._

> [!quote] **Page **
> **Highlight:** we usually pad the inputs.
> 

> [!quote] **Page **
> **Highlight:** Attention masks are tensors with the exact same shape as the input IDs tensor, filled with 0s and 1s: 1s indicate the corresponding tokens should be attended to, and 0s indicate the corresponding tokens should not be attended to (i.e., they should be ignored by the attention layers of the model).
> 

> [!quote] **Page **
> **Highlight:** Truncate your sequences.
> 💬 _Quantity Limit: 
Theoretically, <b>batch_size</b> depends on GPU memory/RAM, but the model itself does not limit batch_size. 
* <b>Length Limit</b>: Most models (such as BERT) have a maximum length limit for a single sentence, usually 512 tokens. If the length exceeds this, the tokenizer will automatically truncate.

How to avoid: 
* <b>Sliding window</b> (sliding window) technology can be used to input long texts in chunks to the model. 
* <b>Models</b> that support long sequences such as Longformer, BigBird can also be used. 

The impact of truncation: 
* Truncation may result in the loss of key information, especially in NLP tasks where important information in long sentences is often at the end. 
* A more reasonable approach is to process segments and aggregate contextual information rather than directly truncate._


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

‘Handling multiple sequences - Hugging Face NLP Course’. Accessed: Mar. 16, 2025. [Online]. Available: [https://huggingface.co/learn/nlp-course/en/chapter2/5](https://huggingface.co/learn/nlp-course/en/chapter2/5)