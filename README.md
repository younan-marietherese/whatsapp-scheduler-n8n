# WhatsApp Scheduler using n8n + Node.js API + Cloudflare Tunnel

This project enables automated **WhatsApp message scheduling** using:

- A WhatsApp Web automation API (Node.js + whatsapp-web.js)
- A public endpoint created using **Cloudflare Tunnel**
- An **n8n workflow** for scheduling and sending messages

---

## Features

- Scheduled WhatsApp reminders (daily/weekly/monthly)
- External API to send WhatsApp messages
- Fully automated workflow using n8n
- Cloudflare Tunnel (HTTPS) for secure remote calls
- Real-time WhatsApp automation using whatsapp-web.js

---

## Project Structure

```
whatsapp-scheduler-n8n/
│ README.md
│ n8n-workflow.json
│ .gitignore
└── api/
    ├── index.js
    └── package.json
```

---

## Setup Instructions

### Install API dependencies
```
cd api
npm install
node index.js
```

### Start Cloudflare Tunnel
```
cloudflared tunnel --url http://localhost:3000
```

You will get a URL like:

```
https://abcde12345.trycloudflare.com
```

Use this URL in n8n.

---

## n8n Workflow

Import the file:

```
n8n-workflow.json
```

Workflow includes:

- **Cron / Schedule Trigger**
- **HTTP Request** node that sends WhatsApp messages via your API
- Optional: Webhook trigger

---

## API Test Example

```
POST https://your-tunnel-url/send-message
```

Body:
```json
{
  "number": "961XXXXXXXX",
  "message": "Scheduled message from n8n!"
}
```


---

## License
MIT License.
