                           CHAPTER 2 - LOOKING INSIDE THE LARGE LANGUAGE MODELS

1. Overview of a Transformer LLM

A Transformer-based LLM takes text as input and generates text as output. It predicts one token at a time and adds each generated token back to the input. This repeated prediction process is called autoregressive generation.

2. Main Components of a Transformer LLM

A Transformer LLM consists of three main components: the Tokenizer, Transformer Blocks, and the Language Modeling (LM) Head. The tokenizer prepares the input, the Transformer blocks process it, and the LM Head predicts the next token. Together, these components generate meaningful text.

3. Tokenizer

The tokenizer breaks text into smaller units called tokens. It converts these tokens into numerical token IDs, which are then transformed into embedding vectors. The model processes these embeddings instead of raw text.

4. Transformer Blocks

Transformer blocks perform most of the computation inside the model. Each block receives token representations, improves them using attention and feedforward processing, and passes the updated representations to the next block. Modern LLMs contain many Transformer blocks stacked together.

5. Language Modeling (LM) Head

The LM Head is the final layer of the model. It converts the output vectors from the Transformer blocks into probability scores for every token in the vocabulary. These scores are used to select the next generated token.

6. Forward Pass

A forward pass is one complete execution of the input through the model. During this process, embeddings pass through all Transformer blocks before reaching the LM Head. Each forward pass predicts only one new token.

7. Decoding (Sampling)

Decoding is the process of selecting one token from the probability distribution produced by the LM Head. Different decoding strategies determine how the next token is chosen. The selected token becomes part of the input for the next prediction.

8. Parallel Token Processing

Transformers process all input tokens simultaneously during a forward pass. Each token has its own processing stream while interacting with other tokens through attention. This parallel computation makes Transformers highly efficient.

9. Context Length

Context length is the maximum number of tokens a model can process at one time. The model uses only the tokens within this context while making predictions. Larger context lengths allow the model to understand longer inputs.

10. Key-Value (KV) Cache

KV Cache stores the previously computed Keys and Values during text generation. This prevents the model from recomputing attention for earlier tokens in every generation step. KV Cache significantly speeds up inference.

11. Transformer Block

A Transformer block consists mainly of a Self-Attention Layer and a Feedforward Neural Network. The attention layer captures contextual information, while the feedforward layer performs most of the computation. Modern blocks also include normalization and residual connections.

12. Feedforward Neural Network (FFN)

The Feedforward Neural Network stores much of the knowledge learned during training. It recognizes language patterns, facts, and relationships between words. It also helps the model generalize to inputs that were not seen during training.

13. Self-Attention

Self-attention enables each token to gather relevant information from other tokens in the input. It helps the model understand context and relationships between words. This improves the quality of language understanding and prediction.

14. Query, Key, and Value (QKV)

Each token is transformed into three vectors called Query, Key, and Value. Queries determine what information is needed, Keys describe the available information, and Values contain the information to be shared. Their interaction forms the basis of the attention mechanism.

15. Multi-Head Attention

Multi-head attention performs several attention operations in parallel. Each attention head learns different relationships between tokens. The outputs of all heads are combined to produce a richer representation.

16. Recent Improvements to the Transformer

Modern Transformers include architectural improvements that increase speed, reduce memory usage, and improve accuracy. Techniques such as Grouped Query Attention (GQA) and Flash Attention are widely adopted. These improvements make modern LLMs more efficient than the original Transformer.

17. Modern Transformer Block Improvements

Recent Transformer blocks use Pre-Normalization, RMSNorm, and SwiGLU instead of older techniques. These changes improve training stability, efficiency, and model performance. Modern architectures also integrate GQA and RoPE.

18. Rotary Positional Embeddings (RoPE)

RoPE provides positional information by rotating the Query and Key vectors during attention. It enables the model to understand both the order and relative positions of tokens. RoPE improves long-context performance compared to earlier positional embedding methods.

19. GPT vs BERT

GPT is a decoder-only model designed for text generation using previous tokens. BERT is an encoder-only model that processes both previous and future tokens for language understanding. They are designed for different natural language processing tasks.

20. Overall Working of a Transformer LLM

The tokenizer converts text into embeddings, which are processed by multiple Transformer blocks. The LM Head predicts the probability of the next token, and a decoding strategy selects one token. This process repeats until the complete response is generated.