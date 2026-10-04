# AI Trip Planner Skill

Version 1.1.0. A reusable, model-agnostic workflow for planning detailed family/group trips with Claude, ChatGPT, Gemini, or any AI tool that supports the [Agent Skills](https://agentskills.io) `SKILL.md` format.

## What it does
The planner follows **ASK → PROPOSE → CHALLENGE → REVISE → LOCK → DOCUMENT**.

It:
1. Learns the group.
2. Calibrates realistic activity ability.
3. Identifies non-negotiables and cut-first items.
4. Researches current logistics, costs, closures, reservations and weather (or flags them as unverified if the AI can't browse).
5. Builds realistic daily itineraries.
6. Stress-tests time, physical effort, kids, budget and weather.
7. Maintains a Master Trip Plan and Decision Log you can save and resume later.
8. Generates a phone-friendly itinerary (image, HTML, or text) with paid activities color-coded.
9. Captures post-trip lessons and updates your group profile for next time.

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
1. Start planning; the AI asks 3–6 questions at a time.
2. Answer conversationally and correct the Group Profile it summarizes.
3. When you approve a decision, say **“Lock that in.”**
4. Ask for the Master Trip Plan. **Save it** — paste it back into a new chat later to pick up where you left off.
5. Ask for the final graphical itinerary for the group text.
6. After the trip, share what happened; the AI separates trip-specific, group-specific and reusable lessons and gives you an updated Group Profile for next time.

## Important lesson
A statement like “we can hike for 5 hours” is not enough. The planner determines whether that means 5 hours on a maintained trail, in water, in sand, with elevation, etc. The Southern Utah example shows why activity duration must be calibrated to terrain, weather and group fatigue.

## Safety
This skill helps plan; it does not replace official safety information. Always check official sources (park flash-flood forecasts, ranger stations, permit offices, road conditions) before hazard-dependent activities.

## Repository layout
- `ai-trip-planner/SKILL.md` — core instructions (the skill entry point)
- `ai-trip-planner/templates/` — planning documents the AI fills in
- `ai-trip-planner/examples/utah-arizona-example.md` — worked example
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
