# CopilotKit + Google DeepMind Gemini + LangGraph Template

A full-stack template to build AI agents using **CopilotKit**, **Google DeepMind’s Gemini**, and **LangGraph**.  
Includes agents exposed through a Next.js frontend and a FastAPI backend.

---

## Table of Contents

1. [Features](#features)  
2. [Tech Stack](#tech-stack)  
3. [Demo](#demo)  
4. [Project Structure](#project-structure)  
5. [Setup & Installation](#setup--installation)  
6. [Usage](#usage)  
7. [Hosted Demo](#hosted-demo)  
8. [Notes](#notes)  
9. [Why This Matters](#why-this-matters)  
10. [Credits](#credits)

---

## Features

- **Post Generator Agent**  
  Generate LinkedIn & Twitter posts based on context you provide.

- **Stack Analyzer Agent**  
  Given a URL, get a detailed breakdown of the website’s tech stack.

---

## Tech Stack

| Layer         | Technology & Tools                                                                 |
|---------------|-------------------------------------------------------------------------------------|
| **Frontend**  | Next.js 15 (TypeScript), CopilotKit SDK (`@copilotkit/react-core`, `@copilotkit/runtime`, `@copilotkit/react-ui`) |
| **Backend**   | FastAPI (Python), Uvicorn (ASGI server)                                             |
| **Agents**    | Google Gemini via `google-genai` (official SDK), LangGraph (StateGraphs for workflows), LangChain’s Google adapter |
| **Data Models** | Pydantic (structured JSON tool outputs)                                           |
| **Deployment**| Vercel (frontend), typical Python host (backend)                                    |


---

## Demo

### Video Walkthrough

<video src="https://github.com/user-attachments/assets/1e95c9e1-2d55-4f63-b805-be49fe94a493" controls width="800"></video>

### Screenshots

#### Post Generator in Action
<img src="https://github.com/SindhuraSriram/gemini-copilot-agents/blob/main/assets/example1.gif" alt="Post Generator Demo" width="800"/>

#### Stack Analyzer Output
<img src="https://github.com/SindhuraSriram/gemini-copilot-agents/blob/main/assets/example2.gif" alt="Stack Analyzer Demo" width="800"/>

---

## Project Structure

```plaintext
.
├── agent/             # FastAPI backend agents
│   ├── main.py
│   └── ...
├── app/               # Next.js frontend
│   ├── pages/
│   ├── components/
│   └── ...
├── docs/              # Images, diagrams, documentation assets
└── README.md
```

---

##  High-Level Architecture

<p align="center">
  <img src="https://gist.githubusercontent.com/Anmol-Baranwal/8a833b19cc6a876296ca8df11731cbeb/raw/7483be99e3842eae8dbbbd7c4a8259495af1d405/architecture" 
       alt="High-Level Architecture" width="800"/>
</p>


## Setup & Installation

### 1. Clone the repository

```bash
git clone https://github.com/SindhuraSriram/gemini-copilot-agents.git
cd gemini-copilot-agents
```

### 2. Configuration

Create `.env` files in both frontend and backend directories.

- **Backend** (`agent/.env`):

```env
GOOGLE_API_KEY=<<your-gemini-key-here>>
```

- **Frontend** (`.env` in root):

```env
GOOGLE_API_KEY=<<your-gemini-key-here>>
```

### 3. Install dependencies

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
- Make sure the FastAPI backend is running.  
- Use the **Post Generator** to create LinkedIn/Twitter posts.  
- Use the **Stack Analyzer** to inspect a website’s tech stack.

---

## Hosted Demo

Live version: **https://copilot-kit-deepmind.vercel.app/**

---

## Notes

- Ensure environment variables are correctly set before running.  
- Backend must be running before frontend can fetch agent responses.  
- Adjust image paths (`./docs/images/...`) if needed.

---

## Why This Matters

This template shows how you can build AI agents that are:

- **Context-aware** — understand what the user inputs  
- **Task-focused** — perform well-defined jobs (post generation, stack analysis)  
- **UI-integrated** — embedded in the app UI, not just an external tool  

---

## Credits

- [CopilotKit](https://github.com/CopilotKit/CopilotKit)  
- [LangGraph](https://www.langchain.com/langgraph)  
- [Google Gemini](https://deepmind.google/technologies/gemini)  
- Inspired by the [CopilotKit blog post](https://dev.to/copilotkit/heres-how-to-build-fullstack-agent-apps-gemini-copilotkit-langgraph-15jb)  
