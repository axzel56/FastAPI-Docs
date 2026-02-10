Transformers is a **neural network architecture** used for performing machine learning processing (NLP) and computer vision.
Excels at processing sequential data like text by using self-attention mechanisms to weigh importance of different parts of the input, enabling parallel processing and deep contextual understanding.
## What are Transformers?

- Neural Network Architecture for NLP & Vision
- Introduced in 2017: "Attention is All You Need"
- Processes whole sentences in parallel

## Need of Transformers

- RNNs loose context in long sentences.
- Transformers use self-attention for full context
- Example: "point" means different things in different sentences

## Need for Transformers Model in Machine Learning

**Transformer Architecture** uses self-attention to transform one whole sentence into a single sentence.

Traditional models like **RNNs (Recurrent Neural Networks)** suffer from the vanishing gradient problems.


# Core Concepts:
## Self - Attention: 
Allows the model to weigh the relevance of all other words in a sequence when processing a single word, capturing long-range dependencies.
  This is calculated using a scaled dot-product attention approach.
  Each word in a sequence is mapped to three vectors.
  - Query (Q)
  - Key (K)
  - Value (V)
  Attention scores are computed as:
  `Attention(Q,K,V) = softmax(QK^T / root(dk))V`

- Encoder-Decoder: The Encoder processes input, creating context; the decoder uses this context to generate output, using both self attention and attention to the encoded input.
- Parallel Processing: Transformers process tokens simultaneously, drastically speeding up training.



