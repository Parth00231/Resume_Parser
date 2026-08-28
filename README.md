# AI Resume Parser & Candidate Screening Tool 🚀

An intelligent, AI-powered HR assistant tool built with Python, Groq (Llama 3.3 70B), and Pydantic. It automatically parses resumes in PDF and Word (DOCX) formats, extracts structured candidate information, compares candidate profiles against a target job description, and ranks candidates based on match percentage.

---

## 🌟 Features

- **📄 Multi-Format Resume Parsing**: Supports extraction of raw text from both `.pdf` (via `pypdf`) and `.docx` (via `python-docx`) files.
- **🎯 Structured Extraction via Pydantic**: Guarantees structured JSON output matching predefined schemas for both Job Descriptions (`Jobd`) and Resumes (`Resume`).
- **🤖 Groq Llama-3.3-70b Powered**: Leverages the high-performance `llama-3.3-70b-versatile` model for accurate skill identification, experience calculation, and resume comprehension.
- **📊 Match Scoring & Analysis**: Generates comprehensive evaluation reports for each candidate including:
  - Overall match score percentage (0 - 100%)
  - Matching vs. missing critical skills
  - Experience requirement verification
  - Concise HR verdict
- **🏆 Automatic Ranking**: Ranks all processed candidates from best match to lowest match, displaying top candidates and candidate breakdown.

---

## 🛠️ Tech Stack & Dependencies

- **Language**: Python `>= 3.14`
- **LLM Provider**: [Groq API](https://groq.com/) (`llama-3.3-70b-versatile`)
- **Data Validation & Schemas**: `pydantic >= 2.13`
- **Document Parsing**: `pypdf`, `python-docx`
- **Environment Management**: `python-dotenv`
- **Package Manager**: `uv` (or `pip`)

---

## 📂 Project Structure

```text
Mini_project1/
├── Resumes/                      # Directory containing candidate resumes (.pdf / .docx)
│   ├── candidate_1.pdf
│   └── candidate_2.docx
├── .env.example                  # Template for environment variables
├── .env                          # Local environment variables (Git ignored)
├── .gitignore                    # Git ignore configuration
├── pyproject.toml                # Project metadata & dependencies
├── resume_parser.py              # Main script for parsing, scoring, and candidate ranking
└── README.md                     # Project documentation
```

---

## 🚀 Getting Started

### 1. Prerequisites

- Python 3.14 or later.
- A **Groq API Key** (Get one at [console.groq.com](https://console.groq.com)).

### 2. Installation

1. Navigate to the project directory:
   ```bash
   cd Mini_project1
   ```

2. Sync dependencies using `uv` (recommended):
   ```bash
   uv sync
   ```
   *Alternatively, using standard `pip`:*
   ```bash
   pip install groq pydantic pypdf python-docx python-dotenv
   ```

### 3. Environment Setup

Create a `.env` file from the provided template:

```bash
cp .env.example .env
```

Open `.env` and add your Groq API key:

```env
GROQ_API_KEY=gsk_your_actual_groq_api_key_here
```

---

## 💻 Usage

1. Place candidate resumes (`.pdf` or `.docx`) inside the `Resumes/` folder.
2. Run the resume parser script:

```bash
python resume_parser.py
```

### Script Execution Flow

1. **Job Description Extraction**: Parses target job criteria (e.g. required skills, experience, responsibilities).
2. **Resume Iteration**: Processes each resume in `Resumes/`, extracting candidate information into structured JSON.
3. **Evaluation**: Compares each parsed resume against the job description using Groq LLM.
4. **Output & Ranking**: Prints candidate match scores and detailed evaluation summaries, highlighting the **Top Candidates** and **Lowest Candidates**.

---

## 📋 Example Output

```text
Processing: candidate_1.pdf
Score: 85.0

Processing: candidate_2.docx
Score: 60.0

TOP 2 CANDIDATES


John Doe - 85.0 %
{'matching_skills': ['Python', 'AWS', 'Microservices'], 'missing_skills': ['Go'], 'verdict': 'Strong fit with relevant cloud and backend experience.'}


LOWEST 2 CANDIDATES


Jane Smith - 60.0 %
{'matching_skills': ['Python'], 'missing_skills': ['AWS', 'Distributed Systems'], 'verdict': 'Lacks required cloud and distributed systems background.'}
```
