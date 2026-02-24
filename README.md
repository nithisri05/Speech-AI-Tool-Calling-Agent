# Voice AI Agent  
### Speech-to-Text + Tool Calling + Text-to-Speech

A full end-to-end **Voice-to-Voice AI Agent** built using OpenAI APIs.

This project demonstrates:

- Speech Recognition (Whisper)
- Intelligent Reasoning (GPT-4.1 with Tool Calling)
- Dynamic Tool Execution
- Conversation Memory
- Text-to-Speech Response

---

# Overview

This system enables natural voice interaction:

1. User speaks
2. Audio is transcribed
3. LLM processes request
4. Tools are called dynamically (if required)
5. Response is generated
6. Response is spoken back to user

This is a **true Voice AI Agent architecture**.

---

# Architecture

```
User Speech
        ↓
Speech-to-Text (Whisper)
        ↓
LLM (GPT-4.1 + Tool Calling)
        ↓
Dynamic Tool Execution Layer
        ↓
LLM Final Response
        ↓
Text-to-Speech (gpt-4o-mini-tts)
        ↓
Spoken Output
```

---

# How It Works

## 1️. Speech-to-Text

- Audio is recorded or uploaded
- Whisper transcribes speech into text
- Transcribed text becomes user input

---

## 2️.Tool-Enabled LLM Reasoning

The model receives:

- System instructions
- Conversation memory
- Tool definitions

It decides whether to:
- Respond directly
- Or call a function (tool)

Tool calls are returned as structured JSON.

---

## 3️.Dynamic Tool Execution

The backend:

- Reads tool name from LLM output
- Uses a dispatcher (`tool_functions`)
- Executes corresponding Python function
- Sends result back to LLM

---

## 4️.Conversation Memory

Memory is maintained as:

```python
memory = [
    {"role": "system", "content": "..."},
    {"role": "user", "content": "..."},
    {"role": "assistant", "content": "..."},
]
```

Each interaction appends to this list.

Since LLMs are stateless, full history is sent with every request.

---

## 5️.Text-to-Speech

Final assistant response is converted to speech using:

```
gpt-4o-mini-tts
```

Audio is saved and played back to the user.

---

#  Available Tools

| Tool | Description |
|------|------------|
| `get_time()` | Returns current date and time |
| `get_weather(city)` | Fetches live weather using external API |
| `calculate(expression)` | Evaluates mathematical expressions |

Tools are defined in a schema and dynamically executed.

---

#  Features

- Whisper-based transcription
- GPT-4.1 function calling
- Dynamic tool execution
- Multi-turn memory
- Text-to-Speech synthesis
- External API integration
- Calculator support
- Agentic workflow
- Modular architecture

---

# Tech Stack

- Python
- OpenAI API
- Whisper (Speech-to-Text)
- GPT-4.1 (Reasoning + Tool Calling)
- gpt-4o-mini-tts (Text-to-Speech)
- Requests (Weather API)
- JSON
- IPython Audio / Local Audio Playback

---

# Installation

```bash
pip install openai requests
```

Add your API keys inside the script:

```python
client = OpenAI(api_key="YOUR_API_KEY")
WEATHER_API_KEY = "YOUR_WEATHER_API_KEY"
```

---

# How To Run

1. Run all cells / script
2. Speak into microphone or provide audio file
3. Agent processes request
4. Assistant speaks response

To exit:

```
quit
```

---

# Example Queries

- "What is the time?"
- "Weather in Erode?"
- "Calculate 25 * 8"
- "Is it raining in Chennai?"
- "What did I say earlier?"

---

# What This Project Demonstrates

This project showcases:

- LLM orchestration
- Tool routing architecture
- Dynamic function dispatch
- API handling
- Stateful conversation design
- Voice AI system pipeline
- Error debugging and sequencing logic

---



# Future Improvements

- Streaming audio responses
- Async tool execution
- Vector database for long-term memory
- FastAPI deployment
- Docker containerization
- Real-time web interface
- Secure math evaluator (replace eval)
- Structured logging

---

#  Final Note

This repository demonstrates a production-style Voice AI Agent architecture combining:

- Speech-to-Text
- Intelligent tool calling
- Conversation memory
- Text-to-Speech

Suitable for:

- AI engineering roles
- Backend developer interviews
- LLM orchestration projects
- Voice assistant research
