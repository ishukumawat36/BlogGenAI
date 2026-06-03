# Blog Generation Agentic AI

An agentic AI-powered blog generation system built with LangGraph and Groq. AgentScribe autonomously generates SEO-friendly blog titles, detailed content, and translates output into multiple languages — all through a structured multi-node graph pipeline.

## Features

- **Agentic Blog Generation** — LangGraph-powered pipeline for title creation and content generation
- **Multi-language Translation** — Supports Hindi and French translations out of the box; defaults to English for unsupported languages
- **FastAPI REST API** — Simple HTTP endpoint to trigger blog generation
- **LangGraph Studio Ready** — Pre-configured `langgraph.json` for visual graph debugging
- **Groq LLM Backend** — Blazing-fast inference using `llama-3.1-8b-instant`

## Tech Stack

- [LangGraph](https://github.com/langchain-ai/langgraph) — Agentic graph orchestration
- [LangChain](https://github.com/langchain-ai/langchain) — LLM abstractions
- [Groq](https://groq.com/) — LLM inference
- [FastAPI](https://fastapi.tiangolo.com/) — REST API
- [Uvicorn](https://www.uvicorn.org/) — ASGI server

## Project Structure

```
AgentScribe/
├── src/
│   ├── graphs/
│   │   └── graph_builder.py   # LangGraph pipeline definitions
│   ├── nodes/
│   │   └── blog_node.py       # Node logic (title, content, translation, routing)
│   ├── states/
│   │   └── blogstate.py       # State schema (BlogState, Blog)
│   └── llms/
│       └── groqllm.py         # Groq LLM wrapper
├── app.py                     # FastAPI app entry point
├── langgraph.json             # LangGraph Studio config
├── pyproject.toml
└── requirements.txt
```

## Setup

1. **Clone the repo**
   ```bash
   git clone https://github.com/your-username/AgentScribe.git
   cd AgentScribe
   ```

2. **Create a virtual environment and install dependencies**
   ```bash
   python -m venv .venv
   source .venv/bin/activate
   pip install -r requirements.txt
   ```

3. **Set environment variables** — create a `.env` file:
   ```env
   GROQ_API_KEY=your_groq_api_key
   LANGSMITH_API_KEY=your_langsmith_api_key  # optional, for tracing
   ```

4. **Run the API server**
   ```bash
   python app.py
   ```

## API Usage

### `POST /blogs`

Generate a blog post.

**Request body:**
```json
{
  "topic": "Agentic AI",
  "language": "hindi"
}
```

| Field      | Type   | Required | Description                                      |
|------------|--------|----------|--------------------------------------------------|
| `topic`    | string | Yes      | The blog topic                                   |
| `language` | string | No       | Target language (`hindi`, `french`). Defaults to English |

**Response:**
```json
{
  "data": {
    "topic": "Agentic AI",
    "blog": {
      "title": "...",
      "content": "..."
    },
    "current_language": "hindi"
  }
}
```

## LangGraph Studio

```bash
langgraph dev
```

Open LangGraph Studio and connect to visualize and debug the graph pipeline.

## License

MIT
