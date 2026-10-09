****Pdf_GPT****

This project/architecture focuses on answering user asked queries from an installed question bank.

**TECH USED -**

- Language: Python

- Libraries: pypdf, google-generativeai, faiss-cpu, numpy

- Generative Model: gemini-3.6-flash (chosen for spatial reasoning and agentic execution)

- Embedding Model: models/gemini-embedding-001




**KEY FEATURES -**

1. Advanced Document Chunking: Splits PDF text into larger 250-word chunks with a 50-word overlap, providing more complete context per chunk and avoiding infinite-loop bugs.

2. Secure API Key Handling: Reads the API key from environment variables or getpass instead of hardcoding, preventing key leakage when sharing the project..

3. Prompt-Injection Guard: Explicitly instructs the model to treat the PDF text as data and reference material only, ignoring any malicious instructions embedded within the document.

4. Similarity-Threshold Gate: Rejects off-topic questions (e.g., "who won IPL?") by evaluating the vector similarity score before making an API call to the LLM.



**WORKFLOW**

I have created 10 modules in the Jupyter Notebook for each step to reach the desired output for Pdf GPT.
Below covers all 10 modules explanation, from pdf loading and text chunking to faiss similarity search, answer generation, conversation memory, and the final response.

Here is the Workflow of my Project Immplementation :

                                          MODULE 01
                                      Environment & API
                 Import libraries -> Configure Gemini API securely -> Initialize models
                                              |
                                              |
                                          MODULE 02
                                          PDF Loader
                       Load one or many PDFs -> Extract text page by page
                                              |
                                              |
                                          MODULE 03
                                        Text Chunking
                              Split text into manageable chunks
                                Chunk size: 250 & Overlap: 50
                                              |
                                              |
                                           MODULE 04
                                       Embeddings & Index
         Convert chunks to vectors -> Build a FAISS index -> Prepare for fast retrieval   
                                              |
                                              |
                                           MODULE 05
                                     Similarity Retrieval
      Embed the user query -> Search FAISS for top-k matches -> Return relevant chunks
                                              |
                                              |
                                           MODULE 06
                                        Prompt Builder
    Combine instructions and retrieved context -> Set grounding and safety rules -> Unsupported: return a clear fallback
                                              |
                                              |
                                           MODULE 07
                                         Gemini Answer
     Send prompt and context to Gemini -> Generate a concise, grounded answer -> Avoid unsupported claims
                                              |
                                              |
                                           MODULE 08
                                    Conversation Memory
                                  Use recent chat history
                                Rewrite follow-up questions
                                 Create a standalone query
                                              |
                                              |
                                           MODULE 09
                                  Orchestration Pipeline
                            Coordinate retrieval and generation
                                Apply similarity threshold
                                Reject off-topic questions
                                              |
                                              |
                                           MODULE 10
                                      PDF Question Bank
                               Source: provided Q&A PDF folder
                             Current set: about 10–50 questions
                                    Indexed for retrieval


                               
                               




