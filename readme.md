# WhatsApp Chatbot with n8n

A WhatsApp chatbot implementation using n8n workflow automation platform integrated with Google Gemini AI. This project allows you to receive WhatsApp messages through a webhook, process them with AI, and respond back to users.

## Project Overview

This project creates an AI assistant named "Jenny" that can respond to WhatsApp messages. The system:

1. Receives incoming WhatsApp messages through a webhook
2. Processes the message content with Google Gemini AI
3. Formats the AI response as JSON
4. Sends the response back to the user via WhatsApp

## Setup Requirements

- Docker and Docker Compose
- n8n account
- Google Gemini API credentials
- WhatsApp Business API integration (via SatuConnect API)
- ngrok or similar service for webhook exposure

## Project Structure

```
├── docker-compose.yml          # Docker configuration for n8n
├── readme.md                   # This documentation file
└── Whatsapp Chatbot/           # Main project folder
    ├── code json formater.txt  # JSON formatting code
    ├── system message.txt      # AI system instructions
    └── Whatsapp_Chatbot.json   # n8n workflow definition
```

## Installation & Setup

1. Clone this repository to your local machine
2. Configure your Google Gemini API credentials in n8n
3. Update the webhook URL in `docker-compose.yml` to match your ngrok or public URL
4. Update the WhatsApp API token in the workflow

### Running the Application

```bash
# Start the n8n service
docker-compose up -d
```

The n8n service will be available at http://localhost:80

## How It Works

1. A webhook receives incoming WhatsApp messages
2. Messages are filtered and validated
3. The user's message is sent to Google Gemini AI with specific formatting instructions
4. The AI response is parsed and formatted as JSON
5. The formatted response is sent back to the user via the WhatsApp API

## Workflow Details

The n8n workflow consists of these key components:

- **Webhook**: Receives incoming messages
- **Filter**: Validates incoming message format
- **Edit Fields**: Extracts message content and sender info
- **AI Text to JSON**: Processes the message with Google Gemini AI
- **Code**: Formats and cleans the AI response
- **HTTP Request**: Sends the response back to WhatsApp

## Configuration

### Environment Variables

In `docker-compose.yml`:
- `N8N_HOST`: Host configuration for n8n
- `N8N_PROTOCOL`: Protocol for n8n (http/https)
- `WEBHOOK_URL`: Your public webhook URL for receiving WhatsApp messages

### API Keys

You'll need to configure:
- Google Gemini API credentials in n8n
- WhatsApp API authorization token in the HTTP Request node

## Customization

To modify the AI assistant's behavior, edit the system message in the `system message.txt` file or directly in the workflow's "AI Text to JSON" node.

## Troubleshooting

- Ensure your webhook URL is publicly accessible
- Check that API credentials are correctly configured
- Verify the WhatsApp Business API integration is working
- Look at n8n execution logs for detailed error information

## Author

Andi Wibowo