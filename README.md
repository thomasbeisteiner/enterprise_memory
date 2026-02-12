# Enterprise Memory
Internal AI knowledge assistant for companies to access project documentation and internal know-how, comparing LoRA fine-tuning and Retrieval-Augmented Generation (RAG)

## 🚀 Project Steps

### 1. Generating Test Project Data

At the start of the project, I created synthetic project data to serve as a test foundation without accessing any real company information. The generated data was designed to simulate a variety of projects and tasks, providing a realistic basis for the subsequent experiments.

### 2. Fine-Tuning a LLM (Qwen2.5-3B)

I knew from the beginning that fine-tuning wasn’t really the right approach for this project. Project data changes all the time, and it’s not practical to retrain the model every time something new comes up. I still ran some early experiments to see how a LLM would react to fine-tuning on own data. It quickly became clear that the model either made up information based on what it learned before, or, if trained longer, just repeated the text from the training data, which wasn’t useful for real questions. Since the approach wasn’t suitable anyway, I stopped the experiments.

### 3. Retrieval-Augmented Generation (RAG)

Instead of fine-tuning, I switched to Retrieval-Augmented Generation (RAG), a method that combines a LLM with a vector-based search. First, all project data is converted into vectors (embeddings) that capture the meaning of the text — words that have similar meanings end up closer to each other in this vector space.

When a question is asked, it’s also turned into a vector. The system then finds the most relevant documents by comparing these vectors — using Cosine Similarity to pick the ones that match the question most closely. These documents are used as the context for the LLM (in my case, Qwen2.5-3B), which then generates accurate, fact-based answers. The model doesn’t need to learn the information itself, so the answers stay reliable, consistent, and directly based on the project data.

### 4. Key Learnings

The project clearly showed that RAG works better than traditional fine-tuning for company-specific knowledge bases. Combining vector-based retrieval with a LLM gives a flexible and expandable system, where new project data can easily be added and used for answering questions as it comes in.