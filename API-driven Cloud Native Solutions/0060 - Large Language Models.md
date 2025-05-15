## **Large Language Models (LLMs)**

### **Definition**

Large Language Models (LLMs) are a class of **deep learning algorithms** designed to understand, generate, and manipulate human language. They are trained on **massive datasets**—including books, articles, and web pages—to learn the structure and semantics of language.

### **Key Capabilities**

LLMs can:

* **Recognize** patterns in text
* **Extract** meaning and information
* **Summarize** long documents
* **Predict** the next word or phrase
* **Generate** coherent and grammatically correct sentences

LLMs are used in tasks such as:

* Language translation
* Summarization
* Question answering
* Text completion and generation

---

## **Model Parameters**

### **What Are Parameters?**

In neural networks, **parameters** are the values (like weights and biases) that the model learns from data during training.

### **Why Are They Important in LLMs?**

* Parameters define how the model **interprets language**, detects patterns, and understands relationships between words.
* During training, parameters are **tuned** to reduce the difference between predicted and actual outputs (this is called minimizing the loss/error).
* More parameters typically mean the model can **capture more complex patterns**.

### **Example**

* **GPT-3** has **175 billion parameters**.
* This enables it to generate highly detailed and contextually accurate responses across a wide range of topics.

---

## **Tokens in LLMs**

### **What Are Tokens?**

Tokens are the **smallest pieces of text** that a language model processes. They can be:

* Whole words (e.g., "cat")
* Sub-words (e.g., "un", "believ", "able")
* Even characters or punctuation

### **Subword Tokenization**

Most modern LLMs use **subword tokenization** (like Byte-Pair Encoding or SentencePiece) to:

* Handle rare or unknown words more efficiently
* Improve performance in multilingual settings
* Avoid a massive vocabulary of full words

**Example**:

> “Unbelievable” → \["un", "believ", "able"]

---

## **Tokens and LLM Cost**

### **Why Do Tokens Matter?**

LLMs don’t process unlimited text—they have **token limits per request**. This includes both:

* The **input** (your prompt)
* The **output** (the model’s reply)

### **Impact on Cost**

* The **more tokens** used, the **higher the computational cost**.
* API-based models (like OpenAI's GPT) often charge **per token**.

**Example**:

> Prompt: “What is the capital of Australia?”
> Response: “The capital of Australia is Canberra.”

If each word is roughly a token, this uses about **12 tokens**.

---

## **Popular Large Language Models (LLMs)**

Here’s a list of some of the leading LLMs as of 2025:

| Model           | Organization                          | Notes                             |
| --------------- | ------------------------------------- | --------------------------------- |
| **GPT-4**       | OpenAI                                | Strong reasoning, widely used     |
| **Claude 3**    | Anthropic                             | Strong safety alignment           |
| **LLaMA 3**     | Meta                                  | Open-weight model, fast inference |
| **Mistral 7B**  | Mistral AI                            | Compact, fast, performant         |
| **PaLM 2**      | Google                                | Text-focused                      |
| **Gemini**      | Google                                | Multimodal (text, images, etc.)   |
| **Grok**        | xAI (Elon Musk)                       | Built into X (Twitter)            |
| **ERNIE 4.0**   | Baidu                                 | Designed for Chinese language     |
| **Falcon**      | Technology Innovation Institute (UAE) | Open-weight LLM                   |
| **DeepSeek R1** | DeepSeek AI                           | Open-source research LLM          |
