# Using with ChatGPT, Gemini, or other chat apps

Tools with native skill support (Claude Code, Claude.ai, and other Agent Skills–compatible tools) load the skill automatically — see the README's Install section. This guide is for chat apps without skill support.

## Setup
1. Create a persistent Project / Custom GPT / Gem if your app supports one.
2. Upload **all** files from `ai-trip-planner/`: `SKILL.md`, every file in `templates/`, and `examples/utah-arizona-example.md`.
3. If your app only accepts instructions text (no files), paste the contents of `SKILL.md` as the instructions; it still works, just without the templates.
4. Turn on web browsing if available, so the AI can check current hours, prices and permits.

## Starter prompt

> Use the attached AI Trip Planner skill (SKILL.md) to plan my trip. Start conversational discovery. Ask 3–6 questions at a time. Do not build the final itinerary until you understand our group, activity capability, priorities, budget, pace and constraints. Research current information where appropriate. Challenge unrealistic assumptions. Lock decisions explicitly. Maintain a Master Trip Plan and, once stable, generate a phone-friendly graphical itinerary with paid activities color-coded.

## Resuming a trip later
Paste or attach your saved Master Trip Plan and say:

> Here is my saved Master Trip Plan. Continue planning from where we left off. Keep all LOCKED decisions.
