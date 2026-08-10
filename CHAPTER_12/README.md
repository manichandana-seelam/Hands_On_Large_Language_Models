              CHAPTER-12 = FINE TUNING GENERATION MODELS

1. Fine-Tuning Generative Models

Fine-tuning means adapting a pretrained LLM for a specific task or behavior. It helps the model give more useful and suitable responses. The chapter mainly discusses SFT and preference tuning.

2. Three Steps of LLM Training

LLM training has three main steps: pretraining, supervised fine-tuning, and preference tuning. Pretraining teaches the model language, SFT teaches it to follow instructions, and preference tuning improves its responses based on preferences.

3. Supervised Fine-Tuning (SFT)

SFT teaches a pretrained model to follow user instructions. It uses examples containing questions or instructions with their answers. The model learns to generate appropriate responses instead of simply continuing the input.

4. Full Fine-Tuning

Full fine-tuning updates all the parameters of the model using task-specific data. It can provide good results but requires high memory, computing power, and storage. Therefore, it can be expensive for large LLMs.

5. Parameter-Efficient Fine-Tuning (PEFT)

PEFT trains only a small part of the model while keeping most original weights unchanged. It reduces memory usage, training time, and storage requirements. LoRA is one of the most commonly used PEFT methods.

6. Adapters

Adapters are small components added inside Transformer layers for fine-tuning. Only these components are trained while the main model remains unchanged. Different adapters can be used for different tasks.

7. LoRA

LoRA stands for Low-Rank Adaptation and makes fine-tuning more efficient. Instead of changing all model weights, it trains small low-rank matrices. This reduces the number of trainable parameters and saves memory.

8. LoRA Parameters

The r parameter controls the size of the LoRA matrices. lora_alpha controls the strength of the LoRA updates, while target_modules selects the layers to modify. lora_dropout helps reduce overfitting during training.

9. Quantization

Quantization reduces the number of bits used to store model weights. This makes the model smaller and reduces GPU memory usage. It is useful for training and running large models on limited hardware.

10. QLoRA

QLoRA combines 4-bit quantization with LoRA for efficient fine-tuning. The original model is stored in low precision while LoRA adapters are trained. This allows models to be fine-tuned using much less GPU memory.

11. Instruction Data and Chat Templates

Instruction data contains user instructions and corresponding model responses. Chat templates organize these messages using roles such as user and assistant. This helps the model learn the correct conversational format.

12. UltraChat Dataset

UltraChat is a large dataset containing conversations between users and language models. A smaller portion can be selected to reduce training time. The conversations are formatted using the model's chat template before training.

13. SFT Training with QLoRA

In QLoRA-based SFT, the model is first loaded using 4-bit quantization. LoRA adapters are added to selected model layers. The SFT trainer then trains these adapters using instruction-based data.

14. Merging LoRA Weights

After training, the LoRA adapter can be merged with the original model. The merge_and_unload() function combines the adapter weights with the base model. The merged model can then be used for text generation.

15. Evaluating Generative Models

Evaluating LLMs is difficult because they can perform many different tasks. No single metric can completely measure the quality of a generative model. Evaluation should therefore match the model's intended use.

16. Word-Level Metrics

Perplexity, BLEU, ROUGE, and BERTScore are common metrics for evaluating generated text. They measure prediction quality or similarity with reference answers. However, they cannot fully measure correctness, creativity, or usefulness.

17. Benchmarks

Benchmarks are standard tests used to measure different LLM abilities. Examples include MMLU, GLUE, GSM8K, TruthfulQA, HellaSwag, and HumanEval. They test areas such as language understanding, reasoning, math, and coding.

18. Leaderboards

Leaderboards compare models using results from several benchmarks. They provide an easy way to understand the performance of different models. However, a high leaderboard position does not always mean the model is best for a specific task.

19. Automated Evaluation

Automated evaluation can use another LLM to judge the quality of generated answers. This method is called LLM-as-a-judge. It can compare different answers and decide which one is better.

20. Human Evaluation

Human evaluation allows people to directly judge the quality of model responses. Humans can check correctness, usefulness, clarity, and overall quality. It is often considered the most reliable method for real-world evaluation.

21. Preference Tuning

Preference tuning teaches a model which responses are better or more desirable. Preferred answers are encouraged while unwanted answers are discouraged. This helps align the model's behavior with human preferences.

22. Reward Models

A reward model gives a score to a generated response based on its quality. It is trained using preferred and rejected responses. The reward model learns to give higher scores to better answers.

23. RLHF and PPO

RLHF uses human preferences to improve the behavior of an LLM. A reward model evaluates the generated answers and provides rewards. PPO uses these rewards for training but can be complex and expensive.

24. Direct Preference Optimization (DPO)

DPO is an alternative to PPO that does not require a separate reward model. It directly learns from chosen and rejected responses. It makes the model more likely to produce preferred answers.

25. DPO Dataset

A DPO dataset contains a prompt, a chosen response, and a rejected response. Poor or tied examples can be removed before training. The remaining examples are formatted for DPO training.

26. DPO Training with QLoRA

For DPO training, the model can be loaded using 4-bit quantization to reduce memory usage. LoRA adapters are added and trained using preference data. The trained DPO adapter is then saved for later use.

27. SFT + DPO

SFT first teaches the model to follow instructions and respond like a chatbot. DPO then teaches the model which responses are preferred. Together, SFT and DPO can improve both instruction following and response quality.

28. ORPO

ORPO combines supervised fine-tuning and preference optimization into one training process. It removes the need for two separate training stages. This can make the fine-tuning process simpler and more efficient.

Overall Chapter Summary

Chapter 12 explains how to improve pretrained LLMs using SFT, LoRA, QLoRA, and DPO. SFT teaches the model to follow instructions, while DPO improves its responses based on preferences. LoRA and QLoRA make training faster and use less memory. Finally, different evaluation methods help us check the quality of the fine-tuned model.