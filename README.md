## 📄 Document Analysis using LLMs

### 🎯 Project Goal
The goal of this project was to build an automated **document analysis pipeline using Large Language Models (LLMs)** that can process long documents and extract meaningful insights. Specifically, the system was designed to:

- Extract text from a PDF document  
- Generate a concise summary of the document  
- Break the document into manageable passages  
- Automatically generate questions from the document content  
- Answer those questions using a question-answering model  

This helps convert large, unstructured documents into **structured knowledge** that is easier to understand and analyze.

---

### ⚙️ Approach

The project was implemented using **Python and transformer-based NLP models from Hugging Face**.

1. **Text Extraction**
   - Used `pdfplumber` to extract text from the Google Terms of Service PDF.
   - The extracted text was stored in a `.txt` file for further processing.

2. **Document Summarization**
   - Applied the `t5-small` transformer model to generate a high-level summary.
   - The model condensed the first **1000 characters of the document into a ~150-token summary**, capturing the main themes.

3. **Text Segmentation**
   - Used `NLTK` sentence tokenization to split the document into sentences.
   - Sentences were grouped into passages of **approximately 200 words each** to make them suitable for transformer models.

4. **Question Generation**
   - Used the `valhalla/t5-base-qg-hl` model to automatically generate questions from each passage.
   - A custom function ensured that **at least 3 questions were generated per passage**.

5. **Question Answering**
   - Used the `deepset/roberta-base-squad2` model to extract answers from the passages.
   - The system tracked unique questions to avoid duplicates and improve efficiency.

---

### 📊 Results

The pipeline successfully transformed a long legal document into structured information:

- Extracted text from a **multi-page PDF document**
- Generated a **concise summary (~150 tokens)** of the document
- Split the document into **multiple passages (~200 words each)**
- Automatically generated **3+ questions per passage**
- Used a QA model to produce **context-aware answers for each question**

Overall, the system demonstrates how **LLMs can automate document understanding**, making it easier to analyze complex documents such as legal terms, research papers, or policy documents.

---

### 💡 Key Outcome

This project showcases how **modern NLP techniques and transformer models** can be combined to build an **end-to-end intelligent document analysis system** capable of summarizing content, generating questions, and extracting answers automatically.
