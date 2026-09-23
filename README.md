# Researchmind
🔬 ResearchMind — Multi-Agent AI Research System

ResearchMind is an AI-powered research assistant built with Streamlit, LangChain, Google Gemini, DDGS web search, and BeautifulSoup.

It takes a research topic from the user, searches the web for relevant information, extracts useful content, generates a structured research report, and finally reviews the report with an AI critic.

✨ Features

🔎 Web Search — Finds recent and relevant sources using DDGS.

📄 Web Scraping — Extracts readable content from selected web pages.

✍️ AI Report Generation — Uses Google Gemini to generate a detailed research report.

🧐 AI Critic — Reviews the generated report and provides a score, strengths, and areas for improvement.

📥 Report Download — Download the final research report as a Markdown file.

⚡ Optimized API Usage — Search and scraping do not consume Gemini requests; Gemini is mainly used for the Writer and Critic stages.

🛡️ Error Handling — Handles temporary API errors, quota limits, and request failures with user-friendly messages.

🎨 Modern Streamlit UI — Responsive dark interface with pipeline status cards and result panels.

🧠 How It Works

User enters research topic
          │
          ▼
┌─────────────────────┐
│   Search Agent      │
│   DDGS Web Search   │
└─────────┬───────────┘
          │
          ▼
┌─────────────────────┐
│   Reader Agent      │
│   Web Scraping      │
└─────────┬───────────┘
          │
          ▼
┌─────────────────────┐
│   Writer Chain      │
│   Gemini AI         │
└─────────┬───────────┘
          │
          ▼
┌─────────────────────┐
│   Critic Chain      │
│   Gemini AI         │
└─────────┬───────────┘
          │
          ▼
   Final Research Report

🛠️ Tech Stack

Technology

Purpose

Python

Core programming language

Streamlit

Web application interface

LangChain

AI pipeline and prompt orchestration

Google Gemini

Report writing and critique

DDGS

Web search

BeautifulSoup

Web page content extraction

Requests

HTTP requests

python-dotenv

Environment variable management

📁 Project Structure

Researchmind/
│
├── app.py
├── agents.py
├── tools.py
├── pipeline.py
├── requirements.txt
├── .gitignore
├── README.md
└── .env              # Local only — never commit this file

Main Files

app.py — Streamlit UI, pipeline execution, results display, downloads, and error handling.

agents.py — Search/reader logic, Gemini model configuration, writer chain, and critic chain.

tools.py — DDGS search and web scraping utilities.

pipeline.py — Command-line pipeline version.

requirements.txt — Python dependencies.

🚀 Local Installation

1. Clone the repository

git clone https://github.com/karam4696/Researchmind.git
cd Researchmind

2. Create a virtual environment

Windows

python -m venv venv
venv\Scripts\Activate.ps1

macOS / Linux

python3 -m venv venv
source venv/bin/activate

3. Install dependencies

pip install -r requirements.txt

4. Create a .env file

Create a file named:

.env

Add your Gemini API key:

GEMINI_API_KEY=your_gemini_api_key
GOOGLE_API_KEY=your_gemini_api_key

Never upload your .env file or API keys to GitHub.

5. Run the application

python -m streamlit run app.py

Then open:

http://localhost:8501

🔑 Getting a Gemini API Key

Create a Gemini API key from Google AI Studio and add it to your .env file.

The application currently uses a Gemini Flash-Lite model configuration to reduce API usage while keeping report generation fast and practical.

☁️ Deploying on Streamlit Community Cloud

Push the project to GitHub.

Open Streamlit Community Cloud.

Create a new app.

Select this GitHub repository.

Set the main file path to:

app.py

Add the following secrets in the Streamlit app settings:

GOOGLE_API_KEY="your_gemini_api_key"
GEMINI_API_KEY="your_gemini_api_key"

Deploy the application.

🔐 Security

The .gitignore file should contain:

.env
__pycache__/
venv/

Never commit:

Gemini API keys

.env

private credentials

service-account credentials

If an API key is accidentally committed, revoke it immediately and create a new one.

⚙️ API Usage Optimization

ResearchMind is designed to minimize Gemini API consumption.

The current optimized flow uses Gemini mainly for:

Writer Chain  → 1 AI request
Critic Chain  → 1 AI request

Search and scraping are performed without Gemini, so a normal successful report typically requires far fewer AI requests than a fully agentic search pipeline.

Actual API usage may vary because of retries, failures, provider limits, and model behavior.

🧪 Example Research Topics

Try topics such as:

Artificial Intelligence in Healthcare

Quantum Computing Breakthroughs

CRISPR Gene Editing

Future of Fusion Energy

Impact of Generative AI on Education

📊 Report Output

A generated report contains:

Introduction

Key Findings

Conclusion

Sources

Critic Score

Strengths

Areas to Improve

One-line Verdict

The final report can also be downloaded as a .md file.

⚠️ Limitations

Free Gemini API tiers have request and quota limits.

Some websites may block automated scraping.

Search results depend on publicly available web content.

AI-generated reports should be verified before academic or professional use.

Temporary provider errors may occur during periods of high demand.

🔮 Future Improvements

Possible future upgrades:

Multiple-source scraping instead of a single primary source

PDF export

Research history

User authentication

Citation validation

Source credibility scoring

Database integration

Admin dashboard

Multiple AI model fallback

Daily API usage tracking
