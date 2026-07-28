                     CHAPTER-5 - TEXT CLUSTERING AND TOPIC MODELLING


1. Using Text Generation Models

Text generation models (LLMs) generate human-like text based on the input prompt. They are used for tasks such as question answering, summarization, translation, content writing, and code generation. In this chapter, the book uses the open-source Phi-3 Mini model because it is lightweight, free, and can run on an 8 GB GPU.

2. Loading a Text Generation Model

A text generation model is loaded using the Transformers library with AutoModelForCausalLM, AutoTokenizer, and pipeline. The model generates text, the tokenizer converts text into tokens, and the pipeline simplifies the interaction by handling tokenization, prompt formatting, and text generation automatically.

3. Messages and Chat Templates

Instead of giving a plain prompt, chat models use a messages format with roles like user and assistant. The Transformers pipeline automatically converts these messages into the chat template (<|user|>, <|assistant|>) expected by the model. This is why we usually don't need to call apply_chat_template() ourselves.

4. Controlling Model Output

The generated output can be controlled using parameters like do_sample, temperature, and top_p. These parameters determine whether the model should produce deterministic or creative responses. Adjusting them allows us to balance accuracy and creativity depending on the task.

5. Temperature

Temperature controls the randomness of token selection. A low temperature makes the model choose highly probable tokens, producing consistent and focused responses. A high temperature allows lower-probability tokens to be selected, resulting in more creative and diverse outputs.

6. Top-p (Nucleus Sampling)

Top-p controls how many candidate tokens the model can choose from based on cumulative probability. A low top_p restricts the model to a small set of highly probable tokens, while a high top_p allows it to consider a wider range of tokens, increasing vocabulary variety and creativity.

7. Prompt Engineering

Prompt engineering is the process of designing prompts that guide the model toward the desired output. A clear and specific prompt usually produces better responses than a vague one. It is an iterative process where prompts are refined through experimentation to improve quality.

8. Basic Ingredients of a Prompt

A good prompt generally contains an instruction, the data related to the task, and sometimes an output indicator that tells the model how the answer should be formatted. These components help the model clearly understand both the task and the expected output.

9. Instruction-Based Prompting

Instruction-based prompting means directly telling the model what task to perform, such as summarizing, translating, classifying, or generating text. The instruction should be specific, concise, and placed clearly in the prompt to reduce ambiguity and improve output quality.

10. Components of a Complex Prompt

A complex prompt may include persona, instruction, context, format, audience, tone, and data. Each component provides additional guidance to the model, helping it generate responses that better match the user's expectations. These components can be added or removed depending on the use case.

11. In-Context Learning

In-context learning improves model performance by providing examples within the prompt. It includes zero-shot (no examples), one-shot (one example), and few-shot (multiple examples) prompting. By seeing examples, the model learns the expected pattern without changing its internal parameters.

12. Chain Prompting

Chain prompting solves complex problems by breaking them into smaller prompts. The output of one prompt becomes the input to the next prompt, creating a sequence of steps. This approach improves accuracy and makes it easier for the model to handle complicated tasks.

13. Reasoning with Generative Models

Reasoning techniques encourage LLMs to solve problems step by step instead of predicting the final answer immediately. Although LLMs mainly perform pattern matching rather than true reasoning, these techniques help them produce more logical and accurate responses.

14. Chain-of-Thought (CoT)

Chain-of-Thought prompting asks the model to explain its reasoning before giving the final answer. By generating intermediate reasoning steps, the model often performs better on mathematical, logical, and multi-step reasoning tasks. It can be implemented using examples or simply by adding phrases like "Let's think step-by-step."

15. Self-Consistency

Self-consistency improves reliability by asking the model the same question multiple times using sampling. Since each run may produce different reasoning paths, the final answer is selected using majority voting. This reduces randomness and increases the likelihood of obtaining the correct answer.

16. Tree-of-Thought (ToT)

Tree-of-Thought extends Chain-of-Thought by exploring multiple reasoning paths instead of just one. The model evaluates different intermediate solutions, keeps the promising ones, and discards weaker ones before reaching the final answer. This approach is useful for complex reasoning and creative problem-solving but requires more computation.

17. Output Verification

Before using an LLM's output in real-world applications, it should be verified for correctness, structure, ethics, and accuracy. Verification helps ensure that the output follows the required format, avoids hallucinations, and is safe for production use.

18. Providing Examples for Output

Few-shot prompting can also guide the structure of the output. By showing the model an example of the expected format, such as a JSON object, it is more likely to generate responses that follow the same structure. However, the model may still occasionally deviate from the format.

19. Grammar-Constrained Sampling

Grammar-constrained sampling restricts the tokens the model is allowed to generate, ensuring that the output follows predefined rules such as valid JSON or a limited set of labels. Libraries like llama-cpp-python, Guidance, and Guardrails implement these constraints to produce more reliable outputs.

20. GGUF Model Format

GGUF is a model file format used by llama-cpp-python for storing quantized and optimized language models. Unlike the Transformers library, which automatically selects the required files, llama-cpp requires the user to specify the exact GGUF file to load. This format is designed for efficient inference and lower memory usage.

21. Memory Management

When switching from one model to another, it is often necessary to free CPU and GPU memory by deleting the old model and clearing the cache. This prevents memory-related errors such as CUDA Out of Memory and allows the new model to load successfully. If sufficient memory is available, clearing is not required.

22. JSON Output Validation

When a model is instructed to generate JSON, its output should be validated before use. The function json.loads() checks whether the generated text is valid JSON and raises an error if it is not. After validation, json.dumps(..., indent=4) formats the JSON into a clean, readable structure without changing its content.