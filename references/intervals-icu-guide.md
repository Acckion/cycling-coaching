# Connected data and calendar workflow

Tool names differ across STAS, the community Intervals MCP and future official connectors. Discover the live schemas; capability mapping below is guidance, not a list of callable functions guaranteed to exist. Use available connectors before browser automation; do not request credentials when access already works.

## Read

- STAS coaching: `get_user_summary`, then `get_trainings` for a suitable bounded history (at least 14 days for analysis; about 60 for new strategies when present). Its `newest` boundary is exclusive; for date D use D to D+1. Use selected `get_activity_detail` for a deep dive, not every activity.
- Upcoming intentions: `get_planned_events` before changing calendar sessions. Existing plans never substitute for completed activities. Respect athlete edits and current authorization; do not silently replace unrelated manual changes.
- Live thresholds: Intervals `icu_get_sport_settings` or equivalent. This is the source for configured power/HR zones; profile summaries and old activity stamps can differ.
- Current load: fitness summary or `icu_get_fitness_chart`, clearly distinguishing actual dates from future planned projections. Wellness supplies sleep/RHR/HRV context, not a substitute load series. Prefer the direct dated Intervals series if cached STAS snapshots differ and explain meaningful discrepancies.
- Completed details: activity, timer events, laps, intervals, streams and power curves. Discover the needed schema and select a bounded query. Source-derived stats may use different pause or zero-handling conventions; check before comparing.

If a tool returns an error in a fulfilled call, inspect `isError` and content rather than treating the Promise as success. On catalog-change errors rediscover and retry appropriately; never continue with an empty object as verified data. STAS responses may have structured data or text-wrapped JSON; inspect their actual shape and avoid dumping private raw records unnecessarily.

## Interpret

Separate source provenance (power sensor vs estimated), actual execution, model estimates, coach inference and user report. Retain the athlete's current availability and goals. If a plan says SS but actual intensity/rep structure does not support it, do not count it as delivered SS. Do not rewrite completed activity intervals, historical power or wellness merely to make a comparison look consistent.

## Write only authorized changes

1. Read target-week events and exact target event(s). Identify duplicates and existing alternative dates; schedule one ride, not two copies of an either/or choice.
2. Snapshot existing event payload locally without secrets before modifying it. Preserve unrelated dates/times, fields, events and manual edits. A newly discovered change outside the agreed scope is not implied permission to overwrite it.
3. Create or update only intended fields with [workout text](intervals-icu-workout-format.md). Use the platform event ID when replacing an existing session. Respect the athlete profile's local timezone rather than the execution host's clock. Do not assume a default calendar time is the athlete's actual availability.
4. Read back title, start/end date, duration, description and parsed structure where available. Verify repeat counts and total duration. Check recalculated planned load; a stale explicit load override may not reflect changed work. Use a forecast, if available, to show the effect of the changed week without claiming it is guaranteed.
5. On an ambiguous write/timeout, read the event or target calendar before retrying. Repair a demonstrated mismatch within scope; stop repeated uncertain mutations and report the unverified part.

Writing plans does not authorize changing FTP, zones, profile, historic power or external messaging. A skill should use authorization already in the conversation rather than repeatedly asking for the same approval. State which events changed and what was verified; do not claim writes on a proposal-only response.
