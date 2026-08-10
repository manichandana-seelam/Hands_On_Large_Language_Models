                    CHAPTER-10 CREATING TEXT EMBEDDING MODELS .

                    
1. Embedding Models

Embedding models convert text into numerical vectors called embeddings. These vectors represent information about the meaning of the text. Similar sentences should generally have similar embeddings, making embeddings useful for search, classification, clustering, and RAG.

2. Contrastive Learning

Contrastive learning teaches a model by using similar and dissimilar examples. The model learns to make similar texts closer in vector space and different texts farther apart. It is one of the main techniques used for training sentence embedding models.

3. BERT

BERT is a pretrained Transformer encoder that understands words based on their context. It produces contextual representations for tokens, but basic BERT is not specifically trained to produce good sentence embeddings. It can be used as the Transformer part of a Sentence Transformer.

4. Cross-Encoder

A Cross-Encoder sends two sentences together through BERT and directly predicts their relationship or similarity. It is usually accurate because both sentences interact inside the model. However, it is slow when a large number of sentence pairs need to be compared.

5. SBERT / Bi-Encoder

SBERT processes the two sentences separately and creates an embedding for each sentence. These embeddings can then be compared using cosine similarity. Because embeddings can be created and stored beforehand, SBERT is much faster than a Cross-Encoder for search and retrieval.

6. MNLI Dataset

MNLI is an NLI dataset containing sentence pairs and three labels: Entailment, Neutral, and Contradiction. It can be used to train embedding models because it provides information about the relationship between sentences.

7. Softmax Loss

Softmax Loss treats the relationship between two sentences as a classification problem. The model predicts Entailment, Neutral, or Contradiction and compares the prediction with the actual label. The loss is then used to update the model weights.

8. Cosine Similarity Loss

Cosine Similarity Loss teaches the model how similar two sentences should be. It compares the cosine similarity of their embeddings with a target similarity score. Similar sentences should have high similarity, while dissimilar sentences should have low similarity.

9. Multiple Negatives Ranking Loss

MNR Loss uses an anchor and a correct positive sentence, while other sentences act as negatives. The model learns to make the anchor-positive pair more similar than the incorrect pairs. It is especially useful for semantic search and retrieval.

10. Easy Negatives

Easy negatives are randomly selected incorrect examples that are usually completely unrelated to the anchor. Because they are obviously wrong, the model can reject them easily. They provide useful training data but may not teach the model very detailed differences.

11. Semi-Hard Negatives

Semi-hard negatives are somewhat related to the anchor but are not the correct answer. They can be found using a pretrained embedding model and semantic similarity. They are more challenging than random negatives but may still be relatively easy.

12. Hard Negatives

Hard negatives are very similar to the anchor but are still incorrect. They force the model to understand small differences in meaning and therefore can improve the quality of embeddings. They can be created or selected using humans, models, or negative-mining methods.

13. STSB Evaluation

STSB contains sentence pairs with human similarity scores. The evaluator creates embeddings for both sentences, calculates cosine similarity, and compares it with the human score. STSB is mainly used to check how well an embedding model understands sentence similarity.

14. MTEB

MTEB is a large benchmark for evaluating embedding models across many different tasks and datasets. It includes tasks such as classification, retrieval, clustering, and similarity. It provides a broader evaluation than STSB.

15. Training from Scratch

With training from scratch, we can start with a basic pretrained Transformer such as bert-base-uncased and train it for sentence embeddings. The model learns from sentence pairs using a loss function. This usually requires more training compared with starting from an existing embedding model.

Fine-Tuning
16. Fine-Tuning

Fine-tuning means taking an already trained model and training it further on new data. It is usually easier and faster than building an embedding model from a basic Transformer. The goal is to make the existing model work better for your data or task.

17. Supervised Fine-Tuning

In supervised fine-tuning, we start with a pretrained embedding model such as all-MiniLM-L6-v2 and train it using labelled examples. The labels or positive/negative pairs tell the model what it should learn. MNR Loss or Cosine Similarity Loss can be used for this process.

18. Augmented SBERT

Augmented SBERT is useful when only a small amount of labelled data is available. A Cross-Encoder is first trained on the small Gold Dataset, then labels new sentence pairs to create a larger Silver Dataset. Gold and Silver data are then used to train SBERT.

19. Gold Dataset

The Gold Dataset is a small dataset containing trusted, usually human-created labels. It represents the ground truth for the task. It is used to train the Cross-Encoder in Augmented SBERT.

20. Silver Dataset

The Silver Dataset contains new sentence pairs that have been labelled automatically by the trained Cross-Encoder. Its labels may not always be perfectly correct, but it provides much more training data. The Gold and Silver datasets can then be combined.

Unsupervised Learning
21. Unsupervised Learning

Unsupervised learning is used when we have text but no predefined labels. The model creates its own learning objective from the available text. Examples discussed in the chapter include SimCSE, Contrastive Tension, TSDAE, and GPL.

22. TSDAE

TSDAE is an unsupervised method that randomly removes words from a sentence to create a damaged version. The encoder converts the damaged sentence into an embedding, and the decoder tries to reconstruct the original sentence. This teaches the encoder to create useful sentence representations.

23. Encoder and Decoder

The encoder converts the damaged sentence into a sentence embedding. The decoder uses that embedding to reconstruct the original sentence during training. After training, the encoder is mainly used to generate embeddings.

24. Mean Pooling

Mean pooling averages the token representations produced by the Transformer to create one sentence embedding. It is a common default pooling strategy when using a basic BERT model with Sentence Transformers. It combines information from all token representations.

25. CLS Pooling

CLS pooling uses the special [CLS] token representation as the sentence embedding. In the TSDAE approach discussed in the chapter, CLS pooling was found to work better than mean pooling. It can be explicitly selected by manually creating the Transformer and Pooling modules.

Domain Adaptation
26. Domain Adaptation

Domain adaptation means making an existing model better at understanding a specific field, such as medical, banking, or legal text. The target domain may contain vocabulary and concepts that were not common in the model's original training data.

27. Adaptive Training

Adaptive training, or adaptive pretraining, uses unlabelled text from the target domain to make a pretrained model more familiar with that domain. TSDAE or masked language modelling can be used for this. It prepares the model before task-specific fine-tuning.

28. Fine-Tuning After Domain Adaptation

After adaptive training, the domain-adapted model can be fine-tuned using labelled data for a specific task. For example, TSDAE can first adapt a model to banking text, followed by supervised MNR training on labelled banking pairs. This combines domain knowledge with task-specific learning.

29. Data Quality

Good training data is extremely important for embedding models. Positive pairs should be meaningful, and useful negative or hard-negative examples can greatly improve learning. A large dataset is not automatically good if the examples are poor.

30. Overall Chapter Summary

The chapter explains how to create, train, evaluate, fine-tune, and adapt embedding models. It covers BERT, Cross-Encoder, SBERT, Softmax Loss, Cosine Similarity Loss, MNR Loss, negative mining, Augmented SBERT, and TSDAE. The main lesson is that a good pretrained embedding model plus high-quality training data can be adapted effectively to specific tasks and domains.