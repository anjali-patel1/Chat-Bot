# ChatBot — React + Vite

A chatbot UI built with React 19 and Vite. It communicates with an external AI API (configured via environment variable) and renders a floating popup-style chat interface.

---

## Project Structure

```
src/
├── App.jsx                    # Root component — manages chat history & API calls
├── main.jsx                   # React entry point
├── index.css                  # Global styles (Inter font, purple theme)
└── components/
    ├── ChatbotIcon.jsx        # Bot avatar SVG icon
    ├── ChatForm.jsx           # Message input form
    └── ChatMessage.jsx        # Individual message bubble (user / bot)
```

---

## Tech Stack

| Tool | Version |
|------|---------|
| React | ^19.1.0 |
| React DOM | ^19.1.0 |
| Vite | ^6.3.5 |
| ESLint | ^9.25.0 |

---

## Getting Started

### Prerequisites

- Node.js
- npm or yarn

### Install

```bash
npm install
```

### Environment Variable

Create a `.env` file in the root and add your API endpoint:

```env
VITE_API_URL=your_api_endpoint_here
```

The app sends chat history to this URL using a `POST` request with `{ contents: [...] }` as the body and expects a Google Gemini-compatible response format.

### Run Dev Server

```bash
npm run dev
```

### Build

```bash
npm run build
```

### Preview Production Build

```bash
npm run preview
```

### Lint

```bash
npm run lint
```

---

## How It Works

1. The user types a message in `ChatForm` and submits.
2. The message is added to `chatHistory` in `App.jsx`.
3. A `"Thinking..."` placeholder is shown for the bot.
4. `generateBotResponse` sends the full chat history to `VITE_API_URL`.
5. The bot's response replaces the placeholder. Markdown bold (`**text**`) is stripped from the response before display.

---

## UI

- Floating popup (420px wide) centered on screen
- Purple header (`#6D4FC2`) with bot icon and collapse button
- Scrollable chat body (460px height)
- Sticky input footer with send button that appears only when text is present
- Bot messages — light purple bubble, left-aligned
- User messages — purple bubble, right-aligned
- Font: Inter (Google Fonts)
- Icons: Material Symbols Rounded (Google Fonts)
