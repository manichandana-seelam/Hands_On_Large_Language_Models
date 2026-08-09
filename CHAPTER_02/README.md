                           CHAPTER 2 - TOKENS AND EMBEDDINGS

1. Tokens

Tokens are the smallest units of text that an LLM processes. A token can be a word, part of a word, punctuation mark, or even a single character. Before understanding text, every sentence is first converted into tokens.

2. Tokenization

Tokenization is the process of splitting text into tokens. The tokenizer then converts these tokens into numerical IDs that the language model can understand. Different models use different tokenization methods.

3. Why Tokenization is Important

Language models cannot understand raw text directly. Tokenization converts human language into numbers that the model can process. Good tokenization improves efficiency and helps the model understand different languages and rare words.

4. Types of Tokens

A tokenizer may split text into words, subwords, characters, or bytes. The choice depends on the tokenizer and the language model. Subword tokenization is the most common because it handles unknown words effectively.

5. Token IDs

After tokenization, every token is assigned a unique numerical ID from the tokenizer's vocabulary. These IDs become the actual input to the language model. The model processes numbers instead of text.

6. Vocabulary

A vocabulary is the complete list of tokens known by a tokenizer. Every token has a unique ID in this vocabulary. Different models have different vocabulary sizes and token sets.

7. Special Tokens

Special tokens have predefined meanings for the model. They are used to indicate the beginning or end of text, separate sentences, or represent padding and unknown words. These tokens help the model process text correctly.

8. Tokenizer Algorithms

Different tokenizers use different algorithms to split text. The three major algorithms are BPE (Byte Pair Encoding), WordPiece, and SentencePiece. Each algorithm creates tokens differently but aims to represent text efficiently.

9. BPE (Byte Pair Encoding)

BPE starts with individual characters and repeatedly combines the most common character pairs into larger tokens. It reduces vocabulary size while still handling unknown words. GPT-2 mainly uses BPE.

10. WordPiece

WordPiece is similar to BPE but chooses token combinations based on probability instead of frequency. It creates meaningful subword tokens that improve language understanding. BERT uses the WordPiece tokenizer.

11. SentencePiece

SentencePiece treats the input as raw text without depending on spaces between words. It works well for languages like Japanese and Chinese. Models such as T5 and Llama commonly use SentencePiece.

12. Embeddings

Embeddings are numerical vectors that represent the meaning of words or tokens. Similar words have similar embedding vectors. Embeddings allow computers to understand relationships between words.

13. Token Embeddings

Every token in the tokenizer's vocabulary has its own embedding vector stored inside the language model. These vectors are learned during training and represent the meaning of each token. The embedding matrix is an important part of every pretrained model.

14. Contextualized Word Embeddings

Unlike Word2Vec, language models create different embeddings for the same word depending on its context. This helps the model understand words with multiple meanings. Contextualized embeddings improve many NLP tasks.

15. Text Embeddings

Text embeddings represent an entire sentence, paragraph, or document using a single vector. They capture the overall meaning of the text instead of individual words. They are widely used in semantic search, retrieval, and document comparison.

16. Word2Vec

Word2Vec is an early method for creating word embeddings. It learns word meanings by observing neighboring words using techniques like Skip-Gram and Negative Sampling. Although useful, it has mostly been replaced by contextual embeddings from language models.

17. Skip-Gram

Skip-Gram is a Word2Vec training method. It predicts surrounding words from a given input word. This helps the model learn relationships between words that appear in similar contexts.

18. Negative Sampling

Negative Sampling speeds up Word2Vec training by updating only a few incorrect examples instead of the entire vocabulary. It makes training faster while maintaining embedding quality.

19. Embeddings for Recommendation Systems

Embeddings are widely used in recommendation systems. They help find similar users, products, movies, songs, or articles based on their vector representations.

