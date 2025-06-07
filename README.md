#  Multimodal RAG Pipeline Using `unstructured`, LangChain, and Gemini Flash

##  Overview

This project demonstrates how to build a **Multimodal Retrieval-Augmented Generation (RAG)** pipeline that can intelligently process **unstructured documents** — including **text, tables, and images** — and answer user queries using **Gemini Flash LLM**.

We leverage the power of:
- `unstructured` library for parsing documents
- LangChain for chaining and chunking logic
- FAISS for fast vector search
- Gemini Flash for high-performance, token-efficient response generation

---

##  Architecture Summary

###  Data Flow:
1. **Raw Document (PDF/Image)**  
   → Processed using the `unstructured` library  
   → Extracts: **Text**, **Tables**, and **Images**

2. **Content Summarization and Metadata Attachment**
   - Text Summary + Raw Text
   - Table Summary + Original Table (HTML/Markdown)
   - Image Summary + Base64-encoded Image

3. **Chunking & Ingestion**
   - Chunked using LangChain's `RecursiveCharacterTextSplitter`
   - Embedded using `OpenAIEmbeddings`
   - Stored in FAISS vector database with full metadata

4. **Query Pipeline**
   - User query → converted to embedding
   - Most relevant chunks (across modalities) are retrieved

5. **LLM Inference**
   - Query + Prompt + Retrieved Context → passed to Gemini Flash
   - Generates a final grounded answer

---

##  What is OCR?

**OCR (Optical Character Recognition)** enables machines to extract text from images or scanned documents.

###  Why OCR Matters
- Converts images into searchable, analyzable content
- Enables LLMs to reason over scanned PDFs or photos
- Crucial for processing:
  - Invoices
  - Reports
  - Contracts
  - Scanned forms

###  Tools That Use OCR:
- `unstructured` (built-in)
- `pytesseract` (Google Tesseract bindings)
- AWS Textract, Azure Form Recognizer, Google Vision API

---

##  Tech Stack

| Component     | Tool/Library                          |
|---------------|----------------------------------------|
| Document Parser | `unstructured`                      |
| Chunking       | LangChain Text Splitters             |
| Embeddings     | OpenAI Embeddings                    |
| Vector DB      | FAISS                                |
| LLM            | Gemini Flash                         |
| Image Handling | Base64 Encoding + OCR                |

---

## 💡 Use Cases

- Invoice and financial document summarization
- Enterprise document search (legal, healthcare, contracts)
- Scanned document Q&A systems
- AI-powered document assistants

---




---



