Semantic AI integrates meaning, context and relationships into AI.

It uses technologies like keyword to understand intent using tech like knowledge graphs and NLP to convert to connect data and concepts for smarter applications like improved search.

Examples
- Recognizing "account number" and "customer ID" as related concepts.
- Understanding "rock music" (genre) vs. "rock" (stone).
- Analyzing inconsistencies in an email's context to spot threats, not just keywords.

# Vector Embedding

1. Tokenization: The input text is broken into smaller units called tokens (words, sub-words or characters). OpenAI uses byte-pair encoding (BPE) for this.
2. Initial Representation: Each token is converted to initial numerical representation
3. Neural Network Processing: These representations are then passed through the deep layers of NN (based on Transformer Architecture) uses self-attention mechanisms to understand the relationships.
4. Learning context: Network adjusts the internal weights (parameters) through the model to represent words with similar meanings or that appear in similar context as vectors that are closer together in the Multi-Dimensional space.
5. Vector Generation: The final output of this process is a dense vector (an array of numbers) that encapsulates the contextual and semantic info of the original text snippet or input query.


Representing data in terms of Mathematical Vector Embedding (array of numbers). In this system, the similar items are kept closer and vice versa.

We perform` similarity searches` as mathematical operations.

Vector Embedding are created from Vector Embedding Models trained on Large Vector Dataset

### Embedding Model

#### Image - CLIP
#### Text - Glove
#### Audio - Wav2Vec


# Vector Indexing

ANN Algorithm - HSNW, IVF


# Cosine Similarity

Cosine similarity measures how similar two non-zero vectors are by calculating the cosine of the angle between them, indicating directional similarity rather than magnitude.
Resulting in a score -1 (opposite) to 1(identical direction)

Technologies like [recommendation engines](https://www.ibm.com/think/topics/recommendation-engine#:~:text=A%20recommendation%20engine%2C%20also%20called,items%20based%20on%20those%20patterns.) and [large language models](https://www.ibm.com/think/topics/large-language-models) (LLMs) use cosine similarity to identify which content is most relevant and which responses make the most “sense.”

These decisions are made by analyzing relationships between data points in high-dimensional or sparse datasets

### Sparse Dataset

![[0_lg8CUY8XaDBgTiMI.webp]]

Sparse Dataset is essentially a dataset where most of the values are either zero or empty

### Common Domains of Sparse Dataset

1. Text Data: When processing large text, tools like TF-IDF (Term Frequency-Inverse Document Frequency) converts words into vectors. A text doc has few relevant words, with the rest of dictionary being unused, making the resulting vectors sparse.
2. Recommendation System: Users rate only fractions of all available movies or products. These user-item interaction matrices are highly sparse because most users interact with only a small percentage of the items.


```python
from sklearn.feature_extraction.text import TfidfVectorizer

documents = ["Sparse datasets are common in NLP",  
"Machine learning can handle sparse matrices",  
"TF-IDF helps represent sparse text data"]

vectorizer = TfidVectorizer()
X = vectorizer.fit_transformer(documents)
print(X) # 

```

### Storing Sparse Data
When storing a large dataset, the empty values just stores empty values which are not so efficient even matrix operations are quite slower.

Common formats for storing data:

1. COO (Coordinate Format): The COO Format stores the coordinate of non-zero elements along with their values. Its easy to construct but not the most efficient for computations.
2. CSR (Compressed Sparse Rows): In this format, we store the non-zero values row by row compressing the data by keeping track of where each rows starts and ends. This format is faster for row-based operations, like matrix-vector multiplication.
3. CSC (Compressed Sparse Column): The the operations are column-based, This format is similar to CSR but compresses the data column by column instead of row by row.

