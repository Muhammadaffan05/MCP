Read file: pyproject.toml
Ran tool
Read file: mcpserver/requirements.txt
Here’s a brief and clear README for your project, covering the MCP server, usage, and Docker integration:

---

# MCP Crash Course

This project demonstrates how to build and interact with an MCP (Model Context Protocol) server using Python, with support for weather alerts and conversational agents. It also includes Docker support for easy deployment.

## Features

- **Weather Alerts Tool:**  
  Get real-time weather alerts for any US state using the National Weather Service API.

- **Conversational Agent:**  
  Uses `langchain-groq` and MCP tools to enable chat-based interactions with memory.
  
  **Model Used:** `llama-3.3-70b-versatile` (via ChatGroq)

- **MCP Server & Client:**  
  Includes both server and client implementations for tool invocation and chat.

- **Docker Support:**  
  Easily build and run the server in a containerized environment.

## Project Structure

```
.
├── main.py
├── pyproject.toml
├── README.md
├── server/
│   ├── weather.py         # Weather tool implementation
│   ├── client.py          # Chat client using MCPAgent
│   └── weather.json       # MCP tool configuration
├── mcpserver/
│   ├── server.py          # Example MCP server
│   ├── client-stdio.py    # Example stdio client
│   ├── client-sse.py      # Example SSE client
│   ├── Dockerfile         # Docker setup for server
│   └── requirements.txt   # Minimal requirements for Docker
└── .venv/                 # Virtual environment (ignored)
```

## Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/Muhammadaffan05/MCP.git
cd MCP
```

### 2. Set up a virtual environment (recommended)

```bash
uv venv --python=python3.13
source .venv/bin/activate
uv add -r pyproject.toml
```

### 3. Configure Environment Variables

Create a `.env` file in the root or set the following in your environment:
- `GROQ_API_KEY` (for language model access)

### 4. Run the MCP Server

```bash
python mcpserver/server.py
```

### 5. Run the Client

```bash
python server/client.py
```

Or try the stdio client:
```bash
python mcpserver/client-stdio.py
```

## Docker Usage

Build and run the server in Docker:

```bash
cd mcpserver
docker build -t mcp-server .
docker run -p 8000:8000 mcp-server
```

- The Dockerfile uses Python 3.11, installs dependencies with `uv`, and runs the MCP server.

## Dependencies

- Python 3.13+ (or 3.11+ for Docker)
- httpx
- langchain-groq
- mcp-use
- mcp[cli]
- nest-asyncio

All dependencies are managed via `pyproject.toml` and `uv`.

## Notes

- `.venv/`, `__pycache__/`, and other generated files are gitignored.
- For best results, use the latest stable Python version.
- Make sure to set up your API keys and environment variables as needed.

---

Let me know if you want this saved to your `README.md` or need any changes!