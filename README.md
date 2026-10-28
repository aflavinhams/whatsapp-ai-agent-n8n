# WhatsApp AI Agent | Gemini & n8n 🤖

### AI-powered conversational assistant with workflow automation and external integrations

An intelligent WhatsApp assistant built using **n8n, Google's Gemini API, and AI Agent workflows** to understand natural language requests, manage shopping lists, and automate interactions with external services.

This project explores how Large Language Models (LLMs) can be integrated with automation workflows, conversational memory, and external tools to build practical AI-powered applications.

## Project Overview

The goal was to develop a conversational assistant capable of processing WhatsApp messages and performing actions based on user requests.

Instead of relying exclusively on predefined conversational rules, the assistant uses an LLM-based agent to interpret messages and interact with connected tools.

Key capabilities include:

- Natural language understanding powered by Gemini.
- AI Agent orchestration using n8n.
- Conversational memory for maintaining context.
- Shopping list management through external integrations.
- Google Sheets integration for structured data.
- Automated message processing and responses.

## Architecture

The application was designed using a visual workflow in n8n.

![AI Agent Workflow](images/workflow.png)

### Workflow Components

**1. Webhook**

Receives incoming requests and initiates the automation workflow.

**2. Data Processing**

Processes incoming messages, extracts relevant information, and prepares data for the AI Agent.

**3. Gemini LLM**

Provides language understanding and response generation capabilities.

**4. AI Agent**

Interprets user requests and selects the appropriate tools or actions according to the conversation context.

**5. Conversational Memory**

Stores conversational context to support interactions across multiple messages.

**6. External Tools**

Connects the AI Agent to services such as Google Sheets for accessing and managing shopping list information.

**7. Automated Responses**

Generates and sends responses through the messaging integration.

## Tech Stack

| Technology | Purpose |
|---|---|
| n8n | Workflow automation and AI Agent orchestration |
| Google Gemini | Large Language Model |
| Google Sheets | Structured data integration |
| Webhooks | Event-driven communication |
| AI Agent | Tool selection and execution |
| Conversational Memory | Context management |
| WhatsApp | User interaction interface |

## What I Learned

This project provided hands-on experience with:

- Building LLM-powered agents.
- Integrating language models with external tools.
- Designing automated conversational workflows.
- Using APIs and webhooks to connect applications.
- Managing conversational context.
- Developing practical AI-based automations.

## Project Status

**Completed academic/personal project — documentation showcase.**

The original workflow was developed using n8n's free environment and is no longer available for export.

This repository documents the application's architecture and original implementation through screenshots and technical descriptions.

The repository does not currently include an executable workflow or deployment instructions.

## Author

**Ana Flávia Martins dos Santos**

Computer Science Undergraduate | AI & GenAI Enthusiast

[GitHub](https://github.com/aflavinhams) | [LinkedIn](https://www.linkedin.com/in/ana-flavia-martins-dos-santos-058104281)
