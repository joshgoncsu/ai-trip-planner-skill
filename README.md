# AI Trip Planner Skill

Version 1.3.0. A reusable, model-agnostic workflow for planning detailed family/group trips of any kind (sightseeing and landmarks, cities, national parks and outdoors, beach, theme parks, road trips) with Claude, ChatGPT, Gemini, or any AI tool that supports the [Agent Skills](https://agentskills.io) `SKILL.md` format.

## What it does
The planner follows **ASK → OFFER OPTIONS → USER CHOOSES → DRAFT → CHALLENGE → REVISE → LOCK → DOCUMENT**.

It:
1. Learns the trip type, the group, what they love and dislike, budget, pace and realistic ability, in short rounds of at most 4 questions with clickable or lettered answers. “Not sure” is always an acceptable answer.
2. Tracks open decisions and comes back to each one with options and a recommendation.
3. Shows quick destination highlights so you can say what appeals before detailed research.
4. Compares logistics options: airport, bases, lodging type, rental car vs. transit.
5. Presents an activity menu with links and pre-filled recommended picks (Must / Want / Maybe / Skip); you accept or change them in one line before any itinerary is built.
6. Researches current hours, tickets, reservations, closures and weather, or flags them as unverified if the AI can't browse.
7. Builds a realistic day-by-day itinerary and a one-page **DRAFT** visual of it right away.
8. Stress-tests time, effort, kids, budget and weather.
9. Makes it obvious when your input is needed, with recommendations you can accept in a word.
10. Maintains a Master Trip Plan and Decision Log you can save and resume later.
11. Produces a final one-page visual itinerary (PNG, HTML, or text) with paid activities color-coded.
12. Captures post-trip lessons and updates your group profile for next time.

## Install

Download the repository from [github.com/joshgoncsu/ai-trip-planner-skill](https://github.com/joshgoncsu/ai-trip-planner-skill) (**Code → Download ZIP**), or clone it:

```bash
git clone https://github.com/joshgoncsu/ai-trip-planner-skill.git
```

The skill is the [`ai-trip-planner/`](ai-trip-planner/) folder. Always use the **whole folder**: `SKILL.md` refers to the templates and example inside it.

### Claude Code
Copy the folder into your skills directory:
- Personal (all projects): `~/.claude/skills/ai-trip-planner/`
- One project: `.claude/skills/ai-trip-planner/`

Then just ask: “Help me plan a family trip to Yellowstone.”

### Claude.ai (web / desktop / mobile)
Zip the `ai-trip-planner` folder (the zip should contain the folder, with `SKILL.md` inside it) and upload it under **Settings → Capabilities → Skills**.

### Other skill-compatible tools (Codex, Gemini CLI, Cursor, etc.)
Place the folder wherever the tool loads Agent Skills from; see that tool's documentation.

### ChatGPT, Gemini, or any chat app without skill support
Upload every file in `ai-trip-planner/` (SKILL.md, all of `templates/`, and `examples/`) as Project files, Custom GPT knowledge, or Gem files, then use the starter prompt in [`docs/using-with-ai-assistants.md`](docs/using-with-ai-assistants.md).

## Using it
1. Start planning; the AI asks up to 4 questions at a time. Click answers where your app supports it, or reply in shorthand like “1B 2A”. “Not sure” is a fine answer.
2. Answer conversationally and correct the Group Profile it summarizes.
3. Tick the destination highlights that appeal, then review the activity menu's pre-filled picks and accept or change them (e.g., “Accept, but 9 → Skip”). You can always say “go with your recommendations.”
4. A “yes” records a decision as agreed. When you want it fixed, say **“Lock that in.”**
5. Ask for the Master Trip Plan. **Save it** — paste it back into a new chat later to pick up where you left off.
6. You'll get a DRAFT one-page visual with the first itinerary; the final one comes after you lock the plan.
7. After the trip, share what happened; the AI separates trip-specific, group-specific and reusable lessons and gives you an updated Group Profile for next time.

## Important lesson
Statements like “we can hike for 5 hours” or “the kids love museums” are not enough. The planner asks about real past experience: 5 hours on a maintained trail is very different from 5 hours in a river, and “loves museums” may mean 2 hours, not a full day. The two worked examples (Southern Utah outdoors, Washington DC city) show how ability is calibrated for different trip types.

## Safety
This skill helps plan; it does not replace official safety information. Always check official sources (park and venue alerts, weather services, ranger stations, road conditions) before hazard-dependent activities.

## Repository layout
- `ai-trip-planner/SKILL.md` — core instructions (the skill entry point)
- `ai-trip-planner/templates/` — planning documents the AI fills in
- `ai-trip-planner/examples/` — worked examples (outdoor trip and city trip)
- `docs/` — usage guide for chat apps
- `CHANGELOG.md` — methodology changes by version
- `ROADMAP.md` — planned v2 direction

## Contributing lessons
Trip observations aren't automatically turned into global rules. They are classified first:
- Trip-specific
- Group-specific
- General/reusable

If you find a general lesson that would improve the skill, [open a GitHub issue](https://github.com/joshgoncsu/ai-trip-planner-skill/issues) with the observation and evidence. Approved lessons are added with a version bump and a changelog entry.

## Future development
See `ROADMAP.md` for the planned v2 evolution toward a structured trip-planning intelligence model and AI-IDE/agent deployment.

## License
MIT — see [LICENSE](LICENSE).
