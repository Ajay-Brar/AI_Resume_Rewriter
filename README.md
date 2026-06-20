# Resume Bullet Point Rewriter & Benchmarker

## Overview
This project is a Jupyter Notebook tool designed to automatically rewrite and improve resume bullet points using Generative AI. It leverages **LangChain** to interface with various Large Language Models (LLMs), allowing users to transform raw, descriptive bullet points into professional, impactful, and metric-driven statements.

The repository currently contains two versions of the tool:
1.  **Version 1:** A multi-model benchmark using the Hugging Face Inference API.
2.  **Version 2:** A high-speed prototype using Llama-3.3 via Groq with advanced prompting strategies.

---

## Version 1: Multi-Model Benchmark (Hugging Face)

### Description
This version runs the same input through three distinct open-source models side-by-side to compare writing styles. It uses `HuggingFaceEndpoint` to access models without downloading weights locally.

### Models Tested
* **Zephyr (Mistral Base):** `HuggingFaceH4/zephyr-7b-beta`
* **Google (Gemma 2 9b):** `google/gemma-2-9b-it`
* **Alibaba (Qwen 2.5 7B):** `Qwen/Qwen2.5-7B-Instruct`

### Key Features
* **Benchmarking:** Aggregates outputs into a Pandas DataFrame for easy comparison.
* **Standardized Prompting:** Uses a single "Master Prompt" to enforce conciseness and action verbs across all models.

---

## Version 2: Resume Rewriting Prototype (Groq & Llama 3.3)

### Description
This version automates the rewriting of resume bullet points with a focus on speed and zero-cost inference. It implements specific prompting strategies to optimize output quality.

### Models & Tools Used
* **Model:** Llama-3.3-70b-versatile (via Groq API).
* **Framework:** LangChain (Python).
* **Reasoning:** Selected for its ability to handle complex instruction following while being free to use (Bonus Requirement).

### Prompting Strategies
We implemented three distinct strategies to compare output quality:
1.  **Role-Playing:** Simulates an HR Expert to ensure professional tone.
2.  **Direct Instruction:** Focuses strictly on constraints (Power Verbs, Keyword density).
3.  **Few-Shot Prompting:** Uses "Bad vs. Good" examples to guide the model by demonstration.

### Results & Best Performance
* **Observation:** The **Few-Shot** strategy generally performed best. By providing concrete examples of "Bad vs. Good" transformations, the model better understood how to inject metrics (e.g., "% increase") and maintain the correct length compared to the other methods.

### Challenges
* **Token Limits:** Ensuring the output stayed strictly within 12-20 words required careful tuning of the prompt constraints.
* **Context:** Some original bullets (like technical Power Query examples) were highly technical, making it difficult to shorten them without losing critical details.

---

## Installation & Setup

### Prerequisites
* Python 3.10+
* Jupyter Notebook
* API Keys for **Hugging Face** and **Groq**.

### Install Dependencies
```bash
pip install pandas langchain-huggingface langchain-groq huggingface_hub