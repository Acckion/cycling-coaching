# Longitudinal coaching: activity, week and month

Use the connected training platform as the durable coaching record across chats and devices. The skill supplies the workflow; Intervals.icu user notes hold the athlete profile and current coach journal in separate owned sections, while activity notes and weekly calendar summaries hold detailed evidence. Do not store live FTP, recovery, load, routes, availability or health context as skill defaults. Do not create an automation or claim unattended monitoring unless the user requests one and it is actually configured.

## Post-ride closed loop: review, decide, apply, verify

For each substantive ride review, determine both what this ride delivered and what it changes for subsequent training. Use the five elements below as an internal decision workflow. Distill the activity note to the few conclusions worth remembering rather than copying every element or every checked field.

1. **本次结论** — Compare the intended purpose with actual execution: completion, sustained stimulus, strengths and shortcomings. Separate observed performance from expected adaptation; a single ride cannot establish an exact VO₂max or FTP gain.
2. **关键证据** — Use only decision-relevant measured work, interval duration, target-range time, rep fade, HR/cadence response and athlete feedback. Respect pauses, traffic, source quality and missingness. Keep main-set RPE separate from session RPE and feeling.
3. **后续影响** — Explain recovery demand, whether this supports progression, and any dated limiter hypothesis. Combine recent actual CTL/ATL/Form trends, delivered dose, sleep/recovery and subjective response. Positive Form or absence of soreness alone is not permission to escalate; one poor ride is not proof of lost fitness. State uncertainty and the observation needed to resolve it.
4. **计划决定** — Explicitly choose 保持 / 加量 / 减量 / 改课 / 延后. Name the affected upcoming session(s), reason and concrete change (duration, work reps, target power zone/subrange, recovery or spacing). 保持原计划 is a valid explicit decision. Usually review the next 3–7 days first; alter the wider block only when repeated evidence or a material constraint warrants it. Progress one main variable at a time and preserve the athlete’s available time and current goal.
5. **落实与复查** — Record the decision and define the next verification: which session/date or trigger, what comparable execution/recovery evidence to assess, and whether it supports retaining or revising the decision. At the next relevant review, revisit the previous prediction and record whether it was supported, contradicted or still uncertain.

### Apply justified changes to the calendar

Before changing a workout, retrieve the existing upcoming calendar and its current prescription, identify the exact event/date, and check spacing and actual versus projected load. Apply justified changes only when the current request or independent athlete profile grants standing authorization. Do not extend that authorization to unrelated events, profile/threshold changes or another athlete. If essential readiness feedback is missing, keep dependent changes pending and state the condition; do not invent feedback.

Preserve a recoverable before-state and unrelated event fields. Validate the changed workout’s total duration, power-zone targets and work/recovery structure, save, and read back the event. Update the same event where supported; an ambiguous timeout requires retrieval before retry. Do not duplicate sessions or silently shift dates. Follow connector requirements and any applicable approval rules.

When a future workout actually changes, mention the affected date and the new prescription in one concise sentence. Do not write routine statuses such as `无需修改`, before/after audit trails or verification mechanics into the activity note. If a write fails, tell the user in chat and provide the proposed replacement; do not turn the failed operation into durable coaching content. Reflect material week/block changes in the current journal and relevant weekly note without duplicating the full activity analysis.

This skill update itself does not call for changing today’s actual workouts or populating past logs.

## Durable records and cross-chat recovery

| Record | Canonical destination | Update when | Content |
|---|---|---|---|
| Athlete profile | Athlete profile section in Intervals.icu user notes | Confirmed durable changes | Background, goals, preferences, sustainable availability, equipment and authorization |
| Coach journal | Coach journal section in the same Intervals.icu user notes | Material feedback, corrections or decisions | Updated-at date, current phase, capability evidence, active limiters, decisions and reasons, temporary constraints and review dates, open questions and intake progress |
| Activity review | Coach section in the corresponding completed activity | Substantive review | Delivered work, athlete response, interpretation and next action |
| Weekly summary | Corresponding weekly calendar NOTE | Week review or planning | Covered dates, actual dose, execution, recovery and next priorities |
| Monthly summary | Separate month-labeled section within the weekly NOTE containing the month's last calendar day | Monthly review | Natural-month evidence, trends, conclusions and direction |

Use the athlete's local week convention and preserve existing weekly event identity. A cross-month week's weekly totals and the natural month's totals have separate explicit date ranges. Label incomplete summaries provisional. Update the same weekly NOTE while preserving its other sections. Existing separate historical monthly notes remain valid evidence; migration or deletion requires authorization.

The coach journal carries current state. Keep it concise and replace superseded conclusions; retain dated material direction changes with evidence links. Resolve expired temporary constraints, preserve unresolved questions and record which intake answers are already known. Keep detailed historical evidence in activity and weekly/monthly notes.

## Read before coaching

1. Read the athlete profile and coach journal from Intervals.icu user notes at the start of a chat and before consequential training decisions. Follow applicable connector retrieval requirements.
2. Read relevant weekly/monthly sections and key activity notes, then refresh current thresholds/zones, actual training and load, recovery and future sessions. Read new activity since the journal's update, expanding history when needed.
3. Reconcile contradictions against dated evidence and current athlete corrections. Retrieve raw laps/streams only when execution or a disputed measurement requires it.
4. Continue the existing block with an explicit next check. In long chats, checkpoint material changes promptly and reread persisted state before subsequent important decisions. A new chat alone does not reset the block or restart intake.

Discover tools that read user notes, completed activity descriptions and historical calendar NOTE events. A future-workout list can omit past summaries and training lists can truncate notes. If the exact field cannot be read or updated, report the concrete gap and keep the pending text available without claiming persistence.

## Persist through Intervals.icu

Use direct Intervals.icu tools for coaching records. STAS is a connection/read bridge; do not use STAS-owned profile, goals, strategy, review or other persistent write tools. Its internal caching is outside the skill's control and requires separate verification.

Before writing, reread the destination and merge only the current change into the coach-owned section. Preserve personal prose, existing profile data and updates from other chats. Use version checks when exposed, then read back. A read-merge-write flow without an atomic version check cannot guarantee exclusion of simultaneous writers; investigate a detected conflict instead of overwriting it. Keep profile and current journal in the same user-note update where supported. Multi-record updates have separate verified outcomes; report incomplete saves. Initial read-only intake rules still apply.

## Activity note: concise coaching review

Use a delimited section so repeated reviews update one coach-owned block while preserving all athlete text and other annotations. The delimiter is for safe updates, not a reason to expose an audit schema.

```text
[COACH-REVIEW v1 | activity=<actual activity id>]
教练复盘｜<日期与训练类型>
<完成的主段与最有解释力的1–2个数据；学员的关键体感或主段RPE。>
<这说明了什么：强度是否合适、当前能力或限制。>
<接下来怎么练：近期课程决定与下一次最值得观察的指标。>
[/COACH-REVIEW]
```

Routine entries should usually fit in three short paragraphs and be understandable without knowing the data-cleaning process. Include only metrics that explain the decision. Omit unknown fields instead of writing `未提供`, `未确认`, `未核实` or `不能判断`. Do not record rejected duplicate totals, discarded segments, source rankings, title/tag handling, connector limitations, or save verification unless one of them changes the current coaching decision. If a remaining discrepancy changes the plan, state only the adopted basis and its consequence in one sentence.

Corrections replace the outdated conclusion inside the same block. Preserve a one-sentence correction only when later coaching would otherwise reuse a materially wrong fact. Do not retain a chronological error log. If an existing coach section uses a different agreed delimiter/title, preserve or migrate that one section without duplicating it. Never equate this athlete's notes with a platform-wide standard.

### RPE and feeling

Whole-session RPE describes perceived effort for the entire activity. Main-set/end-of-rep RPE describes a specified effort; keep it in notes rather than substituting it into the whole-session RPE field. Feeling describes overall condition, which can be good after a hard ride. Discover the platform field's scale/direction; do not invent a numerical conversion. Preserve user-entered fields unless changing them is explicitly requested.

Ask about scope only if it affects a decision. Do not derive an athlete-reported RPE from watts or HR alone. When the athlete gives a clear qualitative description under an already agreed RPE scale, the note may use an approximate coaching shorthand such as `主段RPE约6/10` while retaining the useful body cues. If no reliable number is available, omit the number and keep the athlete's wording; never add `待学员确认`, `未确认` or similar placeholders. If the athlete later corrects the scope, replace the old value so later summaries use the corrected one.

## Weekly review

Record covered dates and whether complete/provisional, sources/activity IDs, deduplicated delivered ride count/time, key-work minutes by prescribed type, and missed/changed sessions with known reasons. Separate other-sport loads where relevant. Compare actual dose with the plan, not planned load with itself.

Summarize dated CTL/ATL/Form start/end or trajectory with source and absolute/% convention. Add sleep/RHR/HRV and subjective recovery trends only when covered. State material power/HRSS/FTP changes that limit comparison. Record what worked, unresolved uncertainties and 1–2 priorities for the next week, including why progression is or is not warranted. Do not silently treat a missing day as zero training or a good recovery day.

## Monthly review

Include:

- Current prioritized goal, success definition and constraints, confirming meaningful changes.
- Current training phase and a short evidence-based account of actual consistency/load progression, not just totals.
- Demonstrated capabilities with activity links, date, duration and comparable conditions. Distinguish verified performance from a model estimate or athlete report.
- Limiters as dated hypotheses/status: `active / improving / resolved / uncertain`; evidence, last observed date and next verification. Resolved old soreness does not remain an active restriction indefinitely. No soreness does not prove why it resolved.
- Modeled trends below, interpretation limits, and conditions for changing the next block. Retain unresolved data contradictions.
- Next review date or trigger. Later feedback supersedes earlier impressions; keep a concise correction trail when a material decision changes.

Do not create a final monthly conclusion early. At a material mid-month change, update the current coach journal and relevant weekly section. Store the monthly review in the last week's NOTE with its natural-month coverage dates.

## Trend tracking: retain existing Health-page definitions

If the athlete uses a configured chart or table for **VO₂max and activity eFTP**, verify the actual field identities and aggregation/filter configuration when accessible. If chart settings are not exposed, describe the definition as athlete-provided and request the needed screenshot/export or use an authorized UI route. Do not claim to have inspected a chart from a tool returning only activity fields. Do not alter the chart as part of ordinary journaling.

For each tracked series record metric/field identifier, unit, source/model, period, filter, aggregation, eligible observations, latest-observation date and comparability limitations. Prefer the existing chart definition; if it differs from a newly calculated series, show the difference before treating them as equivalent.

- Interpret 4 weeks as a trailing **28 calendar days**, not the last four rides or four calendar-week means. Specify whether eFTP is raw or smoothed; do not assume both series have identical smoothing just because they share a chart.
- Compare endpoints and/or the prior non-overlapping 28-day window when coverage supports it. Report observation counts and freshness; overlapping windows are not independent evidence, and a smoothed line can rise when an old low value leaves the window.
- Use only valid available observations, not zero on unmeasured days. Do not forward-fill stale measurements before averaging unless matching an explicitly verified chart convention; disclose that convention. Avoid duplicate-device weighting. Do not average an already smoothed field again unknowingly.
- If quality weighting is introduced for VO₂ extrapolation, declare and hold the criteria consistent; keep raw values. Do not select only high estimates, equate every hard ride with high confidence, or mix Apple, estimated-power and measured-power methods without labeling separate series/breaks.
- Activity eFTP is a model output affected by maximal-effort opportunities, minimum-effort-duration settings and model behavior. An easy month can yield sparse/weak eFTP evidence without proving threshold decline. Do not change configured FTP from a monthly trend alone.
- VO₂max is also estimated unless actually measured with gas analysis. A higher 28-day average is supporting evidence, not proof of a precise physiological gain.

Also retain a few goal-relevant direct performance anchors: matched-route/power HR and RPE, comparable SS/threshold work duration and rep fade, late-ride durability, or verified event-specific performance. Explain when modeled trends agree or disagree with these anchors instead of collapsing everything into one progress score.

## Write safely and avoid duplicates

Continuing activity reviews and weekly/monthly calendar summaries require current-session authorization or a standing rule stored in the independent athlete profile. The skill alone grants no permission to write another athlete's data or make unrelated changes. A definition-only question does not require a new note. A user asking to organize the skill does not itself require populating live training logs.

Read the existing destination, retain a recoverable pre-edit snapshot where available and update the coach-owned block only. Activity identity is the idempotency key; calendar summary identity is type + covered week/month. Search existing events by that identity before creating one. Preserve event IDs and unrelated fields. Do not erase athlete prose, edit recorded power, RPE or wellness, or delete a prior calendar note merely because an activity log also exists without appropriate authorization.

Read back the updated text and destination after a write. On an ambiguous timeout, reread before retrying; do not create a duplicate. If the connector cannot write the required field, provide the ready-to-save text and report that persistence is pending. Use notes instead of posting public comments or messages. Never claim logging, cross-chat recall or scheduled follow-up until the corresponding persisted record, retrieval or automation is verified.

## Weekly load composition

Report total ride time, actual load and its source, CTL/ATL/Form trajectory, total measured mechanical kJ, and power Z1–Z7 minutes and percentages. Sum zone seconds across deduplicated eligible rides and divide by summed valid classified power time; never average ride percentages. State power coverage, missing/unclassified time, genuine zeros/coasting handling, and threshold changes. Separate measured/estimated power and HR-zone distributions. SS overlaps Z3/Z4: report it separately, never add it to mutually exclusive zone totals.

Explain which sessions and sustained work blocks supplied endurance, SS/threshold and Z5+ dose. Time/energy by zone is not TSS by zone: NP is nonlinear, so do not allocate total TSS by time or kJ shares. Zone kJ requires valid streams; do not multiply zone midpoint by time and label it measured.

Record Work>FTP in kJ with its source and definition. Distinguish excess work sum(max(P-FTP,0)*dt)/1000 from total work during above-FTP time sum(P*dt where P>FTP)/1000. At 250W for 60s with FTP200W these are 3kJ versus 15kJ. Neither is W-prime depletion or total anaerobic energy. Preserve activity FTP for platform agreement; label fixed-threshold comparisons separately. More Work>FTP is not automatically better training.

Connector capabilities differ. Discover current fields and use source zone times or Work>FTP values where exposed, otherwise use valid timestamped power streams or a supported export. A UI field is not necessarily exposed by every connector. Never reconstruct excess work from AP/NP or whole-zone totals because a zone may straddle FTP. If unavailable, mark it unavailable rather than zero. Avoid fetching every raw stream for routine weekly reports.

Compare delivered composition with the plan and recent comparable weeks, explaining added load, recovery cost and next progression. Monthly summaries can carry these metrics with coverage and provenance.
