# OmniRAG-n8n
A self-hosted, production-ready RAG system built on n8n that automates Google Drive document ingestion into Pinecone via Ollama, and delivers intelligent, context-aware answers through a Telegram AI Agent.


# 🤖 OmniRAG-n8n: Enterprise-Grade Local RAG System

A production-ready, self-hosted **Retrieval-Augmented Generation (RAG)** system built entirely using **n8n**. This workflow automates the entire lifecycle of a knowledge base: from dynamically ingesting documents out of Google Drive to serving intelligent context-aware responses via a Telegram AI Agent using open-source local LLMs. 🚀

![Project Demo](OmniRAG-n8n/blob/main/fotos/rag.gif)

---

## 🌟 Key Features

### 1. 📂 Base Knowledge Ingestion Pipeline
* **🔄 Dynamic Triggers:** Automatically kicks off when a new file is added to a specific Google Drive folder or via manual execution.
* **📄 Smart Document Processing:** Downloads and parses documents seamlessly.
* **🧠 Local Embeddings:** Generates vector embeddings locally using **Ollama Embeddings**.
* **⚡ Cloud Vector Storage:** Upserts knowledge vectors into **Pinecone Vector Store** for high-performance similarity search.

### 2. 💬 Chatbot RAG System (Telegram Interface)
* **🤖 Telegram Integration:** Functions as an automated AI chatbot handling production webhooks.
* **⚙️ Advanced AI Agent:** Utilizes an n8n AI Agent node backed by an **Ollama Chat Model**.
* **🧠 Conversational Memory:** Equipped with `Simple Memory` to retain context across back-and-forth chat sessions.
* **🔍 Vector Store Tool:** Empowered with a specialized tool to query the Pinecone vector database on the fly, ensuring zero hallucinations and highly accurate answers based on your private data.

---

## 🏗️ Architecture & Workflow

Based on the system design, the architecture is split into two isolated, highly cohesive subsystems:



1. **The Ingestion Stage:** Watches your cloud storage, processes the text, chunks it, embeds it via Ollama, and indexes it into Pinecone. 📥
2. **The Retrieval Stage:** The Telegram trigger captures user queries, passes them to the AI Agent, which decides whether to fetch semantic context from Pinecone or reply directly using session memory. 📤

---

## 🛠️ Prerequisites & Tech Stack

* **🔗 n8n** (Self-hosted or Cloud instance)
* **🦙 Ollama** (Running locally with your preferred models, e.g., `llama3` or `mistral`, and an embedding model)
* **🌲 Pinecone Account** (API Key and Environment Index)
* **☁️ Google Cloud Console** (With Google Drive API enabled and credentials configured)
* **📱 Telegram Bot API Token** (Via `@BotFather`)

---

## 🚀 Setup Instructions

1. **📥 Import the Workflow:**
   * Download the `.json` file of this workflow.
   * Open your n8n instance, create a new workflow, and click on **Import from File** (or paste the JSON).

2. **🔑 Configure Credentials:**
   * Set up your **Google Drive OAuth2** credentials.
   * Add your **Pinecone API Key** and input your specific index name in the Pinecone node.
   * Connect your **Telegram Bot Token** to the Telegram nodes.
   * Ensure your **Ollama** base URL is properly mapped (e.g., `http://localhost:11434` or your local network IP).

3. **⚡ Deploy & Test:**
   * Drop a file into your Google Drive to test the Ingestion pipeline.
   * Toggle the workflow to **Active**.
   * Open your Telegram bot, type a question related to your documents, and watch the RAG system in action!

---

## 📝 License
This project is open-source and available under the MIT License.
