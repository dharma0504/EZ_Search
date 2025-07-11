<p align="center">
  <img src="https://github.com/dharma0504/EZ_Search/blob/main/EZ.png" alt="HealthVault Banner" width="100%"/>
</p>


# EZ_Search – AI Web Search Agent for Interview Question Mining

EZ_Search is an AI-powered system that automates the process of collecting, curating, and presenting technical interview questions tailored to specific companies and job roles. It combines web scraping, structured workflows, and large language models (LLMs) to help job seekers and educators access high-quality question sets on demand.

## ✦ Features

- Generate DSA and HR/Behavioral questions based on a company name, role, and job description
- Cleanly formatted and structured questions in both human-readable and JSON formats
- Optional LLM-based filtering and validation using LLaMA 3.3 via Groq API
- Modern, user-friendly interface built with Streamlit
- FastAPI backend with structured REST endpoints
- Supports microservice-style local deployment

## ✦ Tech Stack

| Layer              | Tools / Libraries                                  |
|-------------------|----------------------------------------------------|
| Frontend          | Streamlit                                          |
| Backend API       | FastAPI, Uvicorn                                   |
| Processing Layer  | LangGraph, Langchain, Groq, Pydantic               |
| Web Scraping      | Requests, BeautifulSoup                            |
| LLM Integration   | langchain_groq, LLaMA 3.3-70B                       |
| Others            | python-dotenv, JSON, JSON Schema, Local venv       |

## ✦ System Overview

### Streamlit Frontend
- Takes input: company name, role, and job description
- Displays output under two tabs: DSA Questions and HR/Technical Questions
- Expandable question cards with metadata

### FastAPI Backend
- `/generate_dsa_questions`: Retrieves static DSA question list
- `/generate_interview_questions`: Accepts form input, invokes LangGraph pipeline, returns structured output

### LangGraph Processing
- Agents for scraping, formatting, filtering, validating
- Workflow:
  1. Scrape questions from known sources
  2. Format questions and serialize to JSON
  3. Filter using LLM based on user intent (optional)
  4. Validate and deduplicate output

## ✦ Local Setup

1. **Clone the repo**


git clone https://github.com/your-username/ez_search.git
cd ez_search

2. Create a virtual environment and install dependencies
python -m venv venv
source venv/bin/activate     # for Linux/Mac
venv\Scripts\activate.bat    # for Windows

pip install -r requirements.txt

3. Set up environment variables
   Create a .env file in the root directory and add your Groq API key:
   GROQ_API_KEY=your_api_key_here

4. Run the backend and frontend
uvicorn main:app --reload      # Runs FastAPI on port 7070
streamlit run app.py           # Runs Streamlit on port 8501


## ✦ Folder Structure:
```bash
ez_search/
├── app.py                   # Streamlit frontend
├── main.py                  # FastAPI backend
├── agents/                  # LangGraph processing agents
│   ├── __init__.py
│   ├── fetch_questions.py
│   ├── format_questions.py
│   ├── filter_questions.py
│   └── validate_output.py
├── static/                  # Sample JSON files
│   └── dsa.json
├── .env                     # Environment variables (excluded from version control)
├── requirements.txt         # Python dependencies
└── README.md                # Project documentation
```

