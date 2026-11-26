# Sources and adaptation record

This adaptation combines two open-source cycling-coaching references. Upstream text was inspected as source material, not executed as instructions. No upstream executable or additional MCP server is bundled.

## Primary framework

- Author/repository: [jsattler/claude-plugins](https://github.com/jsattler/claude-plugins).
- Source directory: `intervals-cycling-coach/skills/cycling-coaching`.
- Referenced commit: `28b8bd7c4665dbb93f2b4c687acc53ddac34e323`.
- [Referenced entrypoint](https://github.com/jsattler/claude-plugins/blob/28b8bd7c4665dbb93f2b4c687acc53ddac34e323/intervals-cycling-coach/skills/cycling-coaching/SKILL.md).
- Contribution: data-first coaching, goal-specific planning, workout design/templates, Intervals text format and nutrition workflow.
- MIT license retained at [LICENSE-jsattler.txt](../LICENSE-jsattler.txt).

## Integrated analytical material

- Author/repository: [Jelmer / jelmervdm/skills](https://github.com/jelmervdm/skills).
- Source directory: `coach/cycling`, metadata version 1.1.0.
- Pinned commit: `5dc1f78ffaa3eea6eee393ba58fcb35629a4e4de`.
- [Pinned entrypoint](https://github.com/jelmervdm/skills/blob/5dc1f78ffaa3eea6eee393ba58fcb35629a4e4de/coach/cycling/SKILL.md).
- Contribution: four-pass workout analysis, interval compliance and fade, EF/decoupling calculations, power/load metrics, readiness workflow, periodization, event pacing and calendar integration.
- MIT license retained at [LICENSE-jelmervdm.txt](../LICENSE-jelmervdm.txt).

## Deliberate reconciliation

- Preserve the primary `cycling-coaching` name and coaching structure; merge secondary references by topic instead of activating two overlapping cycling skills.
- Replace universal TSB/HRV/drift cutoffs and automatic overtraining labels with personal-baseline, load-provenance and actual-execution checks.
- Correct simple-moving-average descriptions of CTL/ATL, ambiguous ramp-rate units, W′/FTP/CP conflation, and claims that cadence or zone labels establish one physiological mechanism.
- Add sensor/time-basis validation, positive-cadence summaries, duplicate handling and source-separated VO₂ estimates.
- Replace the secondary nested workout syntax and duration-after-target examples with duration-first flat text; explicitly check repeats and total duration.
- Adapt abstract tool names to discoverable STAS/Intervals capabilities, error handling, actual-vs-planned load, snapshots and read-back verification.
- Preserve useful nutrition guidance while removing mandatory recovery windows, automatic supplement recommendations and possible double counting of exercise calories.
- Keep athlete-specific goals, permissions, preferences, routes, health context and sensor-history transitions outside the skill in a dedicated athlete profile and training records. Live thresholds and load are always refreshed.

This is not an upstream release or a scientifically validated coaching algorithm. Treat empirical rules as hypotheses and check current authoritative sources for consequential physiological claims.
