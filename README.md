# Pdf_GPT
This project/architecture focuses on answering user asked queries from an installed question bank.

**TECH USED -**
Language: Python
Libraries: pypdf, google-generativeai, faiss-cpu, numpy
Generative Model: gemini-3.6-flash (chosen for spatial reasoning and agentic execution)
Embedding Model: models/gemini-embedding-001

**KEY FEATURES -**
Advanced Document Chunking: Splits PDF text into larger 250-word chunks with a 50-word overlap, providing more complete context per chunk and avoiding infinite-loop bugs.
Secure API Key Handling: Reads the API key from environment variables or getpass instead of hardcoding, preventing key leakage when sharing the project..
Prompt-Injection Guard: Explicitly instructs the model to treat the PDF text as data and reference material only, ignoring any malicious instructions embedded within the document.
Similarity-Threshold Gate: Rejects off-topic questions (e.g., "who won IPL?") by evaluating the vector similarity score before making an API call to the LLM.
