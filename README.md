# Prompt Enhancer — Telegram Audio to Gemini Transcription Workflow

An **N8N workflow** that turns Telegram voice messages into intelligent and enhanced text prompts using **Gemini AI**.  
Speak to your Telegram bot, and it will automatically transcribe your voice, process your input through Gemini, and send back a contextual text prompt with RICC (Role, Input, Context, Constraints) framework.

---

## 🧩 Overview

This workflow integrates **Telegram Bot API** and **Gemini AI** through N8N’s automation engine.

-   Accepts **voice messages** from Telegram users
-   Uploads and **transcribes audio** via Gemini API
-   Sends back **AI-generated text responses** directly in Telegram

![Workflow Execution](assets/Prompt%20Enhancer-N8N%20Workflow.gif)  
_GIF: N8N Workflow in action._

---

## ⚙️ Workflow Stages

### **Stage 1: Telegram Bot Trigger**

-   The **Telegram Trigger** node listens for new Telegram messages.
-   When a voice message is received, it captures file metadata (chat ID, file ID, etc.).
-   Example user input (spoken audio):
    > “I want to learn French and want to talk to you for any questions or clarifications.”

### **Stage 2: Audio Retrieval**

-   The **Telegram File** node fetches the `.ogg` voice file from Telegram servers for processing.

### **Stage 3: Upload Preparation**

-   The workflow initiates an upload session and sends the file to Gemini’s file upload endpoint using the **HTTP Request** nodes (`initialize upload session` + `upload file`).

### **Stage 4: AI Transcription and Response**

-   The **Ask Gemini to transcribe** node sends a transcription request.
-   Gemini processes the audio, transcribes speech into text, and generates a structured prompt response.

### **Stage 5: Telegram Message Reply**

-   The **Send a text message** node sends Gemini’s response back to the Telegram chat.
-   Example output (as seen in chat):

![Telegram Chat](assets/Telegram%20Chat%20Screenshot.png)  
_Screenshot: Gemini’s generated prompt sent back to the user._

---

## 🧱 Prerequisites

Before using this workflow, ensure you have:

-   [N8N](https://n8n.io) v1.70 or newer
-   A Telegram Bot Token (from [@BotFather](https://t.me/botfather))
-   A Google Gemini API key
-   Access to Gemini File Upload and Transcription endpoints
-   Basic familiarity with N8N workflow import and credentials setup

---

## 🚀 Setup Instructions

1. **Clone the repository**
    ```bash
    git clone https://github.com/HarshaEmani/prompt-enhancer-n8n.git
    cd prompt-enhancer-n8n
    ```
