# Kendra – GPT-3.5 Turbo Voice Chatbot with Bing Search & DALL·E

**A Python voice chatbot powered by OpenAI GPT-3.5-Turbo, Microsoft Bing Search, Amazon Polly text-to-speech, and DALL·E image generation.** Chat by typing, hear replies spoken aloud, search the web, and generate images—all from the terminal.

---

## Table of Contents

- [Features](#features)
- [Quick Start](#quick-start)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Configuration](#configuration)
- [Usage](#usage)
- [Commands & Capabilities](#commands--capabilities)
- [Customization](#customization)
- [Use Cases](#use-cases)
- [Acknowledgments](#acknowledgments)

---

## Features

| Feature | Description |
|--------|-------------|
| **Conversational AI** | Natural dialogue using OpenAI GPT-3.5-Turbo with conversation memory |
| **Voice output** | Replies spoken aloud via Amazon Polly (text-to-speech) |
| **Web search** | Bing Search API integration—search the web from the chat |
| **Image generation** | Create images with DALL·E from text descriptions; saved to your desktop |
| **Persistent history** | Conversation is saved when you quit properly and restored on next run |

---

## Quick Start

```bash
# 1. Clone and enter the project
git clone https://github.com/YOUR_USERNAME/Chatbot-GPT-3.5-turbo.git
cd Chatbot-GPT-3.5-turbo

# 2. Install dependencies
pip install openai boto3 pygame requests

# 3. Add your API keys in KendraGenVIbot.py (see Configuration)
# 4. Run the chatbot
python KendraGenVIbot.py
```

Type **quit** when done so your conversation is saved.

---

## Prerequisites

- **Python 3.8+** — [Download Python](https://www.python.org/downloads/)
- **OpenAI API key** — for GPT-3.5-Turbo and DALL·E
- **Bing Search API** — subscription key and endpoint (Azure)
- **AWS account** — for Amazon Polly (region, access key, secret key)

---

## Installation

Install required packages:

```bash
pip install openai boto3 pygame requests
```

| Package | Purpose |
|---------|--------|
| `openai` | GPT-3.5-Turbo chat and DALL·E image generation |
| `boto3` | Amazon Polly text-to-speech |
| `pygame` | Audio playback for Polly output |
| `requests` | Bing Search API and image download |

---

## Configuration

Edit `KendraGenVIbot.py` and set your credentials.

### OpenAI (GPT-3.5-Turbo & DALL·E)

1. Sign up at [OpenAI](https://platform.openai.com/signup).
2. Create an API key in the [OpenAI dashboard](https://platform.openai.com/api-keys).
3. Replace `YOUR_OPENAI_API_KEY` with your key.

### Bing Search API

1. Create a Bing Search resource in [Azure](https://portal.azure.com/) — see [Bing Search API docs](https://learn.microsoft.com/en-us/bing/search-apis/bing-web-search/create-bing-search-service-resource).
2. Replace `YOUR_BING_SEARCH_API_KEY` with your subscription key.
3. Replace `BING SEARCH ENDPOINT` with your Bing endpoint URL.

### Amazon Polly (Voice)

1. Log in to [AWS Console](https://console.aws.amazon.com/).
2. Create an IAM user with programmatic access and Polly permissions ([IAM](https://console.aws.amazon.com/iam/)).
3. Replace `YOUR_AWS_ID_API_KEY` and `YOUR_AWS_SECRET_KEY`.
4. Set `YOUR_REGION_NAME` (e.g. `us-east-1`).

---

## Usage

Run the chatbot:

```bash
python KendraGenVIbot.py
```

- Type your message and press Enter.
- Kendra replies in text and speaks the response (Polly).
- Type **quit** to exit and **save** the conversation.

> **Important:** Conversation history is only saved when you exit with **quit**. Exiting with Ctrl+C or closing the terminal will not save.

---

## Commands & Capabilities

### Chat

- Type any question or message for a GPT-3.5-Turbo reply.
- Replies are shown in the terminal and read aloud.

### Web search

- Include the word **search** in your message (e.g. `search latest Python news`).
- The bot uses Bing to return search results and reads them.

### Image generation

1. Type **generate image**.
2. When asked, describe the image you want.
3. DALL·E generates it and saves it to your **Desktop** as a `.jpg` file.

---

## Customization

### Chat response (token and history limits)

In `generate_chat_response`:

- **Number of messages kept:** change `conversation[-15:]` (default: last 15).
- **Token limit:** change `4096` to adjust when history is trimmed.
- **Max response length:** change `max_tokens=1000` in the API call.

### Search result count

In `search_bing`, change the `count` in `params` (default: 5; max 50 per Bing API).

### Amazon Polly voice

1. Pick a voice from the [Polly voice list](https://docs.aws.amazon.com/polly/latest/dg/voicelist.html).
2. In `speak_text`, change `VoiceId="Joey"` to your chosen voice (e.g. `"Emma"`).

Not all voices support the neural engine; if you get an error, try another voice or region. See [Polly regions](https://docs.aws.amazon.com/general/latest/gr/rande.html#polly_region).

---

## Use Cases

- **Customer support** — 24/7 conversational support with search and voice.
- **Personal assistant** — Quick answers, web search, and image creation.
- **Education** — Interactive Q&A and explanations with voice.
- **Research** — Fast web search and summarization.
- **Accessibility** — Spoken replies for users who prefer or need audio.
- **Prototyping** — Base for building custom voice or multimodal bots.

---

## Acknowledgments

Kendra was built by combining **OpenAI GPT-3.5-Turbo** with **Microsoft Bing Search API**, **OpenAI DALL·E**, and **Amazon Polly** for a single voice-enabled chatbot experience.
