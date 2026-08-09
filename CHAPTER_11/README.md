            CHAPTER-11 = FINE TUNING REPRESENTATION MODELS FOR CLASSIFICATION

1. Fine-Tuning

Fine-tuning means taking a pretrained BERT model and training it for a specific task.
BERT already understands general language, so we train it on our task-specific dataset.
Example: training BERT to classify movie reviews as Positive or Negative.

2. Text Classification

Text classification means giving one label to the whole sentence or text.
For example, "I loved this movie" → Positive.
BERT reads the text and predicts the most suitable class.

3. Few-Shot Learning

Few-shot learning means training a model with only a small number of examples.
For example, we may use only 16 examples for each class.
It is useful when collecting a large labeled dataset is difficult.

4. SetFit

SetFit is a method designed for few-shot text classification.
It uses a Sentence Transformer to convert sentences into useful embeddings.
It learns to keep similar sentences close and different sentences apart.

5. Zero-Shot Learning

Zero-shot learning means performing a task without providing labeled training examples.
The model is given the possible labels and tries to understand which label fits the text.
For example, classify a review as Positive or Negative without training examples.

6. Continued Pretraining

Continued pretraining means taking an already pretrained BERT and training it more on domain-specific text.
For example, train BERT further using medical text to improve its understanding of medical language.
After that, the model can be fine-tuned for a specific task.

7. Masked Language Modeling (MLM)

MLM is the training method used by BERT to learn language.
A word is hidden using [MASK], and BERT tries to predict the missing word.
Example: "The movie was [MASK]" → BERT predicts a suitable word.

8. Domain Adaptation

Domain adaptation means making a general model better at understanding a specific field or type of text.
We do this by continuing MLM training on domain-specific data.
For example, movie reviews can help BERT understand movie-related language better.

9. Named Entity Recognition (NER)

NER identifies important entities in a sentence and gives them labels.
For example, "Maarten lives in London" → Maarten = Person and London = Location.
Unlike classification, NER predicts a label for each token.

10. CoNLL-2003 Dataset

CoNLL-2003 is a commonly used dataset for Named Entity Recognition.
It contains sentences, their tokens, and NER labels.
The main labels include Person, Organization, Location, and Miscellaneous.

11. BIO Labeling

BIO tells us where an entity starts and continues.
B means Beginning, I means Inside, and O means Outside an entity.
Example: Dean → B-PER, Palmer → I-PER.

12. NER Labels

B-PER means the beginning of a person's name, while I-PER means its continuation.
B-ORG/I-ORG are for organizations and B-LOC/I-LOC are for locations.
O means the token is not part of an entity.

13. Tokenization in NER

The dataset contains words, but BERT may split a word into smaller subtokens.
For example, Maarten might become Ma + ##arte + ##n.
Therefore, the original word-level labels must be matched with these subtokens.

14. Label Alignment

Label alignment means assigning the correct NER label to every BERT subtoken.
The first subtoken gets the original B label, while following subtokens get the corresponding I label.
This makes the labels match the tokens that BERT actually processes.

15. word_ids()

word_ids() tells us which original word each token came from.
For example, Ma, ##arte, and ##n may all have the same word ID.
This helps us correctly copy the original word's NER label to its subtokens.

16. Special Tokens

BERT adds special tokens such as [CLS] at the beginning and [SEP] at the end.
These tokens are not actual words that need NER labels.
Therefore, we use -100 so the training loss ignores them.

17. Data Collator for Token Classification

A data collator prepares multiple sentences into a proper batch for training.
Since sentences have different lengths, it adds padding to make them equal in length.
For NER, it also makes sure the token labels stay aligned with the tokens.

18. Token Classification Model

For NER, we use BERT with a token-classification head.
The model produces a prediction for every token instead of one prediction for the whole sentence.
Each prediction is one of the NER labels such as B-PER, I-LOC, or O.

19. id2label and label2id

The model works with numbers, but humans understand labels like B-PER and B-LOC.
label2id converts a label into its number, while id2label converts the number back into a label.
They help us understand the model's predictions.

20. Logits and argmax

The model produces scores called logits for every possible label.
argmax selects the label with the highest score.
For example, if B-PER has the highest score for a token, the prediction is B-PER.

21. NER Evaluation

NER predictions are compared with the correct labels from the dataset.
The seqeval library is commonly used to evaluate NER performance.
It calculates metrics such as Precision, Recall, and F1-score.

22. F1 Score

F1 combines Precision and Recall into one score.
Precision tells us how many predicted entities were correct, while Recall tells us how many real entities were found.
A higher F1 score generally means better NER performance.

23. Freezing BERT Layers

Freezing means telling some BERT layers not to update during training.
Only selected layers are trained, while the frozen layers keep their pretrained knowledge.
This can reduce training time and the number of parameters being updated.

24. Classification Head

A classification head is an additional layer added on top of BERT for a specific task.
For sentiment classification, it predicts classes such as Positive and Negative.
For NER, the head predicts an NER label for each token.

25. Training vs Inference

During training, the model receives input along with the correct labels and learns from its mistakes.
During inference, we give the model new text and ask it to make predictions.
The trained model can then identify sentiment or named entities in unseen text.

26. Summary

BERT can be fine-tuned for tasks like text classification and NER, while SetFit helps when only a few examples are available.
Continued pretraining with MLM helps BERT learn better from domain-specific text by predicting masked words.
In NER, BERT predicts a label for each token, and label alignment and F1-score are used for proper training and evaluation.
