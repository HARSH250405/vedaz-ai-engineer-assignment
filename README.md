Vedaz AI Engineer Assignment
Overview
This project was developed as part of the Vedaz AI Engineer technical assignment. It demonstrates an end-to-end pipeline for generating, validating, and evaluating AI-powered astrology conversations while enforcing safety guidelines.
The project consists of three main components:

Chat Checker – Validates chat structure, detects duplicates, measures chat length, splits data into training and testing sets, and identifies safety policy violations.
Chat Generator – Uses an LLM to generate new astrology conversations in the required JSON format and filters them using the chat checker.
Quality Evaluator – Evaluates AI-generated responses on safety, warmth, honesty, and helpfulness using an LLM-based grading pipeline.
Project Structure
.
├── src/
│   ├── checker.py
│   ├── generator.py
│   ├── evaluator.py
│   ├── safety.py
│   ├── llm.py
│   └── prompts.py
│
├── data/
│   ├── sample_chats.jsonl
│   ├── generated_chats.jsonl
│   ├── train.jsonl
│   └── test.jsonl
│
├── outputs/
│   ├── checker_report.json
│   ├── evaluation_results.csv
│   └── evaluation_summary.md
│
├── requirements.txt
├── .env.example
└── README.md


Installation
Clone the repository:
git clone <repository-url>
cd vedaz-ai-engineer-assignment


Install dependencies:
pip install -r requirements.txt


Create a .env file and add your API key:
TOGETHER_API_KEY=your_api_key_here


Running the Project
Task 1 – Chat Checker
python src/checker.py


Features:
Validates chat structure
Counts chat length
Detects duplicate and near-duplicate chats
Splits data into train and test sets
Flags unsafe conversations
Task 2 – Chat Generator
python src/generator.py


Features:
Generates conversations using an LLM
Validates JSON output
Runs every generated chat through the checker
Saves only safe conversations
Generated chats are stored in:
data/generated_chats.jsonl


Task 3 – Quality Evaluator
python src/evaluator.py


Features:
Evaluates responses to a test set of questions
Scores responses on:
Safety
Warmth
Honesty
Helpfulness
Exports results as CSV
Safety Detection
The safety checker uses a hybrid approach:
Rule-Based Detection
Detects unsafe content such as:
Death predictions
Illness predictions
Guaranteed financial outcomes
Guaranteed medical outcomes
Fear-based language
Pressure to purchase remedies
Manipulative or exploitative advice
LLM-Based Review
A second review is performed using an LLM to identify nuanced policy violations that keyword matching may miss.
Design Choices
Modular project structure for maintainability.
JSON validation before saving generated chats.
Automatic filtering of unsafe conversations.
Reusable LLM wrapper for generation and evaluation.
Deterministic train/test split for reproducibility.
Limitations
Keyword rules may miss subtle violations.
LLM safety evaluation may occasionally produce inconsistent judgments.
Token counting is approximate when a tokenizer is unavailable.
With more development time, I would:
Train a dedicated safety classifier.
Improve duplicate detection using embeddings.
Add automated unit tests.
Build a web interface for dataset inspection.
Expand evaluation metrics with factual consistency and response quality.
Deliverables
Chat Checker
Chat Generator
Quality Evaluator
Generated JSONL dataset
Checker report
Evaluation results
README
Requirements file
Author
Submitted as part of the Vedaz AI Engineer Technical Assignment.
