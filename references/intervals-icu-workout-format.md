# Structured workout syntax for the connected tools

Use the live tool schema/platform documentation if it differs. These examples match the currently available Intervals tools and intentionally avoid the secondary upstream's nested, non-parsing example.

- Headers have no dash: `Warmup`, `Main`, `Cooldown`.
- Steps start with `-`, then duration, then target: `- 15m 95-100% 80-95rpm`.
- `m` means minutes, `s` seconds; distance uses `km` or `mtr` where supported. Use unambiguous integer-minute/second durations.
- Cycling targets: `%FTP` expressed as `95%` or `95-100%`, watts as `185w`, or power zone `Z4`. Give a narrower range when the entire zone is too broad.
- HR targets require explicit HR syntax such as `Z2 HR` or `145bpm`. Check tool semantics for threshold-HR percentages rather than assuming `% HR` means LTHR. Never use HR Z4 and power Z4 interchangeably.
- Ramps: `- 10m ramp 45-65%`.
- Cadence: append `80-95rpm`; do not force an exact target unnecessarily.
- Keep prose outside step blocks. Prefer duration-first steps over embedded cue text for compatibility.

Repeat blocks require blank lines before and after, with flat steps beneath a header containing `Nx`:

```text
Warmup
- 15m ramp 45-75%

Main 3x
- 8m 95-100% 80-95rpm
- 4m 45-55%

Cooldown
- 9m ramp 55-40%
```

This example is 60 minutes including recovery after the last rep. If only between-rep recoveries are desired, expand the steps explicitly. Do not describe one total while silently adding a final recovery. Do not indent nested bullet steps, put `Z4` before duration, or assume `[repeat ...]` is parsed.

After writing, verify actual parsed step count, expanded duration, intensity type and repeat count in the returned event/workout structure. A successful HTTP call does not prove successful workout parsing. Inspect expected load as a reasonableness check, not proof of the dose delivered.
