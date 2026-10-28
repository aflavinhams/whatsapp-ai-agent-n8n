# WhatsApp AI Agent — Gemini, n8n, WAHA & Redis

A personal **Generative AI agent** built with **n8n** to manage a shopping list through WhatsApp. The assistant accepts natural-language requests, uses tools connected to **Google Sheets**, maintains conversation context with **Redis**, and responds using **WAHA**. The workflow also includes an audio-message transcription path using **Gemini**.

> **Portfolio project (2025).** This repository contains a sanitized export of the original workflow and a configuration example. The original environment is not publicly hosted; running it requires setting up your own integrations, credentials, and instances. This repository does not claim measured business outcomes.

## What it does

- Receives incoming WhatsApp message events from WAHA through an n8n webhook.
- Processes ordinary text requests through a **Gemini-powered AI Agent**.
- Lets the agent **add, remove, and list** grocery items in a **Google Sheets** spreadsheet using tool calls.
- Requests missing information (such as quantity) before adding an item.
- Maintains conversational context with **Redis Chat Memory**.
- Includes a branch to **read and transcribe voice recordings** with Gemini before routing text to the agent.
- Sends text responses and message-read acknowledgements back through WAHA.

## Architecture

```text
WhatsApp → WAHA → n8n Webhook → Message routing
                                  ├── Text ─────────────────────────┐
                                  └── Audio → File → Gemini STT ────┤
                                                                      ↓
                                 Gemini Chat Model → n8n AI Agent ← Redis Memory
                                                         ↕
                                          Google Sheets tools (add/remove/list)
                                                         ↓
                                               WAHA → WhatsApp reply
```

## Stack

- **n8n** — workflow and agent orchestration
- **Google Gemini** — chat model (`gemini-2.0-flash` in the exported workflow) and audio transcription (`gemini-2.5-flash`)
- **Redis** — chat memory keyed by conversation
- **Google Sheets** — shopping-list persistence and agent tools
- **WAHA** — WhatsApp gateway integration
- **Docker Compose and ngrok** — original local development infrastructure

## Repository files

- [`workflow/whatsapp-agent.sanitized.json`](workflow/whatsapp-agent.sanitized.json) — sanitized n8n workflow export; importable as a starting point, **not ready to run without setup**
- [`docker-compose.example.yml`](docker-compose.example.yml) — illustrative configuration with no live access tokens or passwords

## Setup notes

1. Install Docker and provision your own n8n, Redis, and WAHA services. This repository's Compose file is a **configuration example**, not a fully tested deployment recipe.
2. Import the workflow JSON into n8n.
3. Configure your own Gemini API, Google Sheets OAuth2, Redis, and WAHA credentials in the relevant nodes.
4. Create a Google Sheets document with columns `Produto`, `Quantidade`, and `Usuário`, and replace the placeholder document ID in the relevant Google Sheets nodes and agent prompt.
5. Configure WAHA webhook events, media mounts, and an accessible webhook URL appropriate to your installation.
6. Review model availability, n8n/WAHA node compatibility, and the workflow branches before testing.

**Limitations:** An unused `Switch1` node remains in the original export. The agent prompt mentions a `send_list` tool, but the exported connections include only `add_item`, `remove_item`, and `list_items`; requests for the list link therefore should not be treated as a verified standalone tool implementation. Audio transcription is represented in the exported path but is not independently re-tested here. The workflow export is marked inactive.

## Demonstration

<img width="1600" height="900" alt="WhatsApp Image 2026-10-28 at 15 05 06" src="https://github.com/user-attachments/assets/f70552fc-f554-439d-818a-b4e58a0c6068" />
<img width="685" height="833" alt="WhatsApp Image 2026-10-28 at 15 06 10" src="https://github.com/user-attachments/assets/0ff10973-b092-41f0-9a11-4289c2367ce9" />

## Security

The original export and infrastructure files contained private resource identifiers and infrastructure configuration. This public version deliberately removes credential references, instance identifiers, direct spreadsheet links, access tokens, and hard-coded secrets. **Never commit your actual `.env`, tokens, credentials, or a raw n8n export without reviewing it.**

## Author

Ana Flávia Martins dos Santos — [GitHub](https://github.com/aflavinhams) · [LinkedIn](https://www.linkedin.com/in/ana-flavia-martins-dos-santos-058104281)
