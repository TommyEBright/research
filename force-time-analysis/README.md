# Force-Time Analysis

Browser-based analysis of force platform data for normal, band-assisted and band-resisted countermovement jumps (CMJs).

Developed by Dr Tommy Bright ([ORCID 0000-0001-8089-817X](https://orcid.org/0000-0001-8089-817X), [ResearchGate](https://www.researchgate.net/profile/Thomas-Bright-4)).

## Using it

Open `force-time-analysis.html` in any modern browser. No installation or internet connection is needed, and data are processed locally and never uploaded.

1. Load the raw Kinvent CSV exports (files or a whole folder). Participant and condition are read from the file name and can be edited.
2. Load each participant's normal (body weight) trials, which are used for body mass.
3. Inspect each trial. Movement onset, take-off and landing can be moved to the next detected candidate if the first is a false detection. No events can be placed by hand.
4. Export the results as CSV. Every row records the software version, the full settings used and any skipped events.

## What it measures

Only metrics taken directly from the ground reaction force, which stay valid when an elastic band acts on the athlete:

- Unweighting, above-weight and pre-take-off phases (durations, impulses relative to the reference weight, minimum and peak force, rates of force development)
- Time to take-off, flight time, flight time : time to take-off
- Landing peak force, time to peak and average loading rate

Centre-of-mass velocity, displacement, power and jump height are deliberately not reported, because the band force is not measured by the platform.

All thresholds, windows, the reference weight, the event detection method (fixed or flight-phase noise thresholds) and the optional low-pass filter (with Winter's residual analysis) can be changed in Settings. Settings can be saved and reloaded as JSON.

## Citation

See `CITATION.cff`, or the "How to cite" section in the tool.
