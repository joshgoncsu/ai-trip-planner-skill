# Itinerary Graphic Specification
Purpose: phone-friendly itinerary for group text.

Required:
- title
- date for every day
- destination/base
- major activities
- approximate timing when useful
- optional labels
- cost legend
- color highlight for paid activities

Cost colors (defaults; use the user's tiers if they set their own):
| Tier | Per person | Color | Text-only marker |
|---|---|---|---|
| FREE / INCLUDED | — | No highlight | (none) |
| $ | Under $25 | Green | 🟢 |
| $$ | $25–$75 | Orange | 🟠 |
| $$$ | Over $75 | Red | 🔴 |

Output format, best available first:
1. Image with accurate, legible text.
2. Self-contained HTML page: inline CSS only, single narrow column (max-width ~420px), large readable text, no external files.
3. Plain text with the emoji markers above, short enough to paste into a group text.

Rules:
- Use the latest Master Trip Plan.
- Never invent activities or prices.
- Do not call ordinary park hikes paid merely because park admission exists.
- Keep text short and readable on a phone.
- Regenerate whenever the itinerary changes.
