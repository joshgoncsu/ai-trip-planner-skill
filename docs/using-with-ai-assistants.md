# Using with ChatGPT, Gemini, or other chat apps

Tools with native skill support (Claude Code, Claude.ai, and other Agent Skills–compatible tools) load the skill automatically — see the README's Install section. This guide is for chat apps without skill support.

## Setup
1. Create a persistent Project / Custom GPT / Gem if your app supports one.
2. Upload **all** files from `ai-trip-planner/`: `SKILL.md`, every file in `templates/`, and both files in `examples/`.
3. If your app only accepts instructions text (no files), paste the contents of `SKILL.md` as the instructions; it still works, just without the templates.
4. Turn on web browsing if available, so the AI can check current hours, prices and permits.

## Starter prompt

> Use the attached AI Trip Planner skill (SKILL.md) to plan my trip, following its workflow step by step. Ask at most 4 questions at a time, one thing each, with lettered options so I can answer like “1B 2A”, and tell me “not sure” is an OK answer. Show me destination highlights early, then an activity menu with links and your pre-filled picks that I can accept or change before you build any itinerary. End each reply with a clear “Your input needed” list. Only lock decisions when I say “lock that in.” Once there's a draft itinerary, make a one-page visual of it.

## Resuming a trip later
Paste or attach your saved Master Trip Plan and say:

> Here is my saved Master Trip Plan. Continue planning from where we left off. Keep all LOCKED decisions.
