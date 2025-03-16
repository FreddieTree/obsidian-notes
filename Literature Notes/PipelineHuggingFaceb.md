# Behind the pipeline - Hugging Face NLP Course

<!-- Collapsible Metadata -->
<details>
  <summary>🌐 Source Information</summary>
  
  - **Source Title:** Behind the pipeline - Hugging Face NLP Course
  - **Source Type:** Web / Snapshot / Other  
  - **URL:** [https://huggingface.co/learn/nlp-course/en/chapter2/2](https://huggingface.co/learn/nlp-course/en/chapter2/2)
  - **Date Captured:** Error: `format` can only be applied to dates. Tried for format object
  - **Tags:** 
  - **Zotero Link:** 

</details>

---

## 🖍️ Annotation Review

> [!quote] **Location:** N/A  
> **Highlight:** Transformer models can’t process raw text directly, so the first step of our pipeline is to convert the text inputs into numbers that the model can make sense of.  
> 

> [!quote] **Location:** N/A  
> **Highlight:** tokenizer  
> 

> [!quote] **Location:** N/A  
> **Highlight:** Mapping each token to an integer  
> 💬 _Note:_ Mapping to integers is efficient because they act as indices to lookup embeddings in the model’s matrix. Using floats would complicate indexing and increase memory and computation costs. The model just needs to know “this is token #N.”

> [!quote] **Location:** N/A  
> **Highlight:** All this preprocessing needs to be done in exactly the same way as when the model was pretrained  
> 💬 _Note:_ The model is trained with a specific tokenizer and expects inputs in that exact format. Changing preprocessing alters token splits, leading to distribution shifts. The model may misinterpret inputs, reducing performance.

> [!quote] **Location:** N/A  
> **Highlight:** However, Transformer models only accept tensors as input.  
> 

> [!quote] **Location:** N/A  
> **Highlight:** input_ids contains two rows of integers (one for each sentence) that are the unique identifiers of the tokens in each sentence.  
> 

> [!quote] **Location:** N/A  
> **Highlight:** We can download our pretrained model the same way we did with our tokenizer. 🤗 Transformers provides an AutoModel class which also has a from_pretrained() method:  
> 💬 _Note:_ Downloading allows local inference, reducing latency compared to online APIs and ensuring faster, stable execution. Once downloaded, the model runs directly on your machine without external calls.

> [!quote] **Location:** N/A  
> **Highlight:** This architecture contains only the base Transformer module: given some inputs, it outputs what we’ll call hidden states, also known as features. For each model input, we’ll retrieve a high-dimensional vector representing the contextual understanding of that input by the Transformer model.  
> 💬 _Note:_ A hidden state is a contextual feature vector for each token, encoding its meaning within the sentence. These vectors feed into downstream tasks like classification or generation.

> [!quote] **Location:** N/A  
> **Highlight:** head  
> 💬 _Note:_ A model head is the task-specific layer on top of hidden states, such as classification or generation heads. It converts hidden states into task-relevant outputs.

> [!quote] **Location:** N/A  
> **Highlight:** The vector output by the Transformer module is usually large. It generally has three dimensions:

Batch size: The number of sequences processed at a time (2 in our example).
Sequence length: The length of the numerical representation of the sequence (16 in our example).
Hidden size: The vector dimension of each model input.  
> 

> [!quote] **Location:** N/A  
> **Highlight:** The hidden size can be very large (768 is common for smaller models, and in larger models this can reach 3072 or more).  
> 

> [!quote] **Location:** N/A  
> **Highlight:** outputs = model(**inputs)  
> 💬 _Note:_ inputs is a dictionary. **inputs unpacks it into keyword arguments, like input_ids=..., attention_mask=..., matching the model’s expected input format.

> [!quote] **Location:** N/A  
> **Highlight:** In this diagram, the model is represented by its embeddings layer and the subsequent layers. The embeddings layer converts each input ID in the tokenized input into a vector that represents the associated token. The subsequent layers manipulate those vectors using the attention mechanism to produce the final representation of the sentences.  
> 💬 _Note:_ a diagram should be inserted

> [!quote] **Location:** N/A  
> **Highlight:** To be converted to probabilities, they need to go through a SoftMax layer (all 🤗 Transformers models output the logits, as the loss function for training will generally fuse the last activation function, such as SoftMax, with the actual loss function, such as cross entropy)  
> 💬 _Note:_ Softmax converts logits into probabilities for classification or generation tasks. It ensures outputs sum to 1, improves interpretability, and works well with cross-entropy loss.


---

