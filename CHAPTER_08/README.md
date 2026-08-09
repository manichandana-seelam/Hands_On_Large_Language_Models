               CHAPTER 8 = SEMANTIC SEARCH AND RAG

1. Semantic Search

Semantic search finds information based on the meaning of the query, not only exact keywords. It uses language models and embeddings to understand that different words can have similar meanings. This helps find relevant results even when the query and document use different words.

2. Dense Retrieval

Dense retrieval converts both the query and documents into embeddings (vectors). It then finds the documents whose vectors are closest to the query vector. Documents with similar meanings are usually closer together in the embedding space.

3. Dense Retrieval with FAISS

In dense retrieval, text is first split into chunks and converted into embeddings. FAISS can store these vectors and quickly find the nearest ones for a new query. The result with the smallest distance is considered the most similar result.

4. Dense Retrieval vs Keyword Search

Keyword search looks mainly for matching words, while dense retrieval looks for similar meaning. For example, a semantic search can understand that “how precise was the science” relates to “scientific accuracy” even though the exact words are different. Keyword search can still be better when an exact phrase or word is important.

5. Limitations of Dense Retrieval

Dense retrieval can still return results even when the correct answer is not present. It may also struggle with exact phrase matching and with specialized domains that were not well represented during training. Because of this, hybrid search, which combines keyword and semantic search, can be more useful.

6. Chunking Long Texts

Long documents are divided into smaller chunks before creating embeddings because models have limited context sizes. Chunks can be sentences, paragraphs, or groups of sentences. Overlapping chunks can preserve surrounding context and improve retrieval.

7. One Vector vs Multiple Vectors per Document

A document can be represented by one vector, but this may lose important information. Using multiple vectors for smaller chunks gives better coverage and allows the system to find specific information inside a long document. Therefore, multiple vectors per document are usually more expressive.

8. Nearest Neighbor Search and Vector Databases

Nearest neighbor search finds vectors that are closest to the query vector. NumPy can work for smaller datasets, while FAISS and Annoy are useful for large collections. Vector databases such as Weaviate and Pinecone also support adding, deleting, and filtering vectors more easily.

9. Fine-Tuning Embedding Models

Embedding models can be fine-tuned to become better at retrieval. Training data contains relevant and irrelevant query-document pairs. Fine-tuning brings relevant queries closer to the correct document and pushes irrelevant queries farther away.

10. Reranking

Reranking is a second step in a search pipeline. First, a search system retrieves a smaller set of possible results, and then a reranker checks their relevance and changes their order. This can greatly improve the quality of the final search results.

11. Cross-Encoder Rerankers

A reranker can work as a cross-encoder, where the query and one result are given to the model together. The model gives a relevance score, usually from 0 to 1. Higher scores mean the document is more relevant to the query.

12. Two-Stage Search Pipeline

A common search system has two stages. The first stage quickly retrieves candidates using keyword search, dense retrieval, or hybrid search. The second stage uses a reranker to select and reorder the best results.

13. Retrieval Evaluation

Search systems need a test collection containing documents, queries, and information about which documents are relevant. The system is then evaluated by checking whether relevant documents appear in good positions. Metrics such as MAP and nDCG are commonly used for this purpose.

14. Average Precision (AP)

Average Precision measures how well a system places relevant documents in the search results. A relevant document appearing near the top gets a better score than one appearing lower down. It is calculated by considering precision at the positions where relevant documents appear.

15. Mean Average Precision (MAP)

MAP is the average of the Average Precision scores across multiple queries. It gives one overall score for a search system. A higher MAP generally means the system is better at retrieving relevant results and placing them near the top.

16. nDCG

nDCG is another search evaluation metric. Unlike simple relevant/not-relevant evaluation, it can handle different levels of relevance. It also gives more importance to highly relevant results appearing near the top of the ranking.

Retrieval-Augmented Generation (RAG)
17. What is RAG?

RAG combines search and text generation. First, the system retrieves relevant information from a data source, and then gives that information to the LLM to generate an answer. This helps reduce hallucinations and makes answers more grounded in real information.

18. Grounded Generation

In grounded generation, the LLM receives the user's question together with retrieved documents. The retrieved information provides the context needed to answer the question. This helps keep the model's answer connected to the available source data.

19. Basic RAG Pipeline

A basic RAG system follows this flow: Question → Retrieval → Relevant Documents → LLM → Answer. The retriever finds useful information, and the LLM uses that information to produce the final response.

20. RAG with Local Models

RAG can also be built using local models instead of managed APIs. An embedding model converts text into vectors, a vector database such as FAISS stores them, and a local language model generates the answer. LangChain can be used to connect these parts into a RAG pipeline.

Advanced RAG Techniques
21. Query Rewriting

Sometimes a user's question is too long, unclear, or depends on previous conversation. Query rewriting uses an LLM to convert it into a clear search query that is easier for the retriever to understand.

22. Multi-Query RAG

Some questions need information from different searches. Multi-query RAG creates multiple search queries from one user question, retrieves results for each query, and gives the combined information to the LLM.

23. Multi-Hop RAG

Multi-hop RAG is used for questions that need several steps of searching. The answer from one search helps create the next search query. This continues until enough information is collected to answer the original question.

24. Query Routing

Query routing allows the system to choose which data source to search. For example, an HR question can be sent to an HR database while customer-related questions can be sent to a CRM system.

25. Agentic RAG

Agentic RAG gives the LLM more responsibility for deciding what information it needs, which tools to use, and what actions to take. Instead of following only a fixed pipeline, the LLM can dynamically interact with different data sources and tools.

RAG Evaluation
26. Fluency

Fluency checks whether the generated answer is clear, natural, and well-written. The response should be easy to read and logically connected.

27. Perceived Utility

Perceived utility checks whether the answer is actually useful and informative for the user. A fluent answer is not enough if it does not properly help with the question.

28. Citation Recall

Citation recall measures how many statements about the outside world are properly supported by citations. Higher citation recall means more of the factual claims have supporting sources.

29. Citation Precision

Citation precision checks whether the given citations actually support the statements they are attached to. A citation should provide evidence for the specific claim being made.

30. LLM-as-a-Judge

Instead of relying only on humans, another capable LLM can evaluate generated answers. It can score aspects such as usefulness, correctness, and citation quality. This approach is called LLM-as-a-judge.

31. Ragas Metrics

Ragas is a library used to evaluate RAG systems. It includes metrics such as faithfulness and answer relevance. Faithfulness checks whether the answer stays consistent with the retrieved context, while answer relevance checks whether the answer properly addresses the question.
