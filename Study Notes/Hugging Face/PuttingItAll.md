# Putting it all together - Hugging Face NLP Course

<!-- Collapsible Basic Information -->
<details>
  <summary>📌 Basic Information</summary>
  
  - **Authors:** 
  - **Publication Date:** Error: `format` can only be applied to dates. Tried for format object
  
  - **Tags:** 
  
</details>
---

## ✏️ Annotations

> [!quote] **Page **
> **Highlight:** 
> ```python
model_inputs = tokenizer(sequence) print(model_inputs["input_ids"]) tokens = tokenizer.tokenize(sequence) ids = tokenizer.convert_tokens_to_ids(tokens) print(ids)

> 💬 _Two methods can be used, but the difference lies in the degree of automation:

1. The tokenizer(sequence) is a complete pipeline that automatically completes tokenization, ID conversion, padding, truncation, and special tokens (such as [CLS], [SEP]). 
2. The tokenizer.tokenize() will only tokenize and will not add special tokens. 
3. convert_tokens_to_ids() manually converts the tokenization results to IDs, but still will not add special tokens. 

Recommendation: Generally, it is more convenient to directly use tokenizer(sequence)._

> [!quote] **Page **
> **Highlight:** 
> ```
return_tensors = "pt"

> 💬 _return_tensors='pt' tells the tokenizer to output <b>PyTorch tensors</b> for model input. For TensorFlow users, you would set 'tf'._
