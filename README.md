# Sloth Desk

Paste any message you'd rather ignore (email, text, bill, school notice). Get what it is, what you must do, and a ready-to-send reply. Runs fully on your computer with an open-weight model. No account, no API key, no cost per use.

## Run it

1. Install [Ollama](https://ollama.com).
2. Pull a model: `ollama pull gemma3:4b`
3. Allow the page to talk to Ollama, then start it:
   - macOS/Linux: `OLLAMA_ORIGINS="*" ollama serve`
   - Windows (PowerShell): `$env:OLLAMA_ORIGINS="*"; ollama serve`
4. Open `index.html` in your browser.

If the status line says it can't reach Ollama, step 3 is almost always the reason.

## How it works

One HTML file, no dependencies, no build step. It sends your message to the local Ollama API (`localhost:11434`) with a system prompt that asks for structured JSON: what the message is, urgency, actions with deadlines, and a draft reply. The page then renders it. Nothing is stored except your last-used model name, in the browser.

## Limits

- Small models can misread messages. It is told never to invent dates or amounts, but always check against the original.
- Not for legal, medical or financial decisions.
- Text only. Images and PDFs are not supported yet.

## License

MIT. Built for the DEV Hacktoberfest Open-Source AI Challenge.
