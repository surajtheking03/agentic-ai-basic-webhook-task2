# Webhook-Based AI Agent (Task 2) — n8n + Gemini

This repository contains my second working AI automation workflow built using **n8n** with a live **webhook trigger**, **JavaScript prompt builder**, and **Gemini Flash Lite model** for intelligent personalized responses.

---

## 📌 Overview

This workflow allows an external system (Postman/Hoppscotch/Frontend App) to send a POST request containing a user's name and message. The AI then generates a personalized reply and sends it back through the webhook response.

Example result:

User → "Hello"
Response → "Hi Suraj! 😄 Agent Jaanu here — what’s on your mind?"


---

## 🧱 Workflow Architecture

| Step | Component | Purpose |
|------|----------|---------|
| 1️⃣ | Webhook Trigger | Receives external POST request |
| 2️⃣ | JavaScript Node | Extracts name & message and builds AI prompt |
| 3️⃣ | Basic LLM Chain | Passes the prompt to Gemini Flash Lite |
| 4️⃣ | Edit Fields | Formats the output into a clean JSON response |
| 5️⃣ | Webhook Respond | Sends the AI reply back to the sender |

---

## 🧠 Prompt Behavior

The LLM is instructed to behave as a warm, playful AI assistant with the persona:

> **Agent Jaanu — friendly, humorous, and personal.**

It must:
- Use the exact name sent in the input JSON  
- Respond concisely  
- Add emojis when appropriate  
- Maintain a conversational tone  

---

## 🧪 Testing Instructions

Send a POST request to:

http://localhost:5678/webhook-test/agent-v1


With JSON body:

```json
{
  "name": "Suraj",
  "message": "Hello agent, respond please"
}



{
  "reply": "Hi Suraj! 😎 Agent Jaanu reporting for duty. What's up?"
}

// 🔑 Note: This workflow does not include an active API key for safety reasons.

To run it successfully:

1. Import the workflow into your n8n instance.
2. Open the "Google Gemini" credential node.
3. Add your own Gemini API key.
4. Save credentials and re-run the workflow.

API keys are intentionally removed before publishing to protect security and avoid unauthorized usage. 🙂

