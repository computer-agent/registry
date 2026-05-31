# Math Wiz 🤖🧮

**Math Wiz** is a LangChain-powered conversational agent that helps users work through arithmetic, numeric calculations, logic-based reasoning problems, and general knowledge questions. It runs as a Chainlit web chat application.

## What it does

Math Wiz uses a **ZERO_SHOT_REACT_DESCRIPTION** agent strategy with three specialised tools, routing each user query to the right tool automatically:

| Tool | Purpose |
|---|---|
| **Calculator** | Evaluates pure numeric/arithmetic expressions via `LLMMathChain` |
| **Reasoning Tool** | Solves logic and word problems step-by-step, presenting answers in bullet points |
| **Wikipedia** | Looks up world events, dates, and factual information |

## Example usage

```
User: What is 1234 * 5678?
Math Wiz: [uses Calculator] → 7,006,652

User: If a train travels at 60mph for 2.5 hours, how far does it go?
Math Wiz: [uses Reasoning Tool] → 150 miles (shows working in bullets)

User: When was calculus invented?
Math Wiz: [uses Wikipedia] → 17th century, Newton and Leibniz...
```

## Getting started

1. Clone the repo and install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
2. Add your OpenAI API key to a `.env` file:
   ```
   OPENAI_API_KEY=your-key-here
   ```
3. Run:
   ```bash
   chainlit run chatbot.py -w --port 8000
   ```

## Links

- **Repository:** https://github.com/tahreemrasul/math_app_langchain
- **Live demo:** https://takedowngpt.streamlit.app *(see README)*
- **Medium article:** https://medium.com/@tahreemrasul/how-to-build-your-own-chatbot-with-langchain-and-openai-f092822b6ba6
