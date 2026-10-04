# Changelog

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
