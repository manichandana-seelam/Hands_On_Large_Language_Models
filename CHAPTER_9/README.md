             CHAPTER 9 = MULTI MODEL LARGE LANGUAGE MODELS

1. Multimodal Large Language Models (MLLMs)

Multimodal models can understand and process different types of data such as text, images, audio, and video. Traditional LLMs only understand text, but multimodal models combine multiple data types to improve their abilities. They can answer questions about images, describe pictures, and perform tasks that require visual understanding.

2. Transformers for Vision (Vision Transformer - ViT)

Vision Transformer (ViT) applies the Transformer architecture to images instead of text. Since images do not contain words, ViT divides an image into small patches and treats them like text tokens. These patches are converted into embeddings and passed through the Transformer encoder to understand image information.

3. Image Patches and Embeddings

In text models, words are converted into tokens, but images are converted into small image patches. Each patch is transformed into a numerical representation called an embedding. These embeddings allow the Transformer model to process images similar to how it processes text.

4. Multimodal Embedding Models

Multimodal embedding models create embeddings for different types of data, such as images and text, in the same vector space. This allows the model to compare the meaning of images and text. For example, a text description like "a puppy playing" can be matched with a similar puppy image.

5. CLIP (Contrastive Language-Image Pretraining)

CLIP is a multimodal embedding model that connects images and text. It uses two encoders: one for images and one for text, and converts both into embeddings of the same size. It learns by making related image-text pairs closer and unrelated pairs farther apart using contrastive learning.

6. Applications of CLIP

CLIP embeddings can be used for many tasks such as zero-shot classification, image search, clustering, and image generation. It can identify an image category without additional training by comparing image embeddings with text descriptions. It can also search images using a text query.

7. How CLIP Generates Embeddings

CLIP takes an image-caption pair and creates embeddings using an image encoder and text encoder. The similarity between these embeddings is calculated using cosine similarity. During training, CLIP improves by increasing similarity between matching image-text pairs and decreasing similarity between incorrect pairs.

8. OpenCLIP

OpenCLIP is an open-source implementation of the CLIP model. It can process both images and text to create embeddings. The image is resized and converted into pixel values, while text is converted into tokens before generating embeddings.

9. Text and Image Embeddings in CLIP

CLIP converts text into text embeddings and images into image embeddings of the same dimension. Since both embeddings exist in the same vector space, their similarity can be calculated. Higher similarity means the image and text are more related.

10. Making Text Generation Models Multimodal

Normal LLMs only understand text, so they cannot directly reason about images. Multimodal generation models add vision capabilities by connecting an image encoder with an LLM. This allows models to answer questions about images and generate text based on visual information.

11. BLIP-2

BLIP-2 connects a pretrained Vision Transformer (ViT) with a pretrained language model using a Querying Transformer (Q-Former). Instead of training a complete model from scratch, it only trains the connection between vision and language. This makes image understanding possible with existing LLMs.

12. Q-Former in BLIP-2

Q-Former acts as a bridge between the image encoder and the language model. It extracts useful visual information from images and converts it into a format that the LLM can understand. These visual features work like prompts for the language model.

13. Training Process of Q-Former

Q-Former is trained using image-text pairs to learn relationships between images and text. It uses tasks like image-text matching, image-text contrastive learning, and image-based text generation. These tasks help it learn meaningful visual representations.

14. BLIP-2 Processing Pipeline

BLIP-2 first processes an image using a vision encoder to extract visual features. The Q-Former converts these features into language-compatible embeddings. The LLM then uses these embeddings along with text input to generate responses.

15. Preprocessing Multimodal Inputs

A processor prepares both images and text before sending them to the model. Images are resized, normalized, and converted into pixel values. Text is converted into token IDs using a tokenizer so that the model can understand it.

16. Image Captioning Using BLIP-2

Image captioning is the task of generating a description of an image automatically. BLIP-2 processes the image, extracts visual information, and generates a text caption. It can describe objects, scenes, and activities present in an image.

17. Multimodal Chat-Based Prompting

BLIP-2 can answer questions about images by combining an image with a text prompt. Instead of only generating captions, it can perform visual question answering. Users can ask follow-up questions and interact with the model like a chatbot.

18. Overall Chapter Summary

This chapter explains how LLMs become multimodal by combining vision and language capabilities. ViT helps convert images into embeddings, CLIP connects images and text in a shared space, and BLIP-2 enables image-based conversations. These technologies allow applications like image search, captioning, and visual chat assistants.