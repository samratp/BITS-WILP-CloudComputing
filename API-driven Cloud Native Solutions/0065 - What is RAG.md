**RAG** stands for **Retrieval-Augmented Generation**.

It is an AI technique that combines **retrieval of external knowledge** with **language model generation** to produce more accurate, relevant, and up-to-date responses.

---

### How RAG Works (Step-by-Step)

1. **Query Input**
   A user asks a question or gives a prompt.
   Example: *“What are the side effects of aspirin?”*

2. **Retrieval Step**
   Instead of relying only on the model’s pre-trained knowledge, RAG first retrieves relevant documents or passages from an external **knowledge base**, such as:

   * A vector database (e.g., FAISS, Pinecone, Weaviate)
   * A document store (e.g., PDFs, websites, internal docs)

3. **Augmentation**
   The retrieved text snippets are fed into the **language model** as **context** along with the original prompt.
   Example context:

   > “Aspirin may cause nausea, stomach pain, and bleeding.”

4. **Generation Step**
   The model uses both the prompt and the retrieved documents to generate a more accurate and grounded response.

---

### Why Use RAG?

| Benefit                               | Description                                                                  |
| ------------------------------------- | ---------------------------------------------------------------------------- |
| **Up-to-date answers**                | LLMs can’t natively know post-training events. RAG can retrieve recent data. |
| **Domain-specific knowledge**         | You can connect the model to private/internal documents.                     |
| **Fact grounding**                    | Reduces hallucinations by giving the model real source material.             |
| **Efficient fine-tuning alternative** | No need to retrain the model — just improve the retrieval layer.             |

---

### RAG Architecture Overview

```
               +---------------------+
               |  User Input Query   |
               +---------+-----------+
                         |
                         v
         +-------------------------------+
         |   Document Retrieval (Search) |
         |  (Vector DB, Index, etc.)     |
         +-------------------------------+
                         |
                         v
         +-------------------------------+
         | Retrieved Context (Snippets)  |
         +-------------------------------+
                         |
                         v
     +-------------------------------------------+
     | LLM (e.g., GPT, Claude)                   |
     | Receives: [Prompt + Retrieved Context]    |
     +-------------------------------------------+
                         |
                         v
               +---------------------+
               |  Final Response     |
               +---------------------+
```

---

### Example Use Cases

* **Enterprise QA bots** using internal documents
* **AI search assistants** for legal, medical, or financial info
* **Customer support agents** that consult your help center
* **Educational tutors** that access specific study material
