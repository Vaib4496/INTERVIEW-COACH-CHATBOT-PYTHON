# Interview Coach — Gemini Notebook

A small learning notebook that uses **Google Gemini** to practice **prompt engineering** (inspired by ideas from the DeepLearning.AI short course): clearer prompts yield more useful interview questions, and structured outputs (JSON) keep scoring predictable.

Main file: [`gemini-notebook.ipynb`](gemini-notebook.ipynb).

## What’s inside

1. **Setup** — Install dependencies, load API key, configure the Gemini client.
2. **Principle 1: clear & specific instructions** — Compares a vague prompt (“give me an interview question”) with a tight, role-specific prompt (e.g. Senior React / performance).
3. **JSON scoring helper** — Asks the model for a strict JSON verdict (`score`, `verdict`, `strengths`, `improvements`) and parses the reply safely (handles empty text and markdown fences).

There is also a static export: [`gemini-notebook.html`](gemini-notebook.html) (read-only in the browser).

## Prerequisites

- **Python 3.10+** (your environment may show 3.14; use whatever kernel you run the notebook with).
- A **Google AI Studio** API key for Gemini: [https://aistudio.google.com/apikey](https://aistudio.google.com/apikey)

## Configuration

1. In the project folder, create a `.env` file (this repo should **not** commit real keys):

   ```env
   GEMINI_API_KEY=your_key_here
   ```

2. Ensure `.env` is listed in `.gitignore` if you use Git.

## Install & run

1. Open `gemini-notebook.ipynb` in Jupyter, VS Code, or Cursor.
2. Run the first **code** cell to install packages and connect:

   ```text
   google-generativeai
   python-dotenv
   ```

3. Run the **Principle 1** code cell to see vague vs specific prompts.

### Scoring cell (`chat`)

The last cell uses `chat.send_message(...)`. That assumes you already have a **chat session** variable named `chat`, for example after you conduct a mock interview in the same notebook:

```python
chat = model.start_chat(history=[])
chat.send_message("You are an interviewer. Ask me one question at a time...")
# ... your back-and-forth ...
```

Then run the scoring cell so the model can judge the full conversation.

If you run the scoring cell **before** defining `chat`, you will get `NameError: name 'chat' is not defined`.

## Model

The notebook uses `gemini-2.5-flash` by default. You can change the model string in the `GenerativeModel(...)` line if your API supports other IDs.

**Note:** When you import `google.generativeai`, the runtime may show that this package is deprecated in favor of **`google.genai`**. The notebook still runs; for new projects, consider migrating to the newer SDK when you have time.

## Troubleshooting

| Issue | What it usually means |
|--------|------------------------|
| **401 / invalid API key** | Wrong or missing `GEMINI_API_KEY` in `.env` or environment. |
| **503 / UNAVAILABLE** | Temporary Gemini capacity; wait and retry, or try again later. |
| **`JSONDecodeError` / empty text** | Use `response_mime_type: application/json` (as in the notebook) and the `parse_json_from_text` helper; avoid `json.loads` on raw text alone. |
| **`chat` is not defined** | Start a chat with `model.start_chat(...)` before the scoring cell. |

## License / use

Personal learning project; ensure your use complies with [Google’s Gemini API terms](https://ai.google.dev/terms) and your API key settings.
