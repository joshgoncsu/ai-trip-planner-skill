# Changelog

## 1.4.0 — Realistic day timing and smarter meals
Adapted from the rules-based scheduling in a companion trip-planner project:
1. New **Day timing** section in SKILL.md, applied whenever a day is drafted, revised or stress-tested.
2. Every travel leg gets a +10% buffer; every drive also gets parking/walk-in time at both ends (5 / 10–15 / 20–30 min defaults by site type), with arrive-by times for lots that fill early.
3. Arrival and departure times are asked in Step 1. Day 1 starts after bags, rental pickup and transfer; the last day ends before airport buffer, rental return and transfer. Unknown times become PLACEHOLDERs.
4. Opening hours are checked against each scheduled date: day-of-week and seasonal closures, holidays, last entry, shuttle last-return. Unstated hours are never assumed open, and hours are re-checked when an activity moves to another day.
5. Meals are planned around the group's own rhythm and the shape of each day (picnic on trail days, eat at the venue, early dinner after long days), with duration by meal style, travel to the restaurant, snack breaks, remote-area food warnings, and a named meal that flexes when the day runs late. Restaurants are named only where it matters; reservation-needed ones go on the booking checklist.
6. Intake, Group Profile and Master Trip Plan templates gained meal and travel-day fields; Step 8 stress test checks all of the above.

## 1.3.0 — Easier answering and earlier interest check
Based on a full test run (a family trip to Washington, DC):
1. At most 4 questions per reply, one thing per question, each with lettered options and “Not sure”; shorthand answers like “1B 2A” are invited.
2. Uses the platform's clickable multiple-choice question tool when available (e.g., in Claude Code), with the recommended option first.
3. The past-trips question is split into “what did the family love?” and “what did the family dislike?”
4. New Step 4, destination highlights: 8–12 headline experiences right after the Group Profile so the user can say what appeals before detailed research. Later steps renumbered (now 10 steps).
5. The activity menu has a pre-filled “My pick” column; the user can accept with changes in one line, use shorthand, or click through by category.

## 1.2.0 — Any trip type, user-chosen activities, clearer decisions
Based on a full test run (a family trip to Yosemite):
1. Works for any trip type (sightseeing/landmarks, city, outdoors, beach, theme parks, road trips); ability questions now match the trip instead of always asking about hiking.
2. Discovery asks about lodging type (hotel, vacation rental, cabin, camping, etc.) and how the group will get around (rental car, own car, transit, mix).
3. “Not sure” is always acceptable; undecided items go on an Open decisions list and are resolved later with options and a recommendation.
4. Budget is asked in a defined form (total vs. per person per day; whether flights/lodging are included) or “help me estimate.”
5. Removed questions that assume the user knows the destination (e.g., naming the hardest hike); effort ladders in the activity menu replace them.
6. New Step 5 activity menu (`templates/activity-menu.md`): the user marks options Must / Want / Maybe / Skip before any itinerary is drafted.
7. Every reply that needs the user ends with a “Your input needed” list with recommendations; stress-test items are labeled Applied or Needs your OK.
8. A one-page DRAFT visual itinerary is produced with the first draft, regenerated on revisions; tested PNG rendering via headless Chrome/Edge.
9. Every proposed activity, lodging and booking item includes its own link; only URLs actually retrieved may be used.
10. Decisions are AGREED on a “yes” and LOCKED only when the user explicitly locks them; unconfirmed details are labeled PLACEHOLDER.
11. Added a Washington, DC worked example for a city/landmark trip.

## 1.1.0 — Packaging for public release
Methodology unchanged; packaging and portability improvements:
1. Added Agent Skills frontmatter (`name`, `description`) to SKILL.md so it loads as a skill.
2. Moved the skill into the `ai-trip-planner/` folder; repository docs stay at the root.
3. SKILL.md now points to each template and the worked example at the step that uses it.
4. Merged the `workflows/` phase files into SKILL.md and removed the duplicates; removed MANIFEST.md.
5. Defined default cost tiers ($ / $$ / $$$) and their colors.
6. Added output fallbacks for the graphical itinerary (image → HTML → text).
7. Added a no-browsing fallback: unverifiable facts are marked UNVERIFIED.
8. Added saving/resuming instructions for the Master Trip Plan.
9. Added safety guidance to defer go/no-go calls to official sources.
10. Post-trip learning now updates the user's own Group Profile; skill changes are suggested to maintainers instead.
11. Added MIT LICENSE and per-platform install instructions.

## 1.0.0 — Initial reusable workflow
Created from the Southern Utah / Northern Arizona planning project.

Initial lessons incorporated:
1. Hiking duration must be calibrated to terrain and group context.
2. River/sand/snow mileage can be much harder than maintained-trail mileage.
3. Maximum duration should not automatically become planned duration.
4. Flexible turnarounds can be better than fixed distance targets.
5. Consecutive hard days need explicit stress testing.
6. Non-negotiables need a cut hierarchy.
7. Lottery-dependent activities need real alternatives.
8. Park admission and activity-specific fees must not be conflated.
9. Detailed Master Trip Plans and concise graphical group itineraries serve different purposes.
10. Post-trip observations should be classified before changing the reusable methodology.
