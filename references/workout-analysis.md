# Ride and interval execution analysis

Integrated from jelmervdm's four-pass analysis into the primary Intervals workflow.

## Activity organization: names, tags and analysis intervals

As part of substantive post-ride coaching, organize the reviewed Intervals.icu activity before finalizing its review only when the current request or independent athlete profile authorizes those changes. Routine authorization does not extend to bulk historical cleanup, deleting duplicate activities, changing raw FIT/laps/streams, or modifying thresholds, RPE or wellness.

### Read and reconcile first

Retrieve the exact activity ID, existing name/tags/analysis intervals/notes, source-device laps and matched planned session. Discover which fields the current connector can read and write; do not assume every UI feature is exposed. Reuse the primary deduplicated record selected for analysis. Preserve a recoverable before-state and unrelated athlete edits. If an intentional user title or manually curated interval conflicts with the proposed organization, retain it and explain the proposed addition instead of silently replacing it.

### Names and tags

Use a concise name in the athlete's language describing actual main work, retaining an existing useful route name when appropriate: examples `常用路线｜甜区 2×15分钟`, `耐力 90分钟`, `阈值测试｜19分钟`, or `阈值尝试｜15+10分钟，未完成`. Replace generic imported titles or prior coach-generated titles when the actual work is clear. Do not name an interrupted/easier ride as a completed planned workout; do not infer precise threshold/VO₂ improvement from the title. Keep unverified class labels provisional in notes.

Read and reuse the athlete’s existing tag vocabulary and casing before adding tags. Prefer one primary delivered-purpose tag (恢复 / 耐力 / 节奏 / 甜区 / 阈值 / VO₂间歇 / 测试 / 混合 as examples, not a mandatory new taxonomy), with only useful supported secondary tags such as 长骑、未完成、真实功率、估算功率. SS and zone labels describe the actual work, not whole-ride AP or the planned name. Distinguish a dominant purpose from smaller additional work; do not tag every touched zone as a training type. Data-source tags may coexist with a purpose tag. Union new tags with existing user tags; never replace the whole tag list blindly or create synonyms on each review. Correct only demonstrably obsolete coach-owned tags.

### Segment actual execution

Organize analysis intervals into warmup, each actual work rep, between-rep recovery, subsequent endurance/easy return and cooldown when identifiable. Use device laps and athlete timing first, corroborated by timestamped power/cadence/HR and the plan. The plan is an aid, not evidence of completion. For unstructured rides, create only meaningful sustained blocks needed for review or repeated comparisons; do not split every transient surge. Label a traffic interruption separately where useful rather than calling it prescribed recovery.

Resolve whether coordinates are elapsed time, active timer time, wall-clock timestamps or stream sample indices before writing. Map through pause/timer events using valid timestamps; do not equate elapsed minutes with moving minutes, or assume 1-Hz samples. Record both timing conventions when relevant, preserve real zeros/coasting, and exclude missing-data gaps from measured-duration claims. Do not bridge a stop or recording gap and call the result continuous.

Use chronological non-overlapping primary intervals covering the relevant recorded effort; optional comparison windows must be clearly separate and excluded from duplicated workload totals. Name work reps consistently, e.g. `甜区1`, `组间恢复1`, `甜区2`, `轻松返程`. Retain native laps and unrelated/manual intervals. Reuse/update existing equivalent coach intervals, identified by stored ID plus timing/type; never append a second identical set on repeated review. If the platform only supports replacing all analysis intervals, preserve all unrelated intervals and stable identifiers or leave the write pending rather than erase them.

Verify boundaries against timestamps, duration sums, pauses and representative power/HR samples. Read back stored names, tags and interval boundaries after mutation. If data or connector support cannot establish reliable boundaries, provide a proposed segment table and mark 分段待核验/未写入; do not invent exact boundaries, successful writes or measured interval metrics.

### Complete the organization loop

Write only the intended metadata/analysis-interval changes, preserving raw data and notes. On ambiguous errors, retrieve before retrying. Keep verification mechanics out of the activity review; mention organization changes only when they affect later interpretation. Then complete the post-ride decision loop in [longitudinal coaching](longitudinal-coaching.md), using the organized actual work to assess subsequent training.

## 1. Establish what was recorded

Identify the exact activity, date/timezone, sensor provenance, power calibration issues if relevant, distance and timer coverage. Deduplicate simultaneous recordings; use the more complete record for route/duration and align secondary cadence data by timestamps if needed. Do not add duplicate workloads.

Give AP/NP/IF/load/HR/cadence only when available and meaningful. State paused vs active duration and denominator. A whole-ride average dominated by easy return, coasting or stops cannot establish interval intensity. Treat platform work/recovery classification as a hint until checked against timer laps, user timing and streams.

## 2. Match plan to delivered intervals

Retrieve the corresponding calendar prescription and recorded laps/streams. For each work rep report:

| Item | Method |
|---|---|
| Timing | actual start/end, valid active time, interruptions |
| Target | configured power zone, selected %FTP/watt range |
| Delivered power | time-weighted AP, optionally NP/VI, time in range |
| Cardiovascular response | mean/late HR, peak with artifact check; allow response lag |
| Pedaling | positive-cadence median/mean, zero-cadence fraction |
| Perception | user's RPE and limiter when supplied; do not invent it |

For a power range, report time below/in/above range; actual AP divided by target midpoint is only an auxiliary number. Equal AP can conceal surges and coasting. Time-in-zone alone does not prove a sustained rep. Distinguish missed work because of traffic from power fading during uninterrupted pedaling.

For comparable equal-target reps, `fade% = 100*(AP_first−AP_last)/AP_first`. Report the signed result and context, not a universal grading cutoff. If prescription or rep duration changed, use target-normalized performance or state that simple fade is not comparable. Do not diagnose fatigue from fade alone.

## 3. Aerobic decoupling

Choose a sufficiently long, fairly steady endurance segment after warmup, not an interval session or entire stop-start urban ride. Compare equal active-time halves, paired valid HR/power and similar workload/terrain; disclose exclusions. Start with all genuine coasting within the selected continuous effort, and explain any separate pedaling-only sensitivity check.

Define your convention: `EF_i = NP_i / meanHR_i` for a platform-style NP/HR calculation, or time-weighted mean power/HR for near-steady work. `decoupling% = 100*(1−EF_second/EF_first)`. Avoid mixing conventions between rides. NP cannot be reconstructed from whole-ride means. If workload differs strongly or pauses dominate, say the drift value is not interpretable instead of forcing a score.

Small drift can support steady-state durability under comparable conditions; large drift can reflect heat, fueling, hydration, pacing, sensor problems or accumulated fatigue. Neither a 5% nor 7% threshold independently determines aerobic fitness, recovery or tomorrow's prescription. Stop/start routes and mixed intensities may invalidate platform drift metrics.

## 4. Interpret and prescribe

Combine load, actual execution, RPE and recovery. High RPE with low power or low HR is a nonspecific performance mismatch, not proof of parasympathetic overtraining. Easy-feeling high power is not enough by itself to raise FTP. Present plausible explanations and the comparison that would discriminate them.

For longitudinal progress, prioritize same-route, same-direction, matched-speed or matched-power steady segments with environment and stops accounted for. A round trip does not cancel wind's nonlinear energy cost. Separate training adaptation from temperature, position, equipment, traffic and body-mass changes.

End with the delivered stimulus, the main limiter supported by evidence, and one concrete next-session adjustment. Show missingness instead of inventing a complete scorecard.
