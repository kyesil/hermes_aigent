# hermes_aigent
Hermes Ai Agent Basic Configs. Telegram, Dashboard.

# Hermes Agent Docker Compose Setup

This repository provides a simple Docker Compose setup for running **Hermes Agent** with:

* OpenAI as the main model provider
* Hugging Face as a fallback provider
* Telegram messaging enabled
* Hermes Dashboard enabled with Basic Auth
* Persistent local data storage

## Requirements

* Docker
* Docker Compose
* OpenAI API key
* Telegram Bot Token
* Optional: Hugging Face token for fallback provider

## Files

Create the following files:

```text
.
├── compose.yml
└── .env
```

## .env.example

Create a `.env` file based on the example.env below.


## Telegram User IDs

`TELEGRAM_ALLOWED_USERS` must contain Telegram numeric user IDs, not usernames.

Example:

```env
TELEGRAM_ALLOWED_USERS=123456789,987654321
```

For Telegram groups or supergroups, use the numeric chat ID.

Example:

```env
TELEGRAM_GROUP_ALLOWED_CHATS=-1001234567890
```

## Start Hermes Agent

Run:

```bash
docker compose up -d
```

Check logs:

```bash
docker logs -f hermes
```

## Access the Dashboard

Open:

```text
http://localhost:9119
```

Login with:

```text
Username: value of HERMES_ADMIN_USER
Password: value of HERMES_ADMIN_PASSWORD
```

## Gateway API

The gateway API is available at:

```text
http://localhost:8642
```

## Stop Hermes Agent

```bash
docker compose down
```

## Remove Local Data

Hermes data is stored in:

```text
./hermes_data
```

To remove all local data:

```bash
docker compose down
rm -rf ./hermes_data
```

## Security Notes

Do not commit your `.env` file to GitHub.

Add this to `.gitignore`:

```gitignore
.env
hermes_data/
```

Keep API keys, bot tokens, and dashboard passwords only in environment variables.

Avoid placing secrets directly inside `compose.yml`.

If exposing the dashboard or gateway to the internet, use HTTPS and a reverse proxy.
