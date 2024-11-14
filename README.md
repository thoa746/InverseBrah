
# Inversebrahai AI

InverseBrahAI AI is a version of InverseBrah on X, forked from AI16z's Eliza.

## Features

-   🛠 Full-featured Discord, Twitter (X), and Telegram connectors
-   👥 Multi-agent and room support
-   📚 Easily ingest and interact with your documents
-   💾 Retrievable memory and document store
-   🚀 Highly extensible - create your own actions and clients to extend capabilities
-   ☁️ Supports many models, including local Llama, OpenAI, Anthropic, Groq, and more
-   📦 Just works!

## Use Cases

-   🤖 Chatbots
-   🕵️ Autonomous Agents
-   📈 Business process handling
-   🎮 Video game NPCs

# Getting Started

**Prerequisites (MUST):**
    
-   [Python 2.7+](https://www.python.org/downloads/)
-   [Node.js 23.1+](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm)
-   [pnpm](https://pnpm.io/installation)

### Configure the .env file

-   Copy .env.example to .env and fill in the appropriate values
-   Update the TWITTER environment variables with your bot's username and password

### Configure the character file

-   Review `src/core/defaultCharacter.ts` for customization
-   Optionally, load characters with `pnpm start --characters="path/to/your/character.json"` to run multiple bots.

After configuring .env and character files, start the bot:

```
pnpm i
pnpm start
```

# Customizing Inversebrahai AI

### Adding custom actions

To prevent conflicts, add custom actions in a `custom_actions` directory and include them in `inversebrahaiConfig.yaml`. Refer to `inversebrahaiConfig.example.yaml` for guidance.

## Using Different Models

### Llama

Use Llama 70B or 405B by setting `XAI_MODEL` to `meta-llama/Meta-Llama-3.1-70B-Instruct-Turbo` or `meta-llama/Meta-Llama-3.1-405B-Instruct`.

### Grok

Run Grok models by setting `XAI_MODEL` to `grok-beta`.

### OpenAI

Set `XAI_MODEL` to `gpt-4o-mini` or `gpt-4o` to use OpenAI models.

## Additional Requirements

If startup errors occur, try installing Sharp:

```
pnpm install --include=optional sharp
```

# Environment Setup

Define necessary variables in .env:

```
# Required
DISCORD_APPLICATION_ID=
DISCORD_API_TOKEN=
OPENAI_API_KEY=sk-*

# ELEVENLABS SETTINGS
ELEVENLABS_MODEL_ID=eleven_multilingual_v2

TWITTER_USERNAME=
TWITTER_PASSWORD=
TWITTER_EMAIL=

XAI_API_KEY=
XAI_MODEL=

# Claude
ANTHROPIC_API_KEY=

WALLET_PRIVATE_KEY=EXAMPLE_WALLET_PRIVATE_KEY
BIRDEYE_API_KEY=
```

# Local Inference

### CUDA Setup

If you have an NVIDIA GPU, install CUDA to enhance performance.

```
pnpm install
npx --no node-llama-cpp source download --gpu cuda
```

Ensure CUDA Toolkit with cuDNN and cuBLAS is installed.

### Running Locally

Set `XAI_MODEL` to a Llama option, leave `X_SERVER_URL` and `XAI_API_KEY` blank to download the model from huggingface for local use.

# Clients

## Discord Bot

For Discord Bot setup, visit: https://discordjs.guide/preparations/setting-up-a-bot-application.html

# Development

## Testing

To run tests:

```bash
pnpm test           # Run tests once
pnpm test:watch     # Watch mode
```

For database tests:

```bash
pnpm test:sqlite    # SQLite tests
pnpm test:sqljs     # SQL.js tests
```

Tests use Jest, located in `src/**/*.test.ts`, configured to load `.env.test`, with a 2-minute timeout.

