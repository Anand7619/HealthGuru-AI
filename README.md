# 🧠 HealthGuru AI

**HealthGuru** is a **multimodal AI health assistant** that leverages **LLMs**, **Retrieval-Augmented Generation (RAG)**, and **agentic orchestration** using **LangGraph** to provide intelligent, contextual, and personalized health-related assistance. It supports text, voice, and image-based queries, ensuring interactive and inclusive health access.

---

## 🔍 Key Features

- 💬 **Conversational AI Chatbot** powered by Large Language Models (LLMs)
- 🔎 **Retrieval-Augmented Generation (RAG)** with Pinecone for accurate medical information retrieval
- 🎙️ **Multimodal Input Support**: Accepts text, voice and image (via LLaMA-4 Scout)
- 🧠 **LangGraph Agents** for routing, query refinement, reasoning, and response generation
- 🌐 **Trusted Medical Sources**: Mayo Clinic, MedlinePlus, PubMed, NIH, NIMH, Healthline, and more
- 🌱 **Polite and Context-Aware Interactions** with few-shot and Chain-of-Thought prompting
- 🧾 **Web-Based Interface** for accessible user interaction

---

## 🏗️ System Architecture

HealthGuru is composed of the following core components:

1. **Multimodal Input Handler**  
   - Converts voice to text using Google Speech API  
   - Extracts context from images using LLaMA-4 Scout model
   - Accepts plain text queries and images directly 

2. **Knowledge Base**  
   - Vectorized embeddings of pre-processed medical content  
   - Semantic search via **Pinecone**
   - Websearch if Fallback to avoid hallucination via tavilysearch

3. **LangGraph Agent Framework**  
   - Agents include: Router, Retrieval Agent, Query Refiner, Generator, WebSearch Agent, Off-topic Handler, Greeting Agent

4. **LLM-Based Reasoning & Generation**  
   - Core LLM: **Gemini 2.0 Flash**  
   - Reasoning with Chain-of-Thought and few-shot prompting  
   - Fallbacks via **Tavily Web Search API** for low-confidence queries

---

## 📚 Dataset

The system uses curated data from:

- Mayo Clinic, MedlinePlus, PubMed, NIH, NIMH, Healthline
- MedQuAD Q&A Pairs
- Wikipedia (for general context)
- Medical PDFs, research articles, and HTML content

All data is cleaned, semantically chunked, tagged using NER, and embedded with `sentence-transformers/all-MiniLM-L6-v2`.

---

## ⚙️ Setup Instructions

### TechStack

- Python,Flask
- Pinecone API key
- Gemini API llm models
- Groq API key for the LLaMA-4 Scout model
- Tavily API key for WebSearch fallback
- LangChain and LangGraph

### Steps

1. **Clone the Repository**
   ```bash
   git clone https://github.com/your-username/healthguru.git
   cd healthguru
2. **Create .env file in root:**
   GOOGLE_API_KEY=your gemini api key
   PINECONE_API_KEY=your pinecone api key
   GROQ_API_KEY=your groq api key
   TAVILY_API_KEY="your tavily search api key"
   index_name="your pinecone index name"
   model="gemini-2.0-flash"

   ```bash
   run app.py
