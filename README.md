# Sloth Desk

Paste a message you don't want to deal with (an email, a college notice, a landlord's text, a bill) and get a short checklist of what you need to know and do, with every date, time, amount, file requirement and place.

Runs fully on your own computer with a local open-weight model (Gemma 3 4B via Ollama). Nothing is uploaded anywhere.

![Placement notice](screenshots/placement.png)
![Rental message](screenshots/rental.png)

## How to run

1. Install [Ollama](https://ollama.com) and pull the model:
   ```
   ollama pull gemma3:4b
   ```
2. Download `index.html` from this repo.
3. In the folder with `index.html`, serve it (do not double-click it, browsers block it from reaching Ollama):
   ```
   python -m http.server 8000
   ```
4. Open `http://localhost:8000/index.html`, paste a message, click **Decode it**.

If the page says it can't reach Ollama, either use step 3 as written, or set `OLLAMA_ORIGINS=*` and restart Ollama.

## How it works

- Calls Ollama's `/api/chat` with strict JSON output and temperature 0.
- A worked example in the prompt teaches the format.
- A code check scans your message for dates, times, amounts, sizes and file formats, confirms each appears in the output, and retries once if something was dropped.

## Limits

A 4B model misses a small share of details (mostly places, items to bring and contacts, which the check can't verify), and sometimes adds a filler line. Always check the original for anything that matters. You can pick a larger model from the dropdown.

## License

MIT
