# MLH Mini Integrator – Webhook Listener
![last commit](https://img.shields.io/badge/last%20commit-yesterday-blue)
![javascript](https://img.shields.io/badge/javascript-100.0%25-yellow)
![languages](https://img.shields.io/badge/languages-1-blue)

A minimal real-world webhook integration built as part of the MLH Webhooks workshop.
This project demonstrates how applications receive external event notifications and forward them to services like Slack for alerting and monitoring.

---

## 🚀 Overview

Modern automation platforms such as Zapier, Make, and Superblocks use webhooks to notify systems when something happens.
This project recreates a simplified real workflow:

1. Receive webhook POST requests
2. Log the event for audit and debugging
3. Process payloads and decide whether the event should be forwarded
4. Send the event to Slack
5. Support optional advanced formatting via Slack Blocks

This simplifies and explains how real webhook-driven automation services operate.

---

## 🛠 Tech Stack
![Express](https://img.shields.io/badge/Express-black)
![JSON](https://img.shields.io/badge/JSON-lightgrey)
![npm](https://img.shields.io/badge/npm-red)
![.ENV](https://img.shields.io/badge/.ENV-yellow)
![JavaScript](https://img.shields.io/badge/JavaScript-yellow)
![Nodemon](https://img.shields.io/badge/Nodemon-green)
![Axios](https://img.shields.io/badge/Axios-purple)

* **Node.js**
* **Express.js**
* **Slack Incoming Webhooks**
* **Ngrok** (for public temporary URLs)

---

## 📂 Project Structure

```
mini-integrator/
│
├── index.js               # Core webhook processor
├── package.json
├── package-lock.json
├── .env                   # Slack & runtime configuration variables
├── webhook.log            # Auto-generated audit log
```

---

## ⚙️ Environment Variables

Create a `.env` file inside the project and configure:

```
PORT=3000
SLACK_WEBHOOK_URL=<your_webhook_url>
USE_SLACK_BLOCKS=false
```

You can enable Slack Block formatting by setting:

```
USE_SLACK_BLOCKS=true
```

---

## ▶️ Running the Project

Install dependencies:

```
npm install
```

Start the server:

```
npm run dev
```

Expose it publicly using ngrok:

```
ngrok http 3000
```

Use the generated public HTTPS URL as your webhook endpoint.

---

## 📩 Testing a Webhook Event

Example test using `curl`:

```
curl -X POST http://localhost:3000/webhook \
  -H "Content-Type: application/json" \
  -d '{"name":"Example Event","score":75}'
```

---

## 🧠 Features Implemented

### Receive and process webhook requests

Handles JSON payloads and safely processes event data.

### Slack integration (basic formatting)

Incoming events are forwarded to Slack using standard message text.

### Conditional filtering

Events can be ignored if they don’t meet processing rules.

For example: only send alerts if `score >= 50`.

### Persistent request logging

Every webhook call is logged into `webhook.log` for auditing.

---

## 📘 Example Log Output

```
2025-11-22T12:15:32.911Z - Received: {"name":"Example","score":90}
```

---

## 📅 Upcoming Features

The following improvements are planned:

* Enhanced Slack Block Kit formatting
* UI dashboard for viewing logs
* Multiple channel routing rules
* Storage in a persistent database
* Header validation and signature auth

---

## 🧩 What I Learned

* How real webhook systems work end-to-end
* How to expose local development servers using ngrok
* Sending messages programmatically to Slack
* Implementing basic automation logic similar to Zapier/Make
* Importance of logging and traceability in webhook workflows

---

<!--## 📝 License

This project is for educational purposes as part of the **MLH Webhooks Workshop**. -->
