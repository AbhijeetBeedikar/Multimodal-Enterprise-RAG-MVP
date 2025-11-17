
📌 Multimodal Enterprise RAG System

A complete Retrieval-Augmented Generation (RAG) pipeline capable of ingesting PDF, images, audio, building a Knowledge Graph, indexing multimodal content into Qdrant, and answering complex queries using a hybrid retrieval pipeline.

This project includes:

✔ Multimodal ingestion (PDF, images, audio)
✔ Vector indexing using Qdrant
✔ Knowledge graph extraction using Gemini
✔ Graph search + vector search hybrid retrieval
✔ Orchestrator for final prompting
✔ LLM answering
✔ Optional DeepEval evaluation

🗂 Project Structure
multimodal_enterprise_rag/
│
├── rag_system/
│   ├── ingestion/
│   ├── vector_db/
│   ├── graph/
│   ├── retrieval/
│   ├── main.py
│   └── env.py
│
├── setup.py
├── requirements.txt
└── README.md

🚀 Running the Project

There are two ways to run this project.

✅ Option 1 — Run Using the Colab Notebook

This is the easiest way.

Steps

Open the provided Colab notebook:
Enterprise_RAG.ipynb

Ensure your directory structure is:

/content/drive/MyDrive/AI_Projects/multimodal_enterprise_rag

or change it accordingly so that the root directory is equivalent to this


Inside rag_system/env.py, update your Google API key:

def key():
    return "YOUR_GEMINI_API_KEY"


Run all cells in order.

The main function to test your system is:

user_input(media_path, query)


Example:

user_input(
    "/content/drive/MyDrive/AI_Projects/multimodal_enterprise_rag/rag_system/ingestion/data/sample.pdf",
    "Summarize the document"
)

✅ Option 2 — Install and Run the Package Manually
Step 1: Install your project as a package

Run this from the project root:

import os
os.chdir("/root")
!pip install -e .


This installs the rag_system module.

Step 2: Ensure Python can import the package
import os
import sys

os.chdir("/root")
sys.path.append("/root")

Step 3: Run the main RAG pipeline
import importlib
import rag_system.main as main

importlib.reload(main)

main.user_input(media_path, query)


Example:

main.user_input("/root/rag_system/ingestion/data/image.png", "What does this image contain?")

📥 Usage

Use the main entry point:

user_input(media_path, query)


Example queries:

"Extract all entities from this PDF"

"Who founded the company described in the image?"

"Summarize the audio file"

"What does the graph say about Acme Corp?"

🧪 DeepEval Evaluation (Optional)

To evaluate your RAG system:

from deepeval import evaluate
from deepeval.metrics import FaithfulnessMetric
from deepeval.models.gemini import GeminiModel

metric = FaithfulnessMetric(model=GeminiModel())
score = metric.measure(prediction="your system output", context=["context docs"])

print(score)

🔑 API Keys

Make sure you update:

rag_system/env.py


With your:

Google Gemini API key

def key():
    return "YOUR_REAL_GEMINI_KEY"

📌 Notes

Qdrant must not be opened by multiple clients simultaneously.

If using Colab, keep your Qdrant data folder inside /content, not Google Drive, to avoid locking issues.

main.py handles:
✔ ingestion
✔ vector indexing
✔ graph building
✔ hybrid search
✔ prompt construction
✔ final LLM answer

🎯 Final Output

Running:

user_input(media_path, query)


Triggers the entire RAG backend, including:

Ingestion

Embedding + Vector Indexing

Knowledge Graph Extraction

Hybrid Search (Graph + Vector + Keywords)

Prompt Construction

LLM Response



