# Roadmap — AI Trip Planner

## Current release
**v1.1.0 — Conversational planning methodology (packaged as an Agent Skill)**

The current skill establishes the core workflow:

**ASK → PROPOSE → CHALLENGE → REVISE → LOCK → DOCUMENT**

It includes group calibration, priority management, current research, itinerary stress testing, decision locking, Master Trip Plan generation, graphical group-text itinerary generation, and post-trip learning.

---

# v2.0 direction — Structured trip-planning intelligence

## Objective
Turn the conversational methodology into a more explicit planning system that an AI agent can reason over consistently across long, complex trips and eventually across multiple trips for the same family/group.

## 1. Formal internal data model

Represent the planning state explicitly as:

**People → Capabilities → Preferences → Constraints → Priorities → Activities → Effort → Dependencies → Decisions → Itinerary**

The model should distinguish:
- facts
- estimates
- assumptions
- preferences
- decisions
- dependencies
- unresolved questions

This should reduce loss of context during long planning sessions and make revisions more reliable.

## 2. Group capability model

Move beyond simple hiking-distance questions toward reusable capability profiles. Examples:
- hiking distance/duration
- elevation tolerance
- technical terrain
- water/sand/snow
- heat/cold
- early-morning tolerance
- driving tolerance
- consecutive hard-day recovery
- child fatigue behavior

The model should support different people having different capabilities.

## 3. Activity effort model

Create a repeatable way to estimate activity burden using more than official mileage/time. Potential dimensions:
- physical effort
- logistical effort
- travel burden
- transition burden
- weather sensitivity
- kid-engagement risk
- recovery impact

The goal is to make statements like “3 miles in a slot canyon” and “3 miles on a flat paved trail” meaningfully different to the planner.

## 4. Constraint and dependency graph

Represent relationships such as:
- lottery won → activity available
- high river level → waders recommended
- rain → slot canyon unsafe
- late arrival → optional activity removed
- group size > permit limit → split activity or select alternative

This would allow the agent to reason about cascading itinerary changes.

## 5. Automated itinerary stress testing

Add a formal stress-test pass that can score or flag:
- overpacked days
- unrealistic transitions
- excessive consecutive effort
- fragile reservations
- weather-sensitive activities
- insufficient recovery
- budget concentration
- single points of failure

## 6. Versioned family/group memory

Maintain reusable profiles across trips, while separating:
- stable preferences
- temporary constraints
- trip-specific observations
- lessons awaiting confirmation

The system should never silently promote a one-off observation into a permanent family rule.

## 7. Post-trip learning engine

Capture actual-vs-planned results and generate candidate lessons such as:
- activity duration was underestimated
- kids tolerated more/less elevation than expected
- meals needed more time
- early starts were unpopular
- scenic drives were highly valued

Each lesson should have evidence, confidence and approval status.

## 8. Improved artifact generation

Eventually generate a coordinated package:
- Master Trip Plan
- concise family/group version
- graphical itinerary
- booking checklist
- reservations/lottery tracker
- packing prompts
- weather decision matrix
- post-trip lessons report

All artifacts should derive from the same structured planning state.

## 9. Agent/IDE readiness

Once the internal data model is stable, create a deployment-oriented version for Claude Code, Codex, Cursor or similar environments. This may include machine-readable state files, validation scripts, templates and automated artifact generation.

---

# Proposed v2 development sequence

### v2.0.0
Formalize the internal data model and structured state.

### v2.1.0
Add group capability and activity-effort models.

### v2.2.0
Add dependency/constraint graph and formal itinerary stress testing.

### v2.3.0
Add reusable family/group memory and actual-vs-planned learning.

### v2.4.0
Unify artifact generation from structured state.

### v2.5.0+
Optimize deployment for AI IDEs/agents and automate validation where practical.

These version numbers are directional, not commitments. The roadmap should evolve as real trip planning exposes better requirements.

---

# Development rule

Do not build v2 features merely because they sound technically interesting. Prioritize changes that solve problems encountered during real trip planning.

The Southern Utah / Northern Arizona worked example remains the first reference implementation and test case.
