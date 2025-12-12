# 🧠 AI-Powered Academic Research Assistant

An autonomous multi-agent system that automates the academic literature review process. This application uses a crew of specialized AI agents to search a private knowledge base, synthesize findings, analyze themes, and generate comprehensive research reports in minutes.

-----

## 🚀 Features

  * **Multi-Agent Workflow:** Orchestrates four specialized agents (Search, Summarizer, Analyst, Writer) using **LangGraph** and **CrewAI** to mimic a human research team.
  * **High-Speed Inference:** Powered by **Groq's** LPU inference engine running **Llama 3**, delivering near-instant reasoning and text generation.
  * **RAG Architecture:**
      * **Long-Term Memory:** Uses **Pinecone** to store and retrieve thousands of embedded document chunks from a curated PDF library.
      * **Session Memory:** Uses **FAISS** for an in-memory, temporary vector store to enable "Chat with Report" functionality.
  * **Interactive UI:** A clean **Streamlit** interface featuring persistent conversation history (stored in **SQLite**) and a dedicated sidebar for managing research sessions.
  * **Cost-Efficient:** Built entirely on free-tier compatible technologies (Groq Free Tier, Local HuggingFace Embeddings, Pinecone Starter).

-----

## 🛠️ Tech Stack

  * **Frontend:** Streamlit
  * **Orchestration:** LangGraph, CrewAI
  * **LLM Provider:** Groq (Model: `llama-3.3-70b-versatile`)
  * **Vector Database:** Pinecone (Persistent), FAISS (Ephemeral)
  * **Embeddings:** HuggingFace (`all-MiniLM-L6-v2`)
  * **Database:** SQLite (for chat history)
  * **Environment Management:** Python-dotenv

-----

## ⚙️ Architecture

The system follows a sequential graph workflow:

1.  **User Input:** The user provides a research topic.
2.  **Literature Search Agent:** Queries the Pinecone database for semantically relevant excerpts.
3.  **Paper Summarizer Agent:** Distills dense academic text into concise summaries.
4.  **Theme Analyst Agent:** Synthesizes summaries to identify cross-cutting themes and debates.
5.  **Report Writer Agent:** Compiles everything into a structured literature review.
6.  **RAG Chat:** The final report is indexed into FAISS, allowing the user to ask follow-up questions.

-----

## 📦 Installation

### 1\. Clone the Repository

```bash
git clone https://github.com/yourusername/ai-research-assistant.git
cd ai-research-assistant
```

### 2\. Create a Virtual Environment

```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

### 3\. Install Dependencies

```bash
pip install -r requirements.txt
```

### 4\. Set Up Environment Variables

Create a `.env` file in the root directory and add your API keys:

```env
GROQ_API_KEY="gsk_..."
PINECONE_API_KEY="pcsk_..."
```

-----

## 🖥️ Usage

### Running the Application

Execute the Streamlit app from your terminal:

```bash
streamlit run app.py
```

### How to Use

1.  **Start New Research:** Enter a topic (e.g., *"Impact of LLMs on Software Engineering"*) in the main input field and click **Start Research**.
2.  **View Report:** Wait for the agents to complete their tasks. The final report will appear in the main window.
3.  **Chat with Report:** After generation, use the chat input box at the bottom to ask specific questions about the generated content.
4.  **History:** Use the sidebar to view and load past research sessions.

-----

## 📂 Project Structure

```bash
├── app.py               # Main application logic & UI
├── database.py          # SQLite database helper functions
├── requirements.txt     # Python dependencies
├── .env                 # API keys (not shared)
└── data/                # Folder for PDF documents (if using ingestion script)
```

-----

## 🤝 Contributing

Contributions are welcome\! Please feel free to submit a Pull Request.

## 📄 License

This project is licensed under the MIT License.
