# AI Interview Coach — Powered by Google Gemini 2.5 Flash 🤖

[![Python](https://img.shields.io/badge/Python-3.10+-blue.svg)](https://www.python.org/)
[![Gemini](https://img.shields.io/badge/Model-Gemini--2.5--Flash-orange.svg)](https://ai.google.dev/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

A specialized tool built to demonstrate advanced **Prompt Engineering** and **LLM Orchestration**. This project focuses on transforming a standard Generative AI into a structured Technical Interviewer capable of providing parseable, data-driven feedback.

---

## 🌟 Project Highlights
This project was born out of a challenge: **Take the core principles of LLM development (originally taught for ChatGPT) and port them to the Google Gemini ecosystem.**

### Key Engineering Features:
* **Persona Engineering:** Utilizes `system_instruction` to anchor the model as a "Senior Technical Interviewer."
* **Stateful Conversations:** Implemented `start_chat(history=[])` to maintain context across multiple interview rounds.
* **Structured Output (JSON):** Forces the LLM to return a strict schema (`score`, `verdict`, `strengths`, `improve`) for easy integration into web applications.
* **Adaptability:** Successfully migrated logic from OpenAI-centric patterns to the Google Generative AI SDK.

---

## 📂 Project Structure

* [`gemini-notebook.ipynb`](gemini-notebook.ipynb): The core logic, experiments, and iterative prompt testing.
* [`gemini-notebook.html`](gemini-notebook.html): A static, read-only export for quick viewing in a browser.
* **Section 1-3:** Environment setup, Gemini connection, and Persona configuration.
* **Section 4-5:** Implementation of Chat Memory and the JSON Scoring Engine.

---

## 🛠️ Setup & Installation

### Prerequisites
- **Python 3.10+**
- A **Google AI Studio** API Key: [Get it here](https://aistudio.google.com/apikey)

### Installation
1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/Vaib4496/INTERVIEW-COACH-CHATBOT-PYTHON.git](https://github.com/Vaib4496/INTERVIEW-COACH-CHATBOT-PYTHON.git)
    cd INTERVIEW-COACH-CHATBOT-PYTHON
    ```
2.  **Install dependencies:**
    ```bash
    pip install google-generativeai python-dotenv
    ```
3.  **Create a `.env` file** in the root directory (do not commit this file):
    ```env
    GEMINI_API_KEY=your_actual_key_here
    ```

---

## 📊 Sample Output: The "Scorecard"
One of the primary goals was to move away from "chatty" AI and toward "data-driven" AI. The notebook produces a structured verdict like this:

```json
{
  "score": 7,
  "verdict": "Strong candidate for mid-senior role",
  "strengths": ["React hooks", "Performance optimization"],
  "improve": ["System design", "Testing strategies"]
}