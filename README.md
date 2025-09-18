# CopilotKit + Google DeepMind Gemini + LangGraph Template

A full-stack template to build AI agents using **CopilotKit**, **Google DeepMind’s Gemini**, and **LangGraph**.  
This project demonstrates how to create **context-aware, task-focused, and UI-integrated AI agents** with a **Next.js frontend** and a **FastAPI backend**.

---

## Table of Contents

1. [Features](#features)  
2. [Tech Stack](#tech-stack)  
3. [Demo](#demo)  
4. [Project Structure](#project-structure)  
5. [High-Level Architecture](#high-level-architecture)  
6. [Call Sequences](#call-sequences)  
7. [Setup & Installation](#setup--installation)  
8. [Usage](#usage)  
9. [Hosted Demo](#hosted-demo)  
10. [Notes](#notes)  
11. [Why This Matters](#why-this-matters)  
12. [Credits](#credits)

---

## Features

- **Post Generator Agent**  
  Generate LinkedIn & Twitter posts based on the context you provide.  
  Ideal for professional, context-aware social content.

- **Stack Analyzer Agent**  
  Given a URL, get a **detailed breakdown** of the website’s technology stack.  
  Useful for quickly identifying frameworks, libraries, and infrastructure.

---

## Tech Stack

| Layer            | Technology & Tools                                                                 |
|------------------|-------------------------------------------------------------------------------------|
| **Frontend**     | Next.js 15 (TypeScript), CopilotKit SDK (`@copilotkit/react-core`, `@copilotkit/runtime`, `@copilotkit/react-ui`) |
| **Backend**      | FastAPI (Python), Uvicorn (ASGI server)                                             |
| **Agents**       | Google Gemini via `google-genai` (official SDK), LangGraph (StateGraphs for workflows), LangChain’s Google adapter |
| **Data Models**  | Pydantic (structured JSON tool outputs)                                             |
| **Deployment**   | Vercel (frontend), typical Python host (backend)                                    |

---

## Demo

### Video Walkthrough

<video src="https://github.com/user-attachments/assets/1e95c9e1-2d55-4f63-b805-be49fe94a493" controls width="800"></video>

### GIF Demos (links)

- [Post Generator in Action](https://github.com/SindhuraSriram/gemini-copilot-agents/blob/main/assets/example1.gif)  
- [Stack Analyzer Output](https://github.com/SindhuraSriram/gemini-copilot-agents/blob/main/assets/example2.gif)

---

## Project Structure

<p align="center">
  <img src="https://github.com/SindhuraSriram/gemini-copilot-agents/blob/main/assets/project_structure.png" 
       alt="Project Structure" width="800"/>
</p>

---

## How It Works

At a high level, here’s the flow of the system:

1. **User Input** → You provide context (a text snippet or a URL).  
2. **Frontend Capture** → CopilotKit SDK in Next.js captures the input and sends it through the runtime.  
3. **Backend Routing** → FastAPI receives the request and prepares the agent workflow.  
4. **Agent Reasoning** → LangGraph (StateGraphs) orchestrates Gemini calls and tool usage.  
5. **LLM Processing** → Google Gemini, via the official `google-genai` SDK, performs reasoning or text generation.  
6. **Structured Output** → Pydantic enforces structured JSON outputs when tools are used.  
7. **Response** → The result is passed back through FastAPI → CopilotKit → UI, displayed seamlessly in the app.
   
---

## High-Level Architecture

<p align="center">
  <img src="https://github.com/SindhuraSriram/gemini-copilot-agents/blob/main/assets/high_level_architecture.png" 
       alt="High-Level Architecture" width="800"/>
</p>

---

##  Why LangGraph (StateGraphs)?

- Provides **stateful workflows** — unlike stateless prompt chains, it can maintain memory across steps.  
- Supports **branching logic** — different paths depending on agent needs (e.g., fetch site data → analyze libraries → summarize).  
- Makes it easier to **scale to multiple agents** without rewriting orchestration logic.  

This ensures our agents behave predictably while handling complex tasks.


## Why CopilotKit?

- Unlike a chat widget, CopilotKit makes the agent **feel native to your app**.  
- The SDK (`@copilotkit/react-core`, `@copilotkit/runtime`, `@copilotkit/react-ui`) lets you embed agents directly in React components.  
- Pass **context from anywhere in the UI** (forms, pages, even buttons).  
- Creates a **fluid developer + user experience** where agents are part of the workflow, not bolted on.

---
## Call Sequences

### Post Generator

<p align="center">
  <img src="https://github.com/SindhuraSriram/gemini-copilot-agents/blob/main/assets/call_sequence_post_generator.png" 
       alt="Post Generator Call Sequence" width="800"/>
</p>

### Stack Analyzer

<p align="center">
  <img src="https://github.com/SindhuraSriram/gemini-copilot-agents/blob/main/assets/call_sequence_stack_analyzer.png" 
       alt="Stack Analyzer Call Sequence" width="800"/>
</p>

---

## Setup & Installation

### 1. Clone the repository

```bash
git clone https://github.com/SindhuraSriram/gemini-copilot-agents.git
cd gemini-copilot-agents
```

### 2. Configure Environment Variables

Create `.env` files in both frontend and backend directories.

- **Backend** (`agent/.env`):

```env
GOOGLE_API_KEY=<<your-gemini-key-here>>
```

- **Frontend** (`.env` in root):

```env
GOOGLE_API_KEY=<<your-gemini-key-here>>
```

### 3. Install Dependencies

- **Frontend**:

```bash
pnpm install
pnpm dev
```

- **Backend**:

```bash
cd agent
pip install -r requirements.txt
uvicorn main:app --reload --port 8000
```

---

## Usage

- Navigate to [http://localhost:3000](http://localhost:3000)  
- Ensure the FastAPI backend is running.  
- Use the **Post Generator** to create LinkedIn/Twitter posts.  
- Use the **Stack Analyzer** to inspect a website’s tech stack.

---

## Hosted Demo

Live version: **https://copilot-kit-deepmind.vercel.app/**

---

## Notes

- Ensure environment variables are correctly set before running.  
- Backend must be running before frontend can fetch agent responses.  
- Adjust asset paths if modifying directory structure.

---

## Why This Matters

This project demonstrates how **CopilotKit + LangGraph + Gemini** can be combined to build:

- **Context-aware agents** — they adapt to your input  
- **Task-focused tools** — purpose-built (post generation, stack analysis)  
- **UI-integrated experiences** — embedded directly into your app  

---

## 🚀 Future Extensions

This project can be extended in several exciting directions:

- **Persistence Layer** → Store outputs in Postgres or Supabase for history & analytics.  
- **Authentication** → Add NextAuth or Clerk for user-level agent sessions.  
- **Multi-Agent Orchestration** → One agent for post generation, another for hashtag optimization, another for scheduling.  
- **Additional Tools** → Expand Stack Analyzer with Lighthouse audits or SEO analysis.  
- **UI Enhancements** → Rich CopilotKit components for more interactive experiences.

---

## Credits

- [CopilotKit](https://github.com/CopilotKit/CopilotKit)  
- [LangGraph](https://www.langchain.com/langgraph)  
- [Google Gemini](https://deepmind.google/technologies/gemini)  
- Inspired by the [CopilotKit blog post](https://dev.to/copilotkit/heres-how-to-build-fullstack-agent-apps-gemini-copilotkit-langgraph-15jb)  

<p align="center">
  <a href="https://github.com/CopilotKit/CopilotKit" target="_blank">
    <img src="https://img.shields.io/badge/Checkout-CopilotKit-blue?style=for-the-badge&logo=github" alt="CopilotKit"/>
  </a>
</p>
