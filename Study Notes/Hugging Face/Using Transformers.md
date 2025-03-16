# Introduction
> **Highlight:** Simplicity: Hardly any abstractions are made across the library. The “All in one file” is a core concept: a model’s forward pass is entirely defined in a single file, so that the code itself is understandable and hackable.
> 

# Behind the pipeline
> [!quote] **Page **
> **Highlight:** Transformer models can’t process raw text directly, so the first step of our pipeline is to convert the text inputs into numbers that the model can make sense of.
> 

> [!quote] **Page **
> **Highlight:** tokenizer
> 

> [!quote] **Page **
> **Highlight:** Mapping each token to an integer
> 💬 _Mapping to integers is efficient because they act as indices to lookup embeddings in the model’s matrix. Using floats would complicate indexing and increase memory and computation costs. The model just needs to know “this is token #N.”_

> [!quote] **Page **
> **Highlight:** All this preprocessing needs to be done in exactly the same way as when the model was pretrained
> 💬 _The model is trained with a specific tokenizer and expects inputs in that exact format. Changing preprocessing alters token splits, leading to distribution shifts. The model may misinterpret inputs, reducing performance._

> [!quote] **Page **
> **Highlight:** However, Transformer models only accept tensors as input.
> 

> [!quote] **Page **
> **Highlight:** input_ids contains two rows of integers (one for each sentence) that are the unique identifiers of the tokens in each sentence.
> 

> [!quote] **Page **
> **Highlight:** We can download our pretrained model the same way we did with our tokenizer. 🤗 Transformers provides an AutoModel class which also has a from_pretrained() method:

> 💬 _Downloading allows local inference, reducing latency compared to online APIs and ensuring faster, stable execution. Once downloaded, the model runs directly on your machine without external calls._

> [!quote] **Page **
> **Highlight:** This architecture contains only the base Transformer module: given some inputs, it outputs what we’ll call hidden states, also known as features. For each model input, we’ll retrieve a high-dimensional vector representing the contextual understanding of that input by the Transformer model.

> 💬 _A hidden state is a contextual feature vector for each token, encoding its meaning within the sentence. These vectors feed into downstream tasks like classification or generation._

> [!quote] **Page **
> **Highlight:** model head

> 💬 _A model head is the task-specific layer on top of hidden states, such as classification or generation heads. It converts hidden states into task-relevant outputs._

> [!quote] **Page **
> **Highlight:** The vector output by the Transformer module is usually large. It generally has three dimensions:

* Batch size: The number of sequences processed at a time (2 in our example).
* Sequence length: The length of the numerical representation of the sequence (16 in our example).
* Hidden size: The vector dimension of each model input.


> [!quote] **Page **
> **Highlight:** The hidden size can be very large (768 is common for smaller models, and in larger models this can reach 3072 or more).
> 

> [!quote] **Page **
> **Highlight:** outputs = model(**inputs)

> 💬 _inputs is a dictionary. **inputs unpacks it into keyword arguments, like input_ids=..., attention_mask=..., matching the model’s expected input format._

> [!quote] **Page **
> **Highlight:** In this diagram, the model is represented by its embeddings layer and the subsequent layers. The embeddings layer converts each input ID in the tokenized input into a vector that represents the associated token. The subsequent layers manipulate those vectors using the attention mechanism to produce the final representation of the sentences.

 ![[transformer_and_head.svg]]

> [!quote] **Page **
> **Highlight:** To be converted to probabilities, they need to go through a SoftMax layer (all 🤗 Transformers models output the logits, as the loss function for training will generally fuse the last activation function, such as SoftMax, with the actual loss function, such as cross entropy)

> 💬 _Softmax converts logits into probabilities for classification or generation tasks. It ensures outputs sum to 1, improves interpretability, and works well with cross-entropy loss._

# Models

> [!quote] **Page **
> **Highlight:** The AutoModel class and all of its relatives are actually simple wrappers over the wide variety of models available in the library. It’s a clever wrapper as it can automatically guess the appropriate model architecture for your checkpoint, and then instantiates a model with this architecture.

> 💬 
* **Architecture** refers to the model’s structure, such as BERT or GPT, defining layers, attention heads, etc. 
* <b>Checkpoint</b> is a saved version of a model at a particular training stage, containing learned weights and configs. It’s called “checkpoint” because it marks a “save point” in training._

> [!quote] **Page **
> **Highlight:** the hidden_size attribute defines the size of the hidden_states vector, and num_hidden_layers defines the number of layers the Transformer model has.

> 💬 _Hidden size refers to the dimensionality of hidden states in the model

<b>Hidden layers</b> = depth of the Transformer, <b>attention heads</b> = number of attention heads per layer. 
More layers/heads generally improve model capacity but increase computation.

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

> The pytorch_model.bin file is known as the state dictionary; it contains all your model’s weights. The two files go hand in hand; the configuration is necessary to know your model’s architecture, while the model weights are your model’s parameters.

> [!quote] **Page **
> **Highlight:** Using a Transformer model for inference
> 
1. Prepare text: Write the input sentences to be processed. 
2. Tokenize: Use a tokenizer to convert the text into input IDs (numeric sequences). 
3. Convert to tensor: Convert input IDs into the tensor format required by the model. 
4. Input model: Use model(inputs) to input into the model. 
5. Obtain output: Get hidden states or logits, which serve as task features or final results. 

> Purpose: Convert text into numbers that can be processed by the model, extract deep semantic information through Transformer, and provide it for downstream tasks.

# Tokenizers

> [!quote] **Page **
> **Highlight:** Tokenizers are one of the core components of the NLP pipeline. They serve one purpose: to translate text into data that can be processed by the model.
> 

> [!quote] **Page **
> **Highlight:** The goal is to find the most meaningful representation — that is, the one that makes the most sense to the model — and, if possible, the smallest representation.

> 💬 _“Smallest representation” means representing the input text with the <b>fewest tokens possible</b>. Fewer tokens reduce model input length and computational cost. For example, “tokenization” split into “token” + “ization” is smaller and more efficient than splitting it into characters.
> 
> 
> <b>Hidden layers</b> = depth of the Transformer, <b>attention heads</b> = number of attention heads per layer. 
More layers/heads generally improve model capacity but increase computation.

> [!quote] **Page **
> **Highlight:** Creating a model from the default configuration initializes it with random values:

> 💬 _The model initializes randomly because it has not been trained yet. You must either <b>train it from scratch</b> or <b>load pretrained weights</b>; otherwise, it will output meaningless results._

> [!quote] **Page **
> **Highlight:** Word-based

> 💬 _<b>Tokenizer 类型</b> <b>原理</b> <b>优点</b> <b>缺点</b> <b>Word-based</b> 以空格或规则划分成单词简单直观，词义完整词表巨大，OOV（未知词）多 <b>Character-based</b> 每个字符为一个 token 词表小，几乎无 OOV 序列长，单个字符语义少 <b>Subword</b> 高频词不拆，低频词拆成有意义的子词，如 “token”+“ization” 兼顾 OOV 和词表大小，效率高，语义保持较好构建和训练更复杂


> [!quote] **Page **
> **Highlight:** from transformers import BertTokenizer tokenizer = BertTokenizer.from_pretrained("bert-base-cased")

> 💬 _<b>AutoTokenizer</b> works the same but is more flexible. It automatically selects the correct tokenizer class (e.g., BertTokenizer) based on the checkpoint.

> [!quote] **Page **
> **Highlight:** Translating text to numbers is known as encoding. Encoding is done in a two-step process: the tokenization, followed by the conversion to input IDs.
> 

> [!quote] **Page **
> **Highlight:** The second step is to convert those tokens into numbers, so we can build a tensor out of them and feed them to the model. To do this, the tokenizer has a vocabulary, which is the part we download when we instantiate it with the from_pretrained() method. Again, we need to use the same vocabulary used when the model was pretrained.

# Handling multiple sequences

<b>Hidden layers</b> = depth of the Transformer, <b>attention heads</b> = number of attention heads per layer. 
More layers/heads generally improve model capacity but increase computation.

> [!quote] **Page **
> **Highlight:** Creating a model from the default configuration initializes it with random values:

> 💬 _The model initializes randomly because it has not been trained yet. You must either <b>train it from scratch</b> or <b>load pretrained weights</b>; otherwise, it will output meaningless results.


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

* Quantity Limit: 
Theoretically, <b>batch_size</b> depends on GPU memory/RAM, but the model itself does not limit batch_size. 
* <b>Length Limit</b>: 
Most models (such as BERT) have a maximum length limit for a single sentence, usually 512 tokens. If the length exceeds this, the tokenizer will automatically truncate.

* How to avoid: 
 <b>Sliding window</b> (sliding window) technology can be used to input long texts in chunks to the model. 
 <b>Models</b> that support long sequences such as Longformer, BigBird can also be used. 

* The impact of truncation: 
 Truncation may result in the loss of key information, especially in NLP tasks where important information in long sentences is often at the end. 
 A more reasonable approach is to process segments and aggregate contextual information rather than directly truncate.

# Putting it all together

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
