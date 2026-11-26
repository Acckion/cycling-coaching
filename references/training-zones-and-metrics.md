# Zones, power and modeled metrics

Adapted from both upstream skills. Formula definitions do not validate the physiological interpretation of an individual estimate.

## Zones and thresholds

Use the athlete's live configured zone boundaries, including the separate HR model and SS range. A common power scheme is Z1 ≤55%, Z2 56–75%, Z3 76–90%, Z4 91–105%, Z5 106–120%, Z6 121–150%, Z7 >150% FTP, but it is a fallback, not a replacement for configuration. Typical workout SS targets such as 88–94% may occupy only part of the configured SS range. Zones describe useful intensity bands, not exclusive energy systems.

FTP is a practical training anchor with individual time-to-exhaustion variability, not universally exactly one-hour power. A standardized 20-minute test ×0.95 is a heuristic affected by protocol, pacing and anaerobic contribution. State the actual duration; a 19-minute effort is not a standardized 20-minute test. Use time-weighted **average power**, including real coasting zeros within the test, rather than NP for this conversion. Paused/rested pieces concatenated into 20 minutes do not establish a continuous test. Distinguish CP from FTP and modeled eFTP/mFTP from a measured benchmark.

## Calculations and time basis

- Mechanical work: `kJ = sum(P_watts * dt_seconds) / 1000`.
- AP: time-weighted mean over the explicitly stated valid timer/segment window, including genuine zeros. Missing sensor values are not zeros.
- NP: fourth root of the time mean of fourth powers of the **30-second rolling-average power**. Prefer the platform's implementation for matching it; state sample/gap/window rules if recomputed. Do not average lap NP or compute whole-ride NP from AP.
- VI = NP/AP (undefined when AP is zero).
- IF = NP/FTP; whole-ride IF is not the work-rep target intensity.
- Power-based TSS ≈ `duration_hours * IF^2 * 100`, only with a consistent duration, NP and FTP basis. Do not relabel HRSS or platform training load as power TSS.
- CTL and ATL are exponentially weighted daily load histories, commonly about 42 and 7 days, not simple rolling means. Use actual configured/model conventions. Form is based on the difference, with platform-specific day alignment and sometimes a percent-of-CTL display. Do not equate absolute −10 with −10%.
- Ramp rate requires a stated window and units (e.g. CTL points/week); do not confuse it with weekly TSS change. Use [load guidance](readiness-and-recovery.md).

Use timer events and timestamps. Report wall time, active timer time, moving time and valid sensor coverage when material. For paired power/HR analysis use aligned valid samples; do not remove coasting simply to improve apparent efficiency. For **pedaling cadence**, report positive-cadence mean/median and zero-cadence share separately from all-time mean. A resting zero cadence is real context, not a bad reading to silently erase.

## Power-duration, W′ and MPA

Describe best efforts over the chosen period, not an athlete type inferred from one fresh sensor ride. Tests that fit CP/W′ need multiple suitable maximal durations and fit diagnostics; sparse unmaximized efforts cannot constrain all parameters reliably.

In the simple CP model, maximal work is `W = CP*t + W′`, and constant-power exhaustion above CP is `t ≈ W′/(P−CP)`. W′ balance is a model with recovery assumptions, not a directly measured fuel tank. Negative W′ balance suggests parameter, data or recovery-model mismatch; it does not prove a unique true W′. Depleted W′ does not mean all mechanical power or MPA becomes zero. MPA is model-specific; use that model's definition and do not substitute it for CP/FTP.

## VO₂max

Power meters improve external-work measurement; they do not measure oxygen uptake. FTP conversion, HR-reserve extrapolation, MAP models and Apple estimates have different assumptions and biases. Report formula, current inputs, uncertainty and source. Do not label an adjusted cycling estimate as native Apple VO₂max or fit a coefficient merely to force agreement then claim validation.

For trend charts retain raw source values, distinguish methods and prioritize comparable steady segments with measured power/valid HR. High intensity may reduce extrapolation distance but short surges and anaerobic work can add bias. Select records by predeclared quality criteria rather than choosing only large values; smooth qualified estimates with a documented window. Smoothing does not remove systematic error. Keep Apple as a separate comparison series unless cross-calibration has independent justification.
