                    # CHAPTER-4  TEXT CLASSIFICATION

1. Introduction to Text Classification

Text classification is the task of assigning a category or label to a piece of text, such as positive/negative sentiment, spam/not spam, or language detection. In this chapter, pretrained language models are used instead of training models from scratch. The chapter compares representation models (BERT, RoBERTa, Sentence Transformers) and generative models (Flan-T5, ChatGPT) for classification.

2. The Rotten Tomatoes Dataset

The Rotten Tomatoes dataset contains movie reviews labeled as positive (1) or negative (0). It is divided into training, validation, and test sets. The training set is used to train models, while the test set is used to evaluate how well the model predicts unseen reviews.

3. Text Classification with a Task-Specific Model

A task-specific model is already fine-tuned for a particular task, such as sentiment analysis. We load the pretrained RoBERTa sentiment model and directly pass movie reviews to it. The model predicts the sentiment without any additional training, making it simple and fast to use.

4. Running Inference and Making Predictions

Inference means using a trained model to make predictions on new data. Each review from the test dataset is passed to the model, which returns sentiment scores. The label with the highest score is selected as the final prediction and stored for evaluation.

5. Evaluating Model Performance

After generating predictions, the model's results are compared with the actual labels using a classification report. The report includes precision, recall, F1-score, and accuracy, which measure different aspects of the model's performance. These metrics help determine how reliable the classifier is.

6. Confusion Matrix and Performance Metrics

A confusion matrix summarizes predictions into True Positive (TP), True Negative (TN), False Positive (FP), and False Negative (FN). From these values, precision, recall, F1-score, and accuracy are calculated. These metrics provide a detailed understanding of where the model performs well and where it makes mistakes.

7. Macro Average and Weighted Average

Macro average calculates the metric for each class separately and then takes their simple average, giving equal importance to every class. Weighted average also calculates each class separately but gives more importance to classes with more samples. When the dataset is balanced, both averages are usually very similar.

8. Classification Using Embedding Models (Supervised Classification)

Instead of directly predicting labels, embedding models first convert each review into a numerical vector called an embedding. These embeddings capture the semantic meaning of the text. A separate classifier, such as Logistic Regression, is then trained on these embeddings to perform sentiment classification.

9. Sentence Transformers and Logistic Regression

Sentence Transformers generate fixed-length embeddings for every review while keeping the model frozen (no fine-tuning). Logistic Regression learns patterns from these embeddings and predicts whether a review is positive or negative. This two-step approach achieves strong performance with much lower computational cost than fine-tuning large language models.

10. Zero-Shot Classification

Zero-shot classification is used when no labeled training data is available. Instead of training a classifier, descriptive labels like "A positive review" and "A negative review" are converted into embeddings. Each review is then assigned the label whose embedding is most similar to the review embedding using cosine similarity.

11. Cosine Similarity

Cosine similarity measures how similar two embeddings are by calculating the angle between their vectors. A higher cosine similarity means the document and label have similar meanings. In zero-shot classification, the label with the highest similarity score becomes the predicted class.

12. Text Classification with Generative Models

Unlike representation models that output numerical class labels, generative models generate text as their output. They require clear instructions, called prompts, to understand the task. The generated text is then converted into numerical labels for evaluation.

13. Prompt Engineering

Prompt engineering is the process of designing and improving prompts so that a generative model produces the desired output. Well-written prompts provide clear instructions and reduce incorrect or unnecessary responses. Better prompts generally lead to more accurate classifications.

14. Using Flan-T5 for Classification

Flan-T5 is an encoder-decoder generative model trained on many instruction-following tasks. Each movie review is prefixed with a question like "Is the following sentence positive or negative?" before being sent to the model. The generated words ("positive" or "negative") are converted into numerical labels for evaluation.

15. ChatGPT for Classification

ChatGPT is a closed-source generative model accessed through the OpenAI API instead of downloading the model locally. A prompt describing the classification task and the movie review is sent to the API, and ChatGPT returns the predicted sentiment. The returned text is converted into numerical labels before evaluating the model.

16. OpenAI API and API Keys

To use ChatGPT programmatically, an OpenAI API key is required. The API key authenticates your requests and allows your program to communicate securely with OpenAI's servers. Since API usage is billed separately from the ChatGPT app, it's important to monitor usage and billing.

17. Rate Limits and API Quota

When using external APIs, requests may fail due to rate limits or insufficient API quota. Rate limits occur when too many requests are sent in a short period, while insufficient quota means the account has no available API credits. Techniques like retry mechanisms and exponential backoff help handle temporary rate-limit errors.

18. Comparison of Classification Approaches

The chapter compares four different approaches to text classification. Task-specific models are simple and require no training, embedding models need a lightweight classifier, zero-shot classification works without labeled data, and generative models rely on prompt engineering to generate predictions. Each method has different advantages depending on the availability of labeled data, computational resources, and the desired flexibility.

19. Overall Summary

This chapter introduces text classification, where language models assign labels such as positive or negative to text. It explores multiple approaches, including task-specific models, embedding-based classification, zero-shot classification, and generative models like Flan-T5 and ChatGPT. The chapter also explains how to evaluate model performance using precision, recall, F1-score, accuracy, confusion matrix, macro average, and weighted average, highlighting the strengths and use cases of each classification method.