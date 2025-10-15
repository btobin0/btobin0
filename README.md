# 🧠 Hall-Detect-RAG

**Hall-Detect-RAG** is an advanced chatbot and hallucination-detection pipeline that integrates Retrieval-Augmented Generation (RAG) with automated hallucination *detection*, *analysis*, and *visualization*.  
It enables researchers and developers to measure, mitigate, and visualize hallucinations in Large Language Model (LLM) responses using quantitative metrics and dashboards.

---

## 🚀 Project Overview

Hall-Detect-RAG is composed of three main components:

1. **`detect_and_mitigate.py`** – Wraps around the chatbot logic to **analyze hallucination risks** in generated answers.  
   - Checks each question–answer pair for hallucination probability, relevance, factual grounding, and confidence.  
   - Uses scoring metrics (e.g., similarity thresholds, entropy, F1-score) to quantify reliability.  
   - Optionally applies mitigation techniques such as prompt re-ranking or confidence-weighted regeneration.

2. **`ingest_and_index.py`** – Handles **data ingestion and vector indexing**.  
   - Loads source documents (text, PDFs, CSVs, etc.) and converts them into vector embeddings.  
   - Builds a local or remote index using frameworks such as **LlamaIndex**, **FAISS**, or **Chroma**.  
   - Enables efficient context retrieval for the chatbot.

3. **`hall-detect-Dash1.py`** – Generates **interactive dashboards** to visualize hallucinations.  
   - Displays hallucination scores, detection heatmaps, similarity matrices, and mitigation effectiveness over time.  
   - Built using **Plotly Dash** for live visual analytics.

---

## 🧩 Architecture

```
                ┌───────────────────────────────┐
                │         User Query            │
                └──────────────┬────────────────┘
                               │
                    ▼ (via Chatbot)
         ┌──────────────────────────────────────────┐
         │         detect_and_mitigate.py            │
         │  - RAG pipeline                           │
         │  - Hallucination analysis & scoring       │
         └──────────────┬────────────────────────────┘
                        │
                        ▼
         ┌──────────────────────────────────────────┐
         │        ingest_and_index.py                │
         │  - Document ingestion                     │
         │  - Vector embedding & search indexing     │
         └──────────────┬────────────────────────────┘
                        │
                        ▼
         ┌──────────────────────────────────────────┐
         │         hall-detect-Dash1.py              │
         │  - Dash/Plotly visualization dashboard    │
         │  - Displays hallucination trends          │
         └──────────────────────────────────────────┘
```

---

## 🛠️ Installation

```bash
# Clone the repository
git clone https://github.com/yourusername/hall-detect-rag.git
cd hall-detect-rag

# Create a virtual environment
python -m venv venv
source venv/bin/activate  # (Windows: venv\Scripts\activate)

# Install dependencies
pip install -r requirements.txt
```

---

## ⚙️ Usage

### 1. Ingest and Index Documents
```bash
python ingest_and_index.py
```
Loads your data into the vector index (FAISS, Chroma, etc.) for RAG-based retrieval.

### 2. Run the Chatbot with Detection
```bash
python detect_and_mitigate.py
```
Starts the RAG chatbot and applies hallucination detection to each Q/A pair.

### 3. Launch the Dashboard
```bash
python hall-detect-Dash1.py
```
Opens an interactive dashboard at `http://localhost:8050` displaying:
- Hallucination severity scores  
- Document grounding visualizations  
- Response consistency heatmaps  
- Confidence distributions  

---

## 📊 Example Output

| Question | Confidence | Hallucination Score | Mitigated |
|-----------|-------------|--------------------|------------|
| "Who is the CEO?" | 0.92 | 0.05 | ✅ |
| "When was the company founded?" | 0.68 | 0.32 | ⚠️ |
| "What are the company’s secret projects?" | 0.41 | 0.77 | ❌ |

---

## 🧪 Tech Stack

- **LLM Frameworks:** OpenAI, LlamaIndex, LangChain  
- **Vector Databases:** FAISS / Chroma  
- **Visualization:** Plotly Dash, Seaborn, Matplotlib  
- **Evaluation Metrics:** F1-score, Cosine Similarity, Entropy Divergence  
- **Data Formats:** TXT, PDF, CSV  

---

## 🧠 Research Use Cases

- Evaluate and benchmark LLM hallucination behavior  
- Quantify reliability of chatbot responses  
- Compare mitigation strategies across datasets  
- Generate reports for academic or enterprise safety studies  

---

## 📁 Repository Structure

```
hall-detect-rag/
├── detect_and_mitigate.py       # Chatbot with hallucination detection & mitigation
├── ingest_and_index.py          # Document ingestion and vector indexing
├── hall-detect-Dash1.py         # Visualization dashboard (Plotly Dash)
├── data/                        # Example input documents
├── results/                     # Logs, hallucination scores, metrics
├── requirements.txt             # Python dependencies
└── README.md                    # Project documentation
```

---

## 🧑‍💻 Contributing

Contributions are welcome!  
Please fork the repository, make your improvements, and submit a pull request.

---

## 📜 License

This project is released under the **MIT License**.  
See [LICENSE](LICENSE) for details.

---

## 🧩 Author

**Brian Tobin**  
Researcher in LLM Safety & Hallucination Detection  
📧 your-email@example.com
