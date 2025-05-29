# SmartFin Analyzer

![Python](https://img.shields.io/badge/Python-3.11+-blue.svg)
![Flask](https://img.shields.io/badge/Flask-2.x-black.svg)

SmartFin Analyzer is a web application designed to help users quickly analyze and understand complex financial documents. By leveraging Large Language Models (LLMs), this tool automates the extraction and summarization of key information from PDF reports, such as annual 10-K filings.

The application provides a three-part automated analysis upon upload and allows for interactive, conversational Q&A using both the document's content and real-time web search capabilities.

---

## Features

* **PDF Document Upload:** Securely upload financial documents for analysis.
* **Automated Three-Part Analysis:** Upon upload, instantly receive a summary of the:
    * Business Overview
    * Key Financial Metrics (formatted in a structured table)
    * Key Business Risks
* **Interactive Q&A:** An intelligent search agent allows you to ask follow-up questions.
* **Hybrid Search:** The agent can retrieve information directly from the uploaded document or perform a real-time web search (using Tavily AI) to answer questions that require external data.
* **User-Friendly Interface:** Clean, intuitive UI with real-time feedback on file selection and processing status.

---

## Live Demo & Screenshot

**You can find a live demo of the application here:**

[SmartFin Analyzer](https://mini-finance-analyst.onrender.com/)

---

## Technology Stack

* **Backend:** Python, Flask, Gunicorn
* **AI & Orchestration:** LangChain, OpenAI GPT-4o
* **Data Processing:** PyPDFLoader (for PDFs), ChromaDB (for vector storage)
* **Web Search:** Tavily AI Search API
* **Frontend:** HTML, CSS, JavaScript (for UI feedback)
* **Deployment:** Render, Git

---

## Setup and Local Installation

To run this project on your local machine, follow these steps:

1.  **Clone the Repository:**
    ```bash
    git clone https://github.com/mateenkq/smartfin-analyzer.git
    cd SMARTFIN_ANALYZER
    ```

2.  **Create and Activate a Virtual Environment:**
    * **Windows:**
        ```powershell
        py -m venv venv
        venv\Scripts\activate
        ```
    * **macOS / Linux:**
        ```bash
        python3 -m venv venv
        source venv/bin/activate
        ```

3.  **Install Dependencies:**
    ```bash
    pip install -r requirements.txt
    ```

4.  **Set Up Environment Variables:**
    * Create a file named `.env` in the root of the project folder.
    * Add your secret API keys to this file:
        ```
        OPENAI_API_KEY="sk-..."
        TAVILY_API_KEY="tvly-..."
        ```

5.  **Run the Application:**
    ```bash
    flask run
    ```
    The application will be available at `http://127.0.0.1:5000`.

---

## Deployment

This application is designed for deployment on a Platform-as-a-Service like [Render](https://render.com/).

The key deployment steps are:
1.  Push the code to a GitHub repository.
2.  Create a new "Web Service" on Render, linking it to the GitHub repo.
3.  Set the **Build Command** to `pip install -r requirements.txt`.
4.  Set the **Start Command** to `gunicorn app:app`.
5.  Add your `OPENAI_API_KEY` and `TAVILY_API_KEY` as **Environment Variables** in the Render dashboard.
6.  Create a **Persistent Disk** and set the **Mount Path** to `/uploads` to handle file storage.
