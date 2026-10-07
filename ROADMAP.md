# Roadmap — AI Trip Planner

## Current release
**v1.4.0 — Conversational planning methodology for any trip type (packaged as an Agent Skill)**

The current skill establishes the core workflow:

**ASK → PROPOSE → CHALLENGE → REVISE → LOCK → DOCUMENT**

It includes group calibration, priority management, current research, itinerary stress testing, decision locking, Master Trip Plan generation, graphical group-text itinerary generation, and post-trip learning.

---

# v2.0 direction — Know more, ask less

## Objective
**Get the most out of every trip:** find the best experiences for this group, narrow them to the strongest options, and stack them across days so each day holds as much great experience as the group's pace allows. Good food is part of the adventure, not a gap between activities.

To do that while asking less, build experienced-planner judgment into the skill so it makes good default assumptions, states them, and asks only the questions whose answers would change the plan.

"Get the most out of it" means **more value per hour, not more hours**: smart stacking, routing and timing make room for more of the best experiences, while the day-fill and rhythm rules below keep the plan realistic.

v1 asks roughly 25–30 discovery questions (7+ rounds) before the user sees anything about the destination. v2 should reach the first proposal (destination highlights) in **8 questions or fewer, over 2–3 rounds**, without losing plan quality.

## Guiding principles
1. **Ages first, then infer.** Ages and group composition imply most defaults: naps, attention span, meal timing, walking range, bedtime.
2. **State assumptions, ask for corrections.** The Group Profile shows what was *told* versus *assumed*; users fix what's wrong instead of answering everything up front.
3. **Scenarios, not self-ratings.** "Which day sounds like you?" beats six abstract pace questions.
4. **Plan to the person who tires first.** Ask who that is and when, not a capability profile per person.
5. **Ask just in time.** Ability questions (ride heights, elevation, water) are asked only when an activity needing them reaches the shortlist.
6. **Never trade away honesty.** Fewer questions must not mean silent guesses: every inference is labelled and revisitable.

## 1. Calibration redesign (v2.0)

Replace the Step 1–2 question set with a short core set:

**Round A — Who's going**
1. **Who's going?** Free text, e.g. "2 adults, kids 7 and 11, grandma 72."
2. **Whose needs set the limits?** Multi-select: young child (naps/stroller) / older or less-mobile adult / medical or accessibility need / dietary or allergy need / no one, we're all similar.

**Round B — Pace and feel**

3. **Which day sounds most like your group?**
   - A) **Full days:** out the door by 7:30 AM, 2–3 big things, back after 8:00 PM
   - B) **Steady:** out by 9:00 AM, one big thing plus one smaller one, a break from about 2:00–4:00 PM, back by 7:00 PM
   - C) **Slow mornings:** out by 10:00 AM, one main activity, pool or downtime after 3:00 PM, an early night
   - D) **Mixed:** alternate full days and recovery days

   This sets start time, activities per day, downtime, consecutive hard days, and default meal times. Always write times with AM/PM.
4. **What makes a trip day great for you?** Multi-select: big views / hands-on and interactive / animals / water / great food / thrills / history and stories / unstructured time / evening outings (sunsets, stargazing, shows, night walks).
5. **What ruins a day?** Multi-select: waiting in lines / long drives / too much walking / heat / early alarms / too many museums / crowds.

**Round C — Limits and money**

6. **One ability question that fits the trip type.** For example, outdoors: "Longest recent hike, and how did it end?" (happy / tired but fine / meltdown / someone got carried). City: "How long into a sightseeing day before someone starts to fade?"
7. **How do you feel about spending?** Value-conscious / middle of the road / splurge on the highlights / not a concern. Exact budgets come later through "help me estimate" in Step 5.
8. **How late do your evenings usually run?** E.g., back at the lodging by 7:30 PM with kids in bed by 8:00 PM / out until about 9:00 PM sometimes / late nights are fine. Ask for the kids' usual bedtime (AM/PM) when children are in the group. Combined with the evening interests in Q4, this lets the planner propose evening ideas.

Follow-up only when Q2 flags it: **What dietary needs or allergies should I plan around?**

**Cut or deferred from v1:**
- The 22-item interest menu: covered by Q4–5 and the Step 4 highlights picker.
- Meal times, snack needs and meal style: inferred from ages and pace.
- The cost-tier question: use the defaults and state them once.
- Lodging type, bases and getting around: start as Open decisions and get resolved in Step 5 with a recommendation.
- Ride heights, elevation, water, snow and museum attention span: asked in Step 6, only if relevant.

**Group Profile changes:** each line is labelled **Told me** or **Assumed** (with confidence). A later answer that contradicts an assumption is called out and the profile is updated.

## 2. Planning playbook (v2.1)

A new reference file, `references/planning-playbook.md`, holds the planner knowledge the skill applies by default instead of asking for it. The first source is the **adventure-dashboard** project's specs and engine defaults, refined by interviewing the maintainer. Contents:
- **Default profiles by group type and age band** (toddler, school-age, teens, adults only, multigenerational): walking range, attention span, nap/bedtime, meal rhythm, heat tolerance.
- **Choosing the best options (narrowing the field):**
  - Research wide before narrowing: build a long internal candidate list for each area, larger than the menu shown to the user.
  - Rank by fit to this group, quality, "only here" uniqueness (favor what they can't do at home), and value per hour (the experience relative to its total time cost, travel included). A great free experience competes equally with paid ones.
  - Cut mediocre options to make room for excellent ones: one great 3-hour experience beats two average ones plus the drive between them.
  - Present the shortlist (Step 6 menu), not the long list, with the pre-filled picks. Size it to the trip: about 2–3 options per trip day (e.g., 15–20 for a week).
- **Stacking adventures within a day:**
  - **Group by area:** same-area activities share a day; route as a line or a loop, never back and forth.
  - **Fix the hard times first:** timed entries, tours, reservations and opening-only windows go in first; everything else fills around them.
  - **Order by best time of day:** crowd-sensitive places at opening, strenuous and heat-exposed activities early, indoor or water at midday in heat, viewpoints at sunset, night-sky activities after dark.
  - **Use the drives:** put short stops along the way (viewpoints, short walks, a notable lunch) instead of making separate trips; place long drives in the heat of the day, at nap time, or right after a meal.
  - **Pair efforts:** follow a strenuous activity with an easy one, an outdoor activity with an indoor one, a long one with a short one.
  - **Keep fillers ready:** for each area, note 15–45 minute options (viewpoints, short trails, a dessert stop) to use if the day runs early or to drop if it runs late.
  - The stack still answers to the day-fill, hard-day and rhythm rules.
  - Each day carries a one-line note on why it's stacked that way (e.g., "Angels Landing at 7:00 AM before the heat and crowds; lunch in Springdale on the way to the Narrows").
- **Stacking across days:**
  - Place Musts first, each on its best day (opening days, expected weather, crowd patterns, lottery or permit dates, closeness to the base that night).
  - Fill with Wants by area, then Maybes where they fit.
  - Report what didn't fit and why ("closed every day you're in the area", "would make Day 3 a third hard day in a row"), and what it would take to fit it.
- **Meals inside the adventure:**
  - Plan meals while stacking the day, not afterwards: each meal is placed where the route already passes or where the group already is.
  - Put lunch at the hinge between the morning and afternoon adventures: before a drive, or on arrival after it, whichever keeps the day on time.
  - When "great food" is an interest, include one notable meal (lunch or dinner) most days (named and linked, with reservations on the booking checklist); otherwise use convenient, well-rated options near the route.
  - Use meals as rest: a sit-down lunch on a hard day is planned recovery; after a long or early day, dinner goes near the lodging.
  - A picnic at a scenic spot counts as both a meal and a stop.
  - Flag stretches with no food and plan packed food plus a grocery stop.
- **Day-shaping rules:** fill only part of the usable day (slack target), pace-to-capacity mapping, where meals and check-in/check-out sit, transfer-day handling. Decided so far:
  - **Day fill:** start from adventure-dashboard's range (about 64% of the usable day at the slowest pace up to 85% at the fullest) and adjust up or down from the calibration answers.
  - **Trip rhythm:** no more than 2 hard days in a row by default. The lighter day after them backs off by about 10%; it is not a day off.
  - **Ages shape the day:** ages set defaults for start time, midday break, dinner time and bedtime; the pace answer overrides.
  - **Evenings:** come from calibration (Q4 evening interests + Q8 bedtime), not a fixed rule. The planner proposes evening ideas that fit.
  - **Hard day:** a day filled to about 80% or more of the usable day, or one with an activity rated Strenuous or harder for this group.
  - **Early start → early finish:** a day that starts very early for an activity ends a little earlier.
  - **Late night → no early start:** a day that ends very late is not followed by an early start the next morning.
  - **Day-trip reach:** up to 45 minutes each way from the lodging by default; up to about 90 minutes for a Must-level activity, stated explicitly.
  - **Bases:** at least 3 nights per base before moving. Road trips are exempt: one-night stops are fine, with 2+ nights at the main destinations.
  - **Heat:** when the destination's average high for that month and elevation is about 90°F or more, finish strenuous outdoor activities by about 11:00 AM, plan indoor, water, pool or driving time from about 12:00–4:00 PM, and do easy outdoor activities in the evening. Planning uses climate averages (no forecast exists months out); the week-before check re-reads the actual forecast and swaps in the planned alternatives if needed.
  - **Crowds:** schedule the busiest Must-level places at opening or late in the day, and say why. "Busy" comes from known patterns, not a date-specific forecast: peak season, weekends and holidays, school breaks, official guidance such as "lots fill by 8:00 AM", typical busy hours by weekday, and published crowd calendars for theme parks. Labelled as an estimate.
  - **Moving days:** a drive under 2 hours is a normal day; 2 hours or more counts as a hard day. Check out after breakfast, plan activities along the route, check in from 3:00 PM.
- **Activity effort heuristics:** what makes equal distance unequal (terrain, elevation, heat, exposure, sand, water crossings, crowds, kid engagement). Decided so far (starting numbers, to be tuned from real trips):
  - **Measure effort in time, not miles:** derive the group's trail pace from their best recent hike.
  - **Climbing:** add about 30 minutes per 1,000 ft of elevation gain (a family adaptation of Naismith's rule).
  - **Terrain multipliers:** sand ×1.5; scrambling or slickrock ×1.3; wading or water crossings ×1.5; above 8,000 ft ×1.2; heat over 85°F ×1.2.
  - **Planned length:** adjusted effort time at or under the group's best recent effort, with a turnaround point and an option to extend.
- **Week-before check:** a short list the user runs about 7 days out (actual forecast, road and park alerts, lottery results, reservations) that swaps in the plan's prepared alternatives where needed.
- **Trip-type rules:** national parks, cities, theme parks, beach, road trips: what usually goes wrong and how to plan around it.
- **Booking knowledge:** high-scarcity items, typical reservation lead times by category, lottery/permit patterns.
- **Rules of thumb for what depends on what:** "rain → slot canyons off", "late arrival → drop the optional item", "group size > permit limit → split or substitute".

## 3. Effort model and stress test (v2.2)

Use the playbook to:
- Estimate activity effort beyond mileage/time (physical, logistical, transition, weather sensitivity, kid-engagement risk, recovery impact), with no extra user questions.
- Run a broader stress test that flags overpacked days, excessive consecutive effort, travel share of the day, missing recovery, fragile reservations, weather-sensitive days, budget concentration and single points of failure, each reported as **Applied** or **Needs your OK**.

---

# v3 direction — Structured state and memory (deferred)

These items were in the earlier v2 plan. They are deferred because they either add user burden or add structure that the conversational skill doesn't yet need.

- **Formal internal data model.** People → Capabilities → Preferences → Constraints → Priorities → Activities → Effort → Dependencies → Decisions → Itinerary, distinguishing facts, estimates, assumptions, preferences, decisions, dependencies and unresolved questions.
- **Per-person capability profiles.** Reusable, multi-dimension profiles (hiking, elevation, terrain, water/sand/snow, heat/cold, early mornings, driving, recovery, child fatigue). v2 plans to the person who tires first instead.
- **Formal constraint and dependency graph** for reasoning about cascading changes (v2 uses the playbook's rules of thumb).
- **Versioned family/group memory** across trips, separating stable preferences, temporary constraints, trip-specific observations and lessons awaiting confirmation. Never silently promote a one-off observation into a permanent rule.
- **Post-trip learning engine** with actual-vs-planned capture and lessons carrying evidence, confidence and approval status (v2 keeps the current Step 10).
- **Coordinated output documents** from one planning state: Master Trip Plan, concise group version, graphical itinerary, booking checklist, reservations/lottery tracker, packing prompts, weather decision matrix, post-trip lessons report.
- **Agent/IDE readiness:** machine-readable state files, validation scripts, templates and automated artifact generation for Claude Code, Codex, Cursor or similar.

---

# Proposed development sequence

### v2.0.0
Calibration redesign: the core question set, inference from ages, Told me / Assumed profile.

### v2.1.0
Planning playbook, seeded from adventure-dashboard and the maintainer interview.

### v2.2.0
Effort model and expanded stress test built on the playbook.

### v3.x
Structured state, group memory, learning engine, coordinated documents, IDE/agent deployment.

These version numbers are directional, not commitments. The roadmap should evolve as real trip planning exposes better requirements.

---

# Development rule

Do not build features merely because they sound technically interesting. Prioritize changes that solve problems encountered during real trip planning, and prefer changes that reduce what the user has to answer.

The Southern Utah / Northern Arizona worked example remains the first reference implementation and test case.
