# LSH Implementation 

The Implementation of the project is divided into four substeps which includes::

## 1. **Reading the Input Content and Text Preprocessing**

This involves loading data from the following files:
- `ids.txt`: Contains the document IDs.
- `texts.txt`: Contains the text data corresponding to the document IDs.

Text preprocessing typically involves several operations:
- **Lowercase conversion**: Ensures uniformity by converting all text to lowercase.
- **Removing punctuation**: Cleans the text to focus on words.
- **Tokenization**: Splits the text into individual words or tokens.

Further, the preprocessing may also include:
- **Stopword removal**: Eliminates common words (e.g., "the", "is", "and") which do not contribute much meaning.
- **Stemming/Lemmatization**: Reduces words to their base forms (e.g., "running" → "run") to standardize the text, improving the comparison process.

## 2. **Vectorizing the Text with TF-IDF**

**TF-IDF** (Term Frequency-Inverse Document Frequency) is a technique used to convert text into numerical vectors. The process weighs terms based on two factors:

- **Term Frequency (TF)**: Measures how often a word appears in a document.
- **Inverse Document Frequency (IDF)**: Measures how rare a word is across all documents.

This method captures the relative importance of words, allowing for meaningful comparisons between documents. TF-IDF representation is effective for identifying key terms and measuring document similarity.

## 2. **Vectorizing the Text with TF-IDF**

**TF-IDF** (Term Frequency-Inverse Document Frequency) is a technique used to convert text into numerical vectors. The process weighs terms based on two factors:

- **Term Frequency (TF)**: Measures how often a word appears in a document.
- **Inverse Document Frequency (IDF)**: Measures how rare a word is across all documents.

This method captures the relative importance of words, allowing for meaningful comparisons between documents. TF-IDF representation is effective for identifying key terms and measuring document similarity.

---

### Proper Working of TF-IDF:

**TF-IDF** stands for Term Frequency-Inverse Document Frequency. It measures how important a word is in a document within a collection of documents.

The TF-IDF value for a term is calculated by multiplying two metrics:

1. **Term Frequency (TF)**: The number of times a term appears in a document, normalized by the total number of terms in the document.

   $$
   TF(t, d) = \frac{\text{Number of times term } t \text{ appears in document } d}{\text{Total number of terms in document } d}
   $$

2. **Inverse Document Frequency (IDF)**: A measure of how rare a term is across all documents. The more rare a term is, the higher its IDF value.

   $$
   IDF(t) = \log \left(\frac{N}{n_t}\right)
   $$

   Where:
   - \( N \) = Total number of documents in the corpus
   - \( n_t \) = Number of documents containing the term \( t \)

The final **TF-IDF** score for a term is the product of the term frequency and inverse document frequency:

---

By applying this formula, TF-IDF identifies important words in the document that are also relatively unique across the corpus.


## 3. **Implementing LSH for Finding Similarity**

**LSH** (Locality-Sensitive Hashing) is used to approximate similarity search, enabling efficient identification of similar documents. It works by:
- Hashing similar items into the same "buckets" with high probability.

For text data, **MinHash** is commonly employed. It creates multiple hash functions to generate a signature for each document, allowing quick retrieval of potential similar items without performing exhaustive pairwise comparisons.

---

## 4. **Evaluating the Accuracy by Comparing with Ground Truth**

This step evaluates the performance of the LSH implementation by comparing its results to the provided ground truth in the `items.json` file. The evaluation process involves:
- Calculating **intersection scores** between the predicted and actual similar items for each document.
- Computing the **average score** across all documents to assess the overall model performance.

