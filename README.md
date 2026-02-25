# 📄 Information Retrieval System (RAG with Gemini + FAISS)

An interactive **PDF-based Question Answering system** built using:

- 🧠 Google Gemini (via `langchain-google-genai`)
- 🔎 FAISS vector database
- 🧩 LangChain Conversational Retrieval Chain
- 🌐 Streamlit frontend
- 📚 PyPDF2 for document parsing

Upload PDFs, ask questions, and get contextual answers powered by Retrieval-Augmented Generation (RAG).

---

## 🚀 Features

- Upload multiple PDF files
- Automatic text extraction
- Intelligent text chunking
- Vector embeddings using Gemini
- FAISS-based similarity search
- Conversational memory
- Clean Streamlit UI
- Context-aware follow-up questions

---

## 🏗️ Project Structure

```
Information-Retrieval-System/
│
├── src/
│   ├── __init__.py
│   └── utils.py
│
├── app.py
├── requirements.txt
├── .env
├── setup.py
├── README.md
└── experiments.ipynb
```

---

## ⚙️ Tech Stack

- LangChain
- Google Gemini (1.5 Flash)
- FAISS (CPU)
- Streamlit
- PyPDF2
- Python 3.9+

---

## 📦 Installation

### 1️⃣ Clone the repository

```bash
git clone https://github.com/yourusername/Information-Retrieval-System.git
cd Information-Retrieval-System
```

### 2️⃣ Create a virtual environment

```bash
python -m venv venv
source venv/bin/activate      # Mac/Linux
venv\Scripts\activate         # Windows
```

### 3️⃣ Install dependencies

```bash
pip install -r requirements.txt
```

---

## 🔐 Environment Setup

Create a `.env` file in the root directory:

```
GOOGLE_API_KEY=your_google_api_key_here
```

### Get a Google API key

1. Visit: https://makersuite.google.com/app/apikey  
2. Generate an API key  
3. Paste it into your `.env` file  

If the key is missing, the app raises:

```python
ValueError("GOOGLE_API_KEY not found")
```

---

## ▶️ Run the Application

```bash
streamlit run app.py
```

Open the browser link shown in the terminal (usually `http://localhost:8501`).

---

## 🧠 How It Works

### Step 1: PDF Upload
Users upload one or more PDFs via Streamlit.

### Step 2: Text Extraction
`PyPDF2` extracts raw text from each page.

### Step 3: Text Chunking

```python
RecursiveCharacterTextSplitter(
    chunk_size=1000,
    chunk_overlap=200
)
```

### Step 4: Embeddings

```python
GoogleGenerativeAIEmbeddings(
    model="models/text-embedding-004"
)
```

Each chunk is converted into a dense vector.

### Step 5: Vector Store

```python
FAISS.from_texts(text_chunks, embedding=embeddings)
```

### Step 6: Conversational Retrieval Chain

```python
ChatGoogleGenerativeAI(
    model="gemini-1.5-flash",
    temperature=0.3
)
```

Uses:
- ConversationBufferMemory
- ConversationalRetrievalChain

Enables:
- Context-aware answers
- Follow-up questions
- Chat memory retention

---

## 🖥️ User Flow

1. Upload PDFs  
2. Click **Submit**  
3. Wait for processing  
4. Ask a question  
5. Receive context-based answer  
6. Continue the conversation naturally  

---

## 🛠️ Customization

### Change Model

```python
model="gemini-1.5-flash"
```

Switch to:

```
gemini-1.5-pro
```

### Adjust Chunk Size

```python
chunk_size=1000
chunk_overlap=200
```

### Adjust Temperature

```python
temperature=0.3
```

- Lower → More factual  
- Higher → More creative  

---

## 📌 Use Cases

- Research paper Q&A  
- Company document assistant  
- Academic study tool  
- Legal document analysis  
- Technical documentation chatbot  

---

## ⚠️ Limitations

- Large PDFs increase processing time  
- FAISS index is in-memory only  
- No authentication system  
- No metadata filtering  
- No OCR support for scanned PDFs  

---

## 🧪 Example Questions

- "Summarize the main findings of the document."
- "Explain section 3 in simple terms."
- "What limitations are mentioned?"
- "What does the author conclude?"

---

## 🏁 Deployment Options

- Streamlit Cloud  
- Render  
- Railway  
- HuggingFace Spaces  
- Docker  

---

## 🧑‍💻 Author

IDOWU 
AI / ML Developer  

---

## 📜 License

This project is licensed under the MIT License.