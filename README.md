# Chatbot with memory

This project contains implementations of a chatbot using Google's Gemini API through the OpenAI-compatible interface.

## Notebooks

### `memory_chat.ipynb`

A manual history management implementation that integrates conversation history with the OpenAI completion library.

**Features:**
- Manually maintains a `history` list to store conversation context
- Appends user messages and assistant responses to the history after each API call
- Uses the history to build complete message contexts for the API
- Suitable for programmatic use cases where you need full control over conversation state

**Key implementation details:**
- History is stored as a list of dictionaries with `role` and `content` keys
- The `generate_message()` function combines system prompt, history, and current user message
- History persists across multiple calls within the same notebook session

### `chatbot.ipynb`

A Gradio-based UI implementation that leverages Gradio's built-in history management feature.

**Features:**
- Uses `gr.ChatInterface` with `type="messages"` for automatic history management
- Gradio handles conversation history automatically through its UI
- The chat function receives history as a parameter from Gradio and converts it to the API format
- User-friendly web interface that can be shared via public URLs

**Key implementation details:**
- History is automatically maintained by Gradio's ChatInterface
- The `chat()` function receives history in Gradio's message format and converts it for the API
- Can be launched locally or shared via public Gradio URLs

## Setup

1. Install dependencies:
   ```bash
   uv sync
   ```

2. Create a `.env` file with your API key:
   ```
   GOOGLE_API_KEY=your_api_key_here
   ```

3. Run the notebooks in Jupyter or JupyterLab

## Dependencies

- Python 3.12+
- OpenAI Python SDK (for API compatibility)
- Gradio (for chatbot UI)
- python-dotenv (for environment variables)
- ipykernel (for Jupyter notebook support)

